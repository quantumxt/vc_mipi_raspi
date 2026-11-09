# Exposure, blanking and other controls

## Exposure
```shell
v4l2-ctl -c exposure=<value> -d <subdevice>
#Example 10 ms for first camera
v4l2-ctl -c exposure=10000 -d /dev/v4l-subdev2
```
The value's unit is µs. The range depends on the sensor; check it with
```shell
v4l2-ctl --all -d /dev/v4l-subdev2
```
A long exposure time reduces the maximum frame rate, see [Frame rate](frame_rate.md).

> [!NOTE]
> With [libcamera support](libcamera.md) enabled (device tree parameter `camX_libcamera_on`),
> the unit is lines instead of µs, as libcamera expects it. The range is then 1 to 1000000.

## Vertical blanking
```shell
v4l2-ctl -c vertical_blanking=<lines> -d <subdevice>
```
Sets the number of blank lines after the image. The sensor frame length (VMAX) is the image height
plus the vertical blanking, so a larger value reduces the frame rate. Values below the minimum of the
current mode are limited to that minimum. This control is mainly used by libcamera; for manual use
the [frame rate](frame_rate.md) control is easier.

## Horizontal blanking
`horizontal_blanking` is read-only. It reports the horizontal blanking of the current mode in pixels,
which libcamera uses together with `pixel_rate` to calculate line and frame timing.

## Sensor info
```shell
v4l2-ctl -C sensor_info -d <subdevice>
```
Read-only. Shows the sensor type and module revision read from the module ROM, e.g. `IMX568 REV.0004`.

## Flip
The controls `horizontal_flip` and `vertical_flip` exist for libcamera compatibility only.
They are accepted but have no effect: flipping is not supported by the driver.
