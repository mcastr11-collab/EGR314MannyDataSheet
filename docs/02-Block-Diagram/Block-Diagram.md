---
title: Module's Block Diagram
tags:
- tag1
- tag2
---

## Overview
The purpose of this block diagram is to illustrate the overall architecture and integration of the camera subsystem within the larger drone system. It highlights the key components and their interactions, including the OV2640 camera sensor, the ESP32-S3 microcontroller, and the WiFi-based HTTP server used to deliver the live video feed to the operator. The diagram also shows the distribution of power across multiple voltage levels, including the 9 V DC input source, the regulated 3.3 V DC rail for the microcontroller, and the 2.8 V DC and 1.5 V DC rails required by the camera sensor.<br>

In addition, the block diagram identifies troubleshooting elements such as LED indicators used for system status and debugging. The UART TX and RX connections illustrate how the subsystem communicates with other team subsystems through a bidirectional daisy-chain network, enabling telemetry sharing and message forwarding. Overall, the diagram provides a clear representation of how power, sensing, communication, and user interaction are integrated to meet the functional requirements of the camera subsystem.

The block diagram is embeded below as a PDF and it can be downloaded using the link at the bottom of the page.


## Camera & Distance Sensor Block Diagram 

<object data="https://mcastr11-collab.github.io/EGR314MannyDataSheet/02-Block-Diagram/Camera Subsystem Block Diagram.drawio.pdf" type="application/pdf" width="700px" height="700px">
    <embed src="https://egr304-203.github.io/sparkguard/Team203BlockDiagramFinal.pdf">
        <p>This browser does not support PDFs. Please download the PDF to view it: <a href="https://egr304-203.github.io/sparkguard/Team203BlockDiagramFinal.pdf">Download PDF</a>.</p>
    </embed>
</object><br><br>

Download of the Block Diagram PDF file [here](./Camera Subsystem Block Diagram.drawio.pdf)<br>

>If you need the zipped source files for the Block Diagram or any other files for this project, please see the [Resources](https://mcastr11-collab/EGR314MannyDataSheet/docs/Appendix/Resources.md) section.