---
title: Reflection
---

The camera subsystem successfully met the primary requirement of providing a live video feed to the drone operator. The ESP32-S3 microcontroller was able to interface with the OV2640 camera sensor and stream image data over WiFi using an embedded HTTP server. This allowed the operator to view the camera feed through a browser, fulfilling the requirement for wireless video transmission without the need for additional communication hardware. The subsystem also successfully integrated into the team’s UART daisy-chain network, allowing it to send telemetry data such as frame rate, resolution, and stream status to other subsystems.

In addition, the subsystem met power design requirements by implementing a multi-rail power system (3.3 V, 2.8 V, and 1.5 V) and validating it through a power budget. The PCB design successfully integrated the microcontroller, camera interface, power regulation, and communication interfaces into a single board.

However, some requirements were not fully achieved. The video quality and frame rate were limited due to the lack of PSRAM on the ESP32-S3 module, requiring the use of lower resolution grayscale images instead of full-color streaming. The frame rate achieved was approximately 2 FPS, which is functional but not ideal for real-time navigation. Additionally, the wireless range was limited by the onboard antenna and access point configuration. These limitations highlight areas for improvement in future iterations.

Microcontroller / Module Startup Tips
Always verify camera pin mapping carefully when working with the OV2640. Incorrect pin assignments can cause the camera to initialize but fail to capture frames.
Start with the simplest working example (basic camera test) before adding features like streaming or telemetry.
Use low resolutions (QQVGA or QVGA) during initial testing to avoid memory-related issues.
If image output looks distorted, adjust camera settings such as contrast, brightness, and exposure rather than assuming hardware failure.
Enable debug serial output early to help identify initialization errors or frame capture failures.
Make sure PSRAM is properly configured or accounted for when selecting ESP32 modules, as it significantly affects image processing capability.
Test UART communication separately before integrating it into the full system.
Use short, simple test messages when debugging UART forwarding and parsing logic.
Verify power rails with a multimeter before connecting sensitive components like the camera sensor.
Keep wiring and PCB traces for camera signals short and clean to reduce noise and timing issues.
Lessons Learned

This project provided valuable experience in both hardware and software design for embedded systems. One of the most important lessons learned was the importance of understanding hardware limitations early in the design process. The lack of PSRAM on the selected ESP32-S3 module significantly impacted the achievable frame rate and image quality, demonstrating how component selection directly affects system performance.

Another key lesson was the importance of incremental development. Attempting to build the full system at once led to confusion and debugging challenges. Breaking the project into smaller steps—such as camera initialization, image capture, streaming, and UART communication—made it easier to isolate and fix issues.

I also learned how critical power design is in embedded systems. Providing stable voltage rails for different parts of the system, especially sensitive components like the camera sensor, is essential for reliable operation. The use of both switching regulators and LDOs highlighted the trade-offs between efficiency and noise performance.

Additionally, I gained experience with PCB design, including component placement, routing, and manufacturability considerations. Designing a board that not only works electrically but can also be fabricated and assembled reliably was an important takeaway.

Another important lesson was the value of debugging tools and logging. Serial output was extremely useful in diagnosing issues with camera initialization, frame capture, and communication.

Finally, I learned the importance of system-level thinking. The camera subsystem was not an isolated component—it needed to communicate with other subsystems, meet power constraints, and integrate into the overall drone platform. Balancing these requirements required careful planning and coordination.

Recommendations for Future Students
Start early and break your project into small, testable steps instead of trying to implement everything at once.
Carefully review your component selections, especially microcontrollers, to ensure they meet memory, performance, and interface requirements.
Spend time understanding power requirements and designing proper voltage regulation, as this is critical for system stability.
Use debugging tools such as serial output and test programs frequently to identify issues quickly.
Keep your design simple at first, and only add complexity once the basic system is working reliably.