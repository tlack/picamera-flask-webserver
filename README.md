# picamera-webserver

This is a minimalistic web server that controls a Raspberry Pi's attached PiCamera.

It was extracted from [https://github.com/tlack/dobot-tcn/](my robot training framework)
because I thought it might be useful to others.

It is useful for creating video data sets for repeated experiments. In my usage
a single application instance controls numerous semi-synchronized cameras on
the LAN.

## Features and Status

HTTP API allows you to start and stop video recording. There is an endpoint
that fetches video contents and an endpoint that returns a list of current
videos.

Uses Flask. On Google AIY Bonnet boards, will make alert noise when shooting.

## Usage

Edit camera settings on first line.

Run one copy of this script on each PiCamera node.

## HTTP API

The API presents these endpoints:

### index

`http://0.0.0.0:5858/`

Returns listing of known videos

### start

`http://0.0.0.0:5858/start?fname=test.h264`

Start recording to named video file

### stop

`http://0.0.0.0:5858/start`

Stop recording

### send

`http://0.0.0.0:5858/send?fname=test.h264`

Retrieve contents of video. Returned as Base64 string inside JSON structure:

```{"fn": "test.h264", "data": "...enormous string...", "size": 123123}```

## Todo

Soon: return very exacting timing data for shutter open and shutter close, number of frames, etc.

Support CNN inference on Google AIY boards.

Record / return various sensor readings along with video data.

HTML page to view current camera frame. Or websockets! :D 

## Help

These are tiny scripts. Read the source. Create a Github issue for more help.

