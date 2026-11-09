# Live ROI (Region of Interest)
In case of a cropped image, the ROI can be shifted during streaming.
The cropping (width x height) has to be done first with media-ctl, see [ROI cropping](cropping.md).

``` shell
v4l2-ctl -d <SUBDEV> -c live_roi=<value>
```

The value combines binning mode, left offset and top offset into one number with the format `B_LLLL_TTTT`:

- the last 4 digits (`TTTT`) are the offset from the top in pixels
- the 4 digits before (`LLLL`) are the offset from the left in pixels
- the 9th digit from the right (`B`) is the [binning mode](binning_mode.md) index (not supported on all sensors)

Example:

`001110333` => 111 pixels shifted from left, 333 pixels shifted from top, binning mode 0

``` shell
v4l2-ctl -d <SUBDEV> -c live_roi=001110333
```

> [!NOTE]
> The value is only applied while the camera is streaming. Outside of streaming it is ignored.
> The offsets are limited so that the ROI stays inside the sensor area.

Reading the control returns the current binning mode and position in the same format.

![Roi Position](./images/ROIPosition.svg)
