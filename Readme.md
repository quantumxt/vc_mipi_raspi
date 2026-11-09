# Raspberry Pi Driver for VC MIPI
This driver package is supporting the official Raspberry Pi 3+, 4 and 5 models and CM. 
Downloads are available under 


**[Releases](https://github.com/VC-MIPI-modules/vc_mipi_raspi/releases)**

For mechanical installation see [Mechanical installation manual](https://github.com/VC-MIPI-modules/vc_mipi_core/blob/raspberrypi/develop/doc/mechanical_setup.md)

# Supported Sensors
The following VC MIPI sensor modules are supported by the driver. Mono and color variants use the
same driver; the color variant carries the suffix `C` (e.g. IMX568C).
Module availability as listed in the [VC MIPI module overview](https://www.mipi-modules.com/mipi-kameramodule-technische-daten/).

| Sensor | Mono | Color | Manufacturer | Resolution (W × H) | Megapixel | Sensor family | Shutter | MIPI lanes | Formats | Binning |
|--------|------|-------|--------------|--------------------|-----------|---------------|---------|------------|---------|:-------:|
| IMX178 | IMX178 | –       | Sony | 3072 × 2048 | 6.3  | Starvis   | Rolling / Global Reset | 2, 4 | RAW8, RAW10, RAW12, RAW14 | |
| IMX183 | IMX183 | IMX183C | Sony | 5440 × 3648 | 20.2 | Exmor R   | Rolling / Global Reset | 2, 4 | RAW8, RAW10, RAW12 | |
| IMX226 | IMX226 | IMX226C | Sony | 3904 × 3000 | 12.4 | Starvis   | Rolling / Global Reset | 2, 4 | RAW8, RAW10, RAW12 | |
| IMX250 | IMX250 | IMX250C | Sony | 2432 × 2048 | 5.0  | Pregius   | Global  | 2, 4 | RAW8, RAW10, RAW12 | |
| IMX252 | IMX252 | IMX252C | Sony | 2048 × 1536 | 3.2  | Pregius   | Global  | 2, 4 | RAW8, RAW10, RAW12 | |
| IMX264 | IMX264 | IMX264C | Sony | 2432 × 2048 | 5.1  | Pregius   | Global  | 2    | RAW8, RAW10, RAW12 | |
| IMX265 | IMX265 | IMX265C | Sony | 2048 × 1536 | 3.2  | Pregius   | Global  | 2    | RAW8, RAW10, RAW12 | |
| IMX273 | IMX273 | IMX273C | Sony | 1440 × 1080 | 1.6  | Pregius   | Global  | 2, 4 | RAW8, RAW10, RAW12 | ✓ |
| IMX290 | IMX290 | IMX290C | Sony | 1920 × 1080 | 2.1  | Starvis   | Rolling | 2, 4 | RAW10, RAW12 | |
| IMX296 | IMX296 | IMX296C | Sony | 1440 × 1080 | 1.6  | Pregius   | Global  | 1    | RAW10 | ✓ |
| IMX297 | IMX297 | –       | Sony |  720 × 540  | 0.4  | Pregius   | Global  | 1    | RAW10 | |
| IMX327 | –      | IMX327C | Sony | 1920 × 1080 | 2.1  | Starvis   | Rolling | 2, 4 | RAW10, RAW12 | |
| IMX335 | IMX335 | IMX335C | Sony | 2592 × 1944 | 5.0  | Starvis   | Rolling | 2, 4 | RAW10, RAW12 | |
| IMX392 | IMX392 | IMX392C | Sony | 1920 × 1200 | 2.3  | Pregius   | Global  | 2, 4 | RAW8, RAW10, RAW12 | |
| IMX412 | –      | IMX412C | Sony | 4032 × 3040 | 12.3 | Starvis   | Rolling | 2, 4 | RAW10 | ✓ |
| IMX415 | IMX415 | IMX415C | Sony | 3840 × 2160 | 8.3  | Starvis   | Rolling | 2, 4 | RAW10 | |
| IMX462 | IMX462 | IMX462C | Sony | 1920 × 1080 | 2.1  | Starvis   | Rolling | 2, 4 | RAW10, RAW12 (2 lanes only) | |
| IMX565 | IMX565 | IMX565C | Sony | 4128 × 3000 | 12.4 | Pregius S | Global  | 2, 4 | RAW8, RAW10, RAW12 | ✓ |
| IMX566 | –      | IMX566C | Sony | 2848 × 2848 | 8.1  | Pregius S | Global  | 2, 4 | RAW8, RAW10, RAW12 | ✓ |
| IMX567 | IMX567 | –       | Sony | 2464 × 2064 | 5.1  | Pregius S | Global  | 2, 4 | RAW8, RAW10, RAW12 | ✓ |
| IMX568 | IMX568 | IMX568C | Sony | 2464 × 2064 | 5.1  | Pregius S | Global  | 2, 4 | RAW8, RAW10, RAW12 | ✓ |
| IMX585 | IMX585 | IMX585C | Sony | 3840 × 2160 | 8.3  | Starvis 2 | Rolling | 2, 4 | RAW10, RAW12 | |
| IMX900 | IMX900 | IMX900C | Sony | 2048 × 1536 | 3.2  | Pregius S | Global  | 2, 4 | RAW8, RAW10, RAW12 | |
| OV7251 | OV7251 | –       | OmniVision | 640 × 480  | 0.3 | OmniPixel3-GS | Global | 1 | RAW8, RAW10 | |
| OV9281 | OV9281 | –       | OmniVision | 1280 × 800 | 1.0 | OmniPixel3-GS | Global | 2 | RAW8, RAW10 | |
| AR2020 | –      | AR2020C | onsemi | 5120 × 3840 | 20.0 | Hyperlux™ LP | Rolling | 2, 4 | RAW8, RAW10, RAW12 | |

The resolution is the maximum image size delivered by the driver; it can differ slightly from the
sensor's total pixel count in the module overview.
The number of lanes must match the module and is set during installation (see [Configure the lanes](#configure-the-lanes)).
For details on binning see [Binning mode](./docs/binning_mode.md).

# Installation
The driver is tested on 64-bit Raspberry Pi OS with Bookworm (Lite or with desktop).
The OS can be installed by the official Raspberry Pi Imager from the Raspberry Pi Foundation.

[Raspberry Pi OS](https://www.raspberrypi.com/software/)

Copy the debian package for your target system to the module:
* Raspi5, CM5    ⇒  BCM2712 
* Raspi4, CM4    ⇒  BCM2711
* Raspi3+        ⇒  BCM2837
* Raspi Zero 2   ⇒  RP3A0   
* VCCMI10 ⇒ [VC MIPI Compute Module Interface Board](https://www.mipi-modules.com/fileadmin/external/documentation/hardware/VC_MIPI_Compute_Module_Interface/index.html)


Run the installation with the installation of the needed packages: 
```
sudo apt install ./vc-mipi-driver-bcm2712_xxx_arm64.deb
```

Run the installation with manual packages:


> [!TIP]
> If you install the package with dpkg, you have to install the dependecies manually
> ```
> sudo apt install dkms linux-headers-generic v4l-utils whiptail
> sudo dpkg -i ./vc-mipi-driver-bcm2712_xxx_arm64.deb
> ```

## Configure the lanes
Before rebooting, the number of MIPI lanes (and the sensor manufacturer) has to be set for each camera.
If the lanes do not fit the sensor, no camera is detected.

The settings are in the boot file installed by the package (here for BCM2712):
```
sudo nano /boot/firmware/config_vc-mipi-driver-bcm2712.txt
```
```
dtoverlay=vc-mipi-bcm2712-cam0
dtparam=cam0_lanes4         # cam0_lanes1, cam0_lanes2 or cam0_lanes4
dtparam=cam0_manu_sony      # cam0_manu_sony, cam0_manu_ov (Omnivision) or cam0_manu_os (Onsemi)
```
Do the same with the `cam1_...` entries for the second camera.

| Lanes | Sensors |
| ----- | ------- |
| 1     | OV7251, IMX296, IMX297 |
| 2     | OV9281, IMX264, IMX265 |
| 2, 4  | IMX178, IMX183, IMX226, IMX250, IMX252, IMX273, IMX290, IMX327, IMX335, IMX392, IMX412, IMX415, IMX462, IMX565, IMX566, IMX567, IMX568, IMX900 |

If the sensor supports 2 and 4 lanes, choose 4 lanes, but only if the camera connector provides them
(e.g. Raspberry Pi 5, CM5; on CM4 only `cam0`, which is the 4-lane connector CAM1 of the IO board). The camera connectors of Raspberry Pi 3+, 4 and Zero 2 have 2 lanes.

> [!NOTE]
> The defaults differ per platform: BCM2712 is preset to 4 lanes and Onsemi, all others to 2 lanes and Sony.

Alternatively, the lanes can be set with `vc-config` → "Configure Device Tree" (see [Configuration](#configuration)).
A reboot is needed after every change.

After a reboot the connected sensor(s) should be detected and visible as v4l2 capture devices
Under the current Raspberry Pi OS with Bookworm, 
the sensors are:

Raspi5
| Camera   | Device      | Subdevice        |
| -------- | ----------- | ---------------- |
| Cam0     | /dev/video0 | /dev/v4l-subdev2 |
| Cam1     | /dev/video8 | /dev/v4l-subdev5 |

> [!TIP]
> **Raspi5 / Bookworm:** The `v4l-utils` version shipped with Raspberry Pi OS Bookworm (1.22.1) does **not** support unpacking raw Bayer pixel formats (e.g. `RG10`, `RG12`) from the capture device.  
> Upgrade to **v4l-utils 1.30.1** from the Trixie repository before capturing raw data:
> ```bash
> echo "deb [arch=armhf] http://raspbian.raspberrypi.com/raspbian/ trixie main contrib non-free rpi" \
>   | sudo tee /etc/apt/sources.list.d/raspbian-trixie.list
> sudo tee /etc/apt/preferences.d/trixie-pin <<'EOF'
> Package: *
> Pin: release n=trixie
> Pin-Priority: 100
> EOF
> sudo apt-get update
> sudo apt-get install -t trixie v4l-utils
> ```
> See [docs/install_v4l2_utils.md](./docs/install_v4l2_utils.md) for full details.

Raspi3-4
| Camera   | Device      | Subdevice        |
| -------- | ----------- | ---------------- |
| Cam0     | /dev/video0 | /dev/v4l-subdev0 |
| Cam1     | /dev/video1 | /dev/v4l-subdev2 |

## Self check
To verify the installation and configuration, run the [self check](./tools/self_check.sh):
```
./tools/self_check.sh
```
It checks the package, driver modules, boot configuration, the active device tree, the devices on the
camera I2C bus, the module ROM (sensor type, supported lanes, sensor manufacturer), the driver probe,
libcamera and a short streaming test,
and gives a hint for each problem found. Use `--no-stream` to skip the streaming test.

# Build from source

See [Build from Source](./docs/build_from_source.md)

# Configuration

1. The configuration for the VC MIPI Sensors is in the boot file 
<i>/boot/firmware/config_vc-mipi-driver-bcm2712.txt</i>. 
The right lanes configuration for the sensors has to be made. For some sensors, 2 modes are available. 
If no specific configuration is needed, the "more lanes" configuration is the first choice (i.e. 4 instead 2 lanes)
2. Additionally the configuration tool vc-config is installed. By calling ```vc-config```
it is possible to change the values of the controls and also the region of interest (ROI)
3. The formats can be adjusted. All formats are displayed, although not all are available which depends on the sensor model.

![Cam Controls](./docs/images/whiptail_controls.png "Cam Controls")
![Cam Selection](./docs/images/whiptail_cam_selection.png "Cam Selection")
![Lanes configuration](./docs/images/whiptail_lanes_config.png "Lanes configuration")
![Format Selection](./docs/images/whiptail_format_settings.png "Format settings")

# ISP and Libcamera Support (Raspberry Pi 4 and 5 Series only)
For Libcamera support, refer to [Libcamera Installation](./docs/libcamera.md)
Then the ISP with features like Auto White Balancing (AWB) are supported.

# Support Tool
## Installation
The official support tool for the v4l2 driver is 
[V4L2-Test](https://github.com/pmliquify/v4l2-test/tree/feature/gstreamer)

```shell
sudo apt-get install git
git clone https://github.com/pmliquify/v4l2-test.git
cd v4l2-test.git
make all
```

⚠️ **Important:** Checkout branch feature/gstreamer for full raspberrypi compliance
Please refer to the installation there. 
```shell
## Usage
For starting, you have to add the subdevice properly in order to set the controls by tool:
```shell
./v4l2-test stream -e <exposure> -g <gain> -f <pixelformat> -p 1 -d <device> -sd <subdevice>
# Camera 0
./v4l2-test stream -e <exposure> -g <gain> -f <pixelformat> -p 1 -d /dev/video0 -sd /dev/v4l-subdev2
# Camera 1
./v4l2-test stream -e <exposure> -g <gain> -f <pixelformat> -p 1 -d /dev/video8 -sd /dev/v4l-subdev5
```
## Display live image

For getting the live image on the screen, add the argument `--fb`

```shell
./v4l2-test stream -e <exposure> -g <gain> -f <pixelformat>  -d <device> -sd <subdevice> --fb
# Camera 0
./v4l2-test stream -e <exposure> -g <gain> -f <pixelformat>  -d /dev/video0 -sd /dev/v4l-subdev2 --fb
# Camera 1
./v4l2-test stream -e <exposure> -g <gain> -f <pixelformat>  -d /dev/video8 -sd /dev/v4l-subdev5 --fb
```

On desktop version, first you have to switch to console mode `Ctrl + Alt + F1`

![Console mode](./docs/images/RaspiDesktopFramebuffer.gif)

# Controls
1. [Black level](./docs/black_level.md)
2. [IO Mode](./docs/io_mode.md)
3. [Trigger mode](./docs/trigger_mode.md)
4. [Binning mode](./docs/binning_mode.md)
5. [Frame rate](./docs/frame_rate.md)
6. [Gain](./docs/gain.md)
7. [Exposure, blanking, sensor info and flip](./docs/exposure.md)
8. [Live ROI](./docs/live_roi.md)
9. [ROI cropping](./docs/cropping.md)
10. [Pixel format](./docs/pixelformat.md)

# Known issues

The driver offers the basic features of the VC MIPI sensors. 
This has the advantage that the same functions are available with all sensors. 
If special functions are required, please contact the support team or your contact at Vision Components GmbH 

1. The flipping controls are not supported by standard driver

<b>[FAQ](./docs/faq.md)
