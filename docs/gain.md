# Gain
```shell
v4l2-ctl -c analogue_gain=<value> -d <subdevice>
#Example 10.000 dB  for first camera
v4l2-ctl -c analogue_gain=10000 -d /dev/v4l-subdev2
```
The range is from 0 to the sensor's maximum value.
Check the maximum value with v4l2-ctl.
```shell
v4l2-ctl --all -d /dev/v4l-subdev2
```
The value's unit is mdB (1/1000 dB).

The gain is given in amplitude dB, the same convention libcamera uses:
gain factor = 10^(mdB / 20000). E.g. `analogue_gain=6020` doubles the signal, `analogue_gain=20000` amplifies it 10 times.

> [!NOTE]
> Older driver versions used 10 · log10 (power dB). With the same value the gain is now lower:
> a value that used to give 2x gain now gives about 1.41x. Double the old values to get the same gain.

The range covers the analog gain of the sensor and, if available, its digital gain on top.

