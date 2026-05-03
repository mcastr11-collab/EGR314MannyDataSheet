---
title: Application Programming Interface
tags:
- tag1
- tag2
---

## Overview
The camera subsystem uses the class UART daisy-chain protocol to transmit information, such as livestream status, frame rate, and resolution. Actual image and video data are not sent over UART; they are transmitted separately through the ESP32-S3’s WiFi access point and embedded HTTP server. Camera telemetry and stream status are sent as independent UART packets to Lia’s HMI subsystem and Matthew’s communication subsystem. The ESP32-S3 handles both the camera web interface and UART packet communication with the subsystem daisy chain.

Due to bandwidth limitations of UART communication, high-volume image data is not transmitted through the UART network. Instead, the camera subsystem streams image data over WiFi using an embedded HTTP server. UART communication is reserved for low-bandwidth control and status messages.

Each UART message follows a standardized format consisting of a start sequence ("AZ"), a source identifier, a destination identifier, a variable-length payload, and an end sequence ("YB"). The use of start and end delimiters allows the receiving subsystem to reliably detect complete messages within a continuous serial data stream. 

Each UART packet is analized via internal message validation  on my subsystem to ensure that malformed or incomplete packets are discarded, improving system robustnes.

## Messages Sent

The camera subsystem periodically transmits telemetry data to other subsystems, including Lia's Human-Machine Interface (HMI) and Matthew's communication module. These telemetry messages include frame rate, resolution, and livestream status, allowing other subsystems to react to changes in camera availability in real time. More details on the message structure can be found on the tables below.


| **Byte** | **Variable Name** | **Type** | **Example** |  **Description** | **Message Range**
|---:|---|---|---|----|:---:|
| Byte 1-2 | start      | char | AZ | Start of the message | AZ-AZ |
| Byte 3 | source_id    | char | C | Who is it from? | C,L,M,K,V.X|
| Byte 4 | dest_id | char | L | Who is it for? | C,L,M,K,V.X|
| Byte 5-26 | fps | string | F: 2.0 | Current camera framerate | 0-99|
| Byte 5-26 | resolution | string | R:320x240 | Camera resolution | 320x240|
| Byte 5-26 | stream status | string | S:ON | Camera resolution | S: ON or S:OFF|
| Byte end | end | char | YB | End of message| YB-YB|


## Message Handling and Forwarding

The camera subsystem receives UART messages as part of the distributed subsystem network. Rather than acting as a command-driven device, the subsystem functions as an autonomous node that processes, filters, and forwards messages based on their destination.

Upon receiving a message, the subsystem parses the packet structure to determine the source and destination identifiers. Messages addressed to the local subsystem are processed and logged, while messages addressed to other subsystems are forwarded along the UART daisy-chain. Broadcast messages (destination "X") are both processed and forwarded to ensure network-wide propagation.

The forwarding mechanism allows each subsystem to act as a relay within the communication network. This enables communication between subsystems that are not directly connected, effectively extending the communication range and maintaining a consistent flow of information throughout the system.

## Valid Message Examples

<table>
<tr><th>Message</th><th>Description</th></tr>
<tr><td>AZMLHELLOYB</td><td>Not for me (forward)</td></tr>
<tr><td>AZMXTESTYB</td><td>Broadcast (process + forward)</td></tr>
<tr><td>AZMCHELLOYB</td><td>For me (process only)</td></tr>
<tr><td>AZCL F:1.5 R:320x240 S:ON YB</td><td>Outgoing message to Lia</td></tr>
<tr><td>AZCM S:ON YB</td><td>Outgoing message to Matthew</td></tr>
</table>


