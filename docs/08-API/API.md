---
title: Application Programming Interface
tags:
- tag1
- tag2
---

## Overview
The camera subsystem uses the class UART daisy-chain protocol to broadcast low-bandwidth status information such as whether the livestream is online. Actual image or video data is sent separately through the wireless website/server link on the main microcontroller. The auxiliary ESP 32 handled communication with the subsystem daisy chain via the UART packet network.

## Messages Sent


| **Byte** | **Variable Name** | **Type** | **Min Value** |  **Min Value** |
|---:|---|---|---|:---:|
| Byte 1 | message_type | char | C | C |
| Byte 2 | stream_state | char | 0 | 1 | 

>"C" is the camera message and "0" and "1" indicate offline and online status of the stream respectively. Combined in the string, it should send a message of "C0" for camera stream offline or "C1" for camera stream online.

## Message Received

This is used to tell the camera subsystem to start or pause the livestream to the website.

| **Byte** | **Variable Name** | **Type** | **Min Value** |  **Min Value** |
|---:|---|---|---|:---:|
| Byte 1 | message_type | char | R | R |
| Byte 2 | stream_command | char | 0 | 1 | 

>"R" is the "reveived" camera message looping back to the subsytem."0" is a message command to pause the stream and "1" to initiate the stream.

The messages are to be transmitted as individual characters over UART, where each character represents one byte in the message structure. This subsystem will periodically transmit the camera stream status to all other subsytems, such as the communication module, such as they are all able to react to the availability of the stream in real time.

## Valid Message Examples

Received Message (turn on stream):  AZMCR1......YB <br>
Received Message (turn off stream): AZMCR0......YB <br>
Sent Message (stream is online):  AZMSC1......YB <br>
Sent Message (stream is offline):  AZMSC0......YB 

