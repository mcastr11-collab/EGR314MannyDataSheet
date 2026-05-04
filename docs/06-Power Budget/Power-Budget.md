---
title: Power Budget
---

## Module's Selected Major Components

The following sections detail the selected major components of my camera sensor subsystem. These work in unison in order to fullfill the project requirements for this subsystem.


### Power Budget (Pending further research)

The camera subsystem uses a shared 12 V supply from the team’s 8-pin connector as the primary power input. This voltage is stepped down to 3.3 V using the LM2575D2T-3.3R4G switching regulator, which powers the ESP32-S3 and LED indicators. The 3.3 V rail also feeds the 2.8 V and 1.5 V LDO regulators required by the OV2640 camera sensor.

The 3.3 V rail is the highest-current rail because it supplies the ESP32-S3 during WiFi operation. The 2.8 V and 1.5 V rails require much less current because they only power the OV2640 camera domains. After applying the required safety margin, each regulator remains within its rated current limit, confirming that the selected regulators can safely support the subsystem.

A switching regulator was used for the main 3.3 V rail to improve efficiency when stepping down from the shared 12 V source. Low-noise linear regulators were used for the 2.8 V and 1.5 V camera rails because the camera sensor requires stable, clean power for reliable image capture. This separation allows the subsystem to meet both efficiency and signal-quality requirements.

The camera subsystem may use external power to power up individually using 9 V AC-DC wall supply rated for 3 A. The PCB has a standard barrel jack that can accomodate many of the common supply AC to DC adapters. This input power is stepped down to 3.3 V using the LM2575D2T-3.3R4G switching regulator. All rails are within the recommended 25% safety margin. This confirms that the selected power source and regulators are sufficient for the camera subsystem

<object data="https://mcastr11-collab.github.io/EGR314MannyDataSheet/05-Power Budget/SableCamSystemPowerBudget.xlsx" type="application/pdf" width="700px" height="700px">
    <embed src="https://egr304-203.github.io/sparkguard/Team203BlockDiagramFinal.pdf">
        <p>This browser does not support PDFs. Please download the PDF to view it: <a href="https://egr304-203.github.io/sparkguard/Team203BlockDiagramFinal.pdf">Download PDF</a>.</p>
    </embed>
</object><br><br>

**Resources** <br>


A link to download the power budget may be found [here] (./SableCamSystemPowerBudget.xlsx)

>If you need the zipped source files for the component selection or any other files for this project, please see the [Resources](https://mcastr11-collab/EGR314MannyDataSheet/Appendix/Resources) section.
