---
title: Hardware 2.0
---

# Hardware V2.0

If I were to create a Version 2.0 of my camera subsystem hardware, one of the biggest improvements I would explore is replacing the ESP32-S3 and OV2640 camera module with a Raspberry Pi-based system and a higher-quality camera module. The current design successfully provides a live camera feed, but the ESP32-S3-WROOM-1-N4 used in my schematic does not include PSRAM. Because of this limitation, the system had to use lower-resolution grayscale image capture and software JPEG conversion to stream video. While this was sufficient for a working prototype, it limited image quality and frame rate substantially.

<div align="center">
  <img src="/EGR314MannyDataSheet/11-Hardware-V2/rgb.png" width="600" height="450">
  <br>
  <b>Figure 1 - Image Capture With Out of Box Settings</b>
</div>
<br><br>

A Raspberry Pi would provide significantly more processing power, memory, and camera support than the ESP32-S3. This would allow the subsystem to stream higher-resolution video at or above 30 frames per second, which would improve the operator’s ability to identify obstacles, objects, and people around the drone. A higher-quality camera module would also improve image clarity, field of view, and low-light performance, which are important for search and rescue applications.

This change would also improve the wireless video link. In the current design, the ESP32-S3 hosts a WiFi access point and HTTP server directly on the microcontroller. In a future design, a Raspberry Pi could support more advanced networking options, including stronger WiFi adapters, external antennas, or long-range wireless bridges. This would improve communication range and make the video feed more reliable in outdoor environments.

The schematic also shows that the current OV2640 camera requires multiple voltage rails, including 2.8 V and 1.5 V regulators in addition to the 3.3 V rail. A Raspberry Pi camera interface would simplify this part of the design because the camera module is designed to connect directly to the Raspberry Pi camera connector. This could reduce the number of custom camera power rails and lower the risk of camera initialization or power stability issues.

However, this improvement would also introduce trade-offs. A Raspberry Pi would require more power than the current ESP32-S3 design, so the power budget and regulator selection would need to be redesigned. The PCB would also need to include a different connector system, mounting support, and possibly a separate power regulation section for the Raspberry Pi. Despite these trade-offs, the increase in frame rate, image quality, processing capability, and wireless range would make a Raspberry Pi-based design a strong candidate for Hardware Version 2.0.