# r.in.kinect
GRASS tool for importing data from a depth camera into a GRASS raster or vector map.

This branch (`xbox-one-updated`) supports the Kinect for Xbox One (Microsoft Kinect v2). It was created by using Claude to compare the original xbox-one branch compared to the femto-bolt branch and update it. Code changes were inserted individually by hand after review and explanation.

Other branches support the Microsoft Azure Kinect DK (`k4a`) and the [Orbbec Femto Bolt](https://www.orbbec.com/products/tof-camera/femto-bolt/) (`femto-bolt`).

See the [r.in.kinect manual page](r.in.kinect.md) for usage, options, and the calibration workflow.
It is the scanning backend of the [Tangible Landscape](https://tangible-landscape.github.io/) project.

## Dependencies
 * [libfreenect2](https://github.com/OpenKinect/libfreenect2)
 * [PCL 1.13 and higher](http://pointclouds.org)
 * OpenCV
 * [GRASS 8.5 and higher](https://grass.osgeo.org) (cmake-based build)

## Installation
Supported platforms include Ubuntu Linux. Running r.in.kinect on any other platforms is possible but not tested.

Install the dependencies following their official installation guides. First test libfreenect2's Protonect binary before you proceed with other steps. Then build and install r.in.kinect with `g.extension`:

    git clone --single-branch --branch xbox-one-updated https://github.com/rgugs/r.in.kinect.git
    sudo grass --tmp-project XY --exec \
        g.extension -s extension=r.in.kinect url=$(pwd)/r.in.kinect

If cmake cannot find libfreenect2, set `freenect2_DIR` to the directory containing `freenect2Config.cmake` (e.g. `/usr/local/lib/cmake/freenect2`). PCL and GRASS
libraries are located automatically through their cmake config files. The `-s`
flag installs system-wide (under `$GISBASE`); drop it to install for the current
user only (and remove `sudo`).

To use r.in.kinect interactively for tangible modeling, also install the
[GRASS Tangible Landscape plugin](https://github.com/tangible-landscape/grass-tangible-landscape).
