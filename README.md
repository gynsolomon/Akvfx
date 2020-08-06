Akvfx
=====

![gif](https://i.imgur.com/h0kApp4.gif)
![gif](https://i.imgur.com/lXRiwU3.gif)

**Akvfx** is a Unity plugin that captures color/depth data from an [Azure
Kinect] device and converts them into attribute maps (textures) handy for using
with [Visual Effect Graph].

[Azure Kinect]: https://azure.com/kinect
[Visual Effect Graph]: https://unity.com/visual-effect-graph

System Requirements
-------------------

- Unity 2019.3
- Azure Kinect DK

See also the [System Requirements] page of Azure Kinect DK. Note that Akvfx
doesn't support Linux at the moment.

[System Requirements]:
    https://docs.microsoft.com/en-us/azure/kinect-dk/system-requirements

	
[Fork specific notes]

This fork is an experiment in live streaming the VFX to an RMTP end point.
- Output to a virtual webcam using Unity Capture (https://github.com/schellingb/UnityCapture)
- Output rgb channel and depth channel (as HSV) for reconstruction in threejs on the "other end"

FFMPEG:
- View Output
 ./ffplay -f dshow -video_size 1280x720 -vf "format=yuv420p" -i video="Unity Video Capture"
 
- Stream output to rtmp
 ./ffmpeg -f dshow -video_size 1280x720 -i video="Unity Video Capture" -c:v libx264 -preset veryfast -b:v 1984k -maxrate 1984k -bufsize 3968k -vf "format=yuv420p" -g 60 -f flv rtmp://localhost:1935/live/test
 
