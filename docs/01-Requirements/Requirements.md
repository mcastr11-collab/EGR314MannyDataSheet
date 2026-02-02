---
title: Camera Stability and Sensor Suite Module Requirements
---

## Sybsystem Requirements
These subsystem requirements are the expectations I will follow as the design and assembly of the subsystem module progresses. To create these requirements, our team looked at the features from the selected design concept and course project requirements; extracted them into tangible goals we can meet with our product in the amount of time and budget given to our team.

Requirements are split between the Measure of Threshold(MoT), being the minimum level required to not be deemed a failure, and Target Measure, being the goal we want our requirements to reach. Notably, there are many stretch requirements. These requirements are not something we need to include in our device to achieve our base goal. Including these stretch requirements will give our completed device an edge in the marketplace, if we are able to reach them.

| # | **Requirement Description** | **Measure of Threshold (MoT)** | **Target Measure** | **Stretch Requirement (Y/N)** |
|---:|---|---|---|:---:|
| 2 | Surface mounted, 3.3V switching power regulator | 3.2V | 3.3V | N |
| 5 | Stable while moving | MoT of #1 without flipping over | MoT of #2 without flipping over | N |
| 6 | Stable video while moving | Must be able to hold the camera steady while driving at 5 MPH | Must be able to hold the camera steady while driving at 10 MPH | Y |
| 7 | Display live video | Sends out 30 FPS per second | Live video with less than 3 seconds of delay | Y |
| 9 | Human Design Interface; Respond manually with buttons | Small OLED screen with pushbuttons that permits a user to view all sensor data in text; directly control the actuator; modify setpoints on all the system boards; toggle GPIO debug pins on ALL subsystems. | All the content in MoT and ability to tune sensors and actuators with controls on exterior of device. | N |
| 10 | Use thermal sensors to people with drone | Drone is able to see human heat signatures | Able to see a human body or track residual human body heat 5 meters away | Y |
| 14 | Detect objects with distance sensors | Detects objects within 1 meter of the drone | Detects objects within 3 meters of the drone | N |
| 15 | I2C or SPI | Control peripheral devices such as sensors, microphones, and camera | Same as MoT | N |
| 16 | Daisy chain UART | Daisy chain UART connection between all subsystems | Separate UART loops for high speed communication through certain subsystems | N |
| 17 | Distance controlled wheel speed | The robot can control wheel speed and can display its speed within +-10 cm/s error, and can drive backwards. | MoT and robot uses sensors to determine speed, maneuver around obstacles by turning, and knows speed within +- 1 cm/s error. | Y |

<br>

## Overview of Requirements

This subsystem will be the the camera sensor module for our search and rescue bot that will need to be capable of operating in natural disaster zones and urban rescue situations. As a stretch goal, we also intend the device to be capable as a land rover in low atmosphere planets, such as Mars. As a search and rescue robot, it needs to be able to locate survivors by sight, sound, and ground vibrations. 

Since our robot must traverse decently rough and granulated terrain in order to be a viable rescue bot, thus requirements 5 abd 6 detail how the needs to drive and be remain stable on this type of terrain. This means the camera system will need to work with both requirements in order to achieve a stable video feed platform to help the operator navigate terrain with ease.

Requirements 2, 9, 15 and 16 are based on the project requirements for this course, due to a certain voltage regulator requirement and communication requirements. These powere the bot and establish the serial communication protocol between sensors and modules.

For more remote control capability and robot vision, the robot should have a camera that has to stabilize its feed in order to be useful in its intended environment, thus we came up with requirements 6 and 7.

Requirement 10 and 14 allows the robot to find survivors who are lost. With 10 being a stretch goal that will incorporate a thermal imaging sensor and 11 being a distance sensor to help regulate speed as it approaches objects abd obstacles.

For the robot to reliably navigate its environment and avoid obstacles, the device must be able to control its speed accurately and turn. Thus requirement 17 addresses this.
