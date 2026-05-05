---
title: Module Schematic
---

## Overview

This schematic is designed to support the OV2640 camera sensor, a 3.3V, 1.5V, and a 2.8V DC power rails, micro USB bus for ease of programming, and several female headers for signal troubleshooting and future expansion.

The 3.3VDC rail brings power to the ESP32-S3, the onboard LEDs, and it distributes power to the two downstream DC power rails of 1.5VDC and 2.8VDC. 

In addition to the 3.3VDC, the camera sensor specifies that AVDD & DOVDD need to be at a range of 2.8VDC and DVDD needs 1.5VDC, which is where both of these specific power rails come in to provide the required power needed by the camera sensor. 

The schematic below shows all details needed to reproduce this subsystem with the specified components.


<object data="https://mcastr11-collab.github.io/EGR314MannyDataSheet/08-Schematic/SableCamSensorv1.9schematic.pdf" type="application/pdf" width="700px" height="700px">
    <embed src="https://egr304-203.github.io/sparkguard/Team203BlockDiagramFinal.pdf">
        <p>This browser does not support PDFs. Please download the PDF to view it: <a href="https://egr304-203.github.io/sparkguard/Team203BlockDiagramFinal.pdf">Download PDF</a>.</p>
    </embed>
</object><br><br>


## Resouces

The schematic as a PDF download is available [*here*](SableCamSensorv1.9schematic.pdf).

>If you need the zipped source files for the schematic or any other files for this project, please see the [Resources](https://mcastr11-collab.github.io/EGR314MannyDataSheet/Appendix/) section.