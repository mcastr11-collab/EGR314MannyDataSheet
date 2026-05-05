---
title: Power Budget
---

## Power Budget Process Summary

I used the power budget to estimate the subsystem’s worst-case current requirements by identifying each major powered component, assigning it to the appropriate voltage rail, and using the maximum or estimated current draw for each device. The total current for each rail was calculated and compared against the rated output current of the selected regulators, including the required 25% safety margin.

The results showed that the 3.3 V rail has the highest current demand because it powers the ESP32-S3 during WiFi operation, while the 2.8 V and 1.5 V rails have lower current requirements since they only supply the OV2640 camera sensor. After applying the safety margin, all regulators operate within their rated current limits.

Based on this analysis, I concluded that the selected power source and regulators are sufficient for the camera subsystem. The use of a switching regulator for the 3.3 V rail improves efficiency, while the 2.8 V and 1.5 V LDO regulators provide clean, stable power for the camera sensor.

### Power Budget Details

The camera subsystem uses a shared 12 V supply from the team’s 8-pin connector as the primary power input. This voltage is stepped down to 3.3 V using the LM2575D2T-3.3R4G switching regulator, which powers the ESP32-S3 and LED indicators. The 3.3 V rail also feeds the 2.8 V and 1.5 V LDO regulators required by the OV2640 camera sensor.

The 3.3 V rail carries the highest current load due to the ESP32-S3 operating with WiFi enabled. In contrast, the 2.8 V and 1.5 V rails supply only the camera’s analog, I/O, and digital core domains, resulting in significantly lower current requirements. After applying the required 25% safety margin, each regulator remains within its rated capacity, confirming that the design is electrically safe and reliable.

A switching regulator was selected for the 3.3 V rail to efficiently step down from the 12 V input, reducing power loss and heat generation. Low-noise linear regulators were selected for the 2.8 V and 1.5 V rails to ensure stable and clean power for the camera sensor, which is sensitive to electrical noise. This combination balances efficiency and signal integrity within the system.

The subsystem can also be powered independently using a 9 V AC-DC wall supply rated at 3 A through an onboard barrel jack. In this configuration, the 9 V input is similarly regulated down to 3.3 V using the LM2575 switching regulator. In both power configurations, all rails remain within the required safety margin, confirming that the selected power sources and regulators are sufficient for the camera subsystem.<br>

<object data="https://mcastr11-collab.github.io/EGR314MannyDataSheet/05-Power Budget/SableCamSystemPowerBudget.xlsx" type="application/pdf" width="700px" height="700px">
    <embed src="https://egr304-203.github.io/sparkguard/Team203BlockDiagramFinal.pdf">
        <p>This browser does not support PDFs. Please download the PDF to view it: <a href="https://egr304-203.github.io/sparkguard/Team203BlockDiagramFinal.pdf">Download PDF</a>.</p>
    </embed>
</object><br><br>

**Resources** <br>


A link to download the power budget may be found [here] (./SableCamSystemPowerBudget.xlsx)

>If you need the zipped source files of the Power Budget or any other files for this project, please see the [Resources](Appendix/index.md) section.
