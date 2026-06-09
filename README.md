# ICS4111-Greenhouse-IoTProject
# ICS 4111: Embedded Systems & IoT
## Semester Project: Deliverable 1

* **Course Cycle:** April - July 2026
* **Location Reference:** Flora Farms Greenhouses, Naivasha
* **Assigned Flower Type:** Carnations (*Dianthus caryophyllus*)
* **Group Identification:** [Insert Group Number / Name]
* **Group Members:**
  1. [Name 1 & Admission Number] - (Member 1: Git Master)
  2. [Name 2 & Admission Number] - (Member 2: Hardware Vetting)
  3. [Name 3 & Admission Number] - (Member 3: Architect A)
  4. [Name 4 & Admission Number] - (Member 4: Architect B)
  5. [Name 5 & Admission Number] - (Member 5: Architect C)
  6. [Name 6 & Admission Number] - (Member 6: Research Analyst)
 Akinyi Stacy 168327
  2. Savayi Chelsea 150765
  3. Gitahi Mathenge Maribei 166078
  4. Njuru Nick Mugo 166915
---

## 1. Environmental Requirements for Carnation Growth

The table below documents the researched baseline characteristics required to optimize carnation growth in Flora Farms' controlled greenhouse environments:

| Metric | Optimal Range / Value | Characteristics & System Implications |
| :--- | :--- | :--- |
| **a. Optimal Temperature Range** | 18°C - 24°C (Daytime)<br>10°C - 15°C (Nighttime) | Carnations are highly sensitive to temperature. If temperatures rise above 25°C, bud formation stops. Rapid fluctuations can cause calyx splitting. |
| **b. Optimal Relative Humidity Range** | 60% - 70% (Full Growth)<br>80% - 85% (Initial establishment) | High relative humidity combined with heat triggers fungal diseases like rust and leaf stains, while dry conditions lead to brittle stems. |
| **c. Recommended Soil Type** | Rich Sandy Loam / Loamy Sand | Carnation roots go 25 to 30 cm deep and are highly susceptible to poor drainage. Soil must be porous and well-aerated. |
| **d. Optimal Soil Moisture Content** | Water holding capacity of 60% - 65% | Irrigation should be supplied via micro-drip networks frequently but in small quantities to prevent waterlogging and root rot. |
| **e. Optimal Soil pH Range** | 5.5 - 6.5 | Soil pH beyond 7.0 locks up essential nutrients like iron, while a low pH diminishes soil microbial life. |
| **f. Sunlight Exposure Hours** | 13 hours (Critical Photoperiod) | Carnations are facultative long-day plants. They require a minimum of 6 hours of full light and benefit from long daylight periods to enhance stem rigidity and flower size. |

> **LPG Monitoring Note:** The greenhouse relies on an LPG heating system to keep nighttime temperatures within the optimal 10°C - 15°C window. The embedded system uses the MQ-5 sensor to continuously monitor air composition for accidental leaks of methane, butane, or propane to preserve crops and safe operations.

---

## 2. Prototyping Hardware Component List & Datasheet Links

To monitor the criteria above and handle the greenhouse environment safely, the following hardware bill of materials is designated for prototyping:

* **Microcontroller:** [ESP32S DevKIT WiFi + BLE Module (30-Pin)](https://www.espressif.com/sites/default/files/documentation/esp32-wroom-32_datasheet_en.pdf)
  * *Role:* Acts as the core microcontroller edge node. It reads sensor data, drives the display, and manages communication over the greenhouse WiFi router.
* **Display:** [1.3" White IIC 128X64 OLED LCD](https://www.adafruit.com/product/938)
  * *Role:* Provides local telemetry visualization inside the greenhouse for field operators.
* **Climate Sensor:** [DHT22 AM2302 Temperature and Humidity sensor](https://www.sparkfun.com/datasheets/Sensors/Temperature/DHT22.pdf)
  * *Role:* Measures ambient temperature and relative humidity levels inside the greenhouse canopy.
* **Gas Sensor:** [MQ-5 LPG, Natural Gas, and Coal Gas Sensor](https://www.sparkfun.com/datasheets/Sensors/Biometrics/MQ-5.pdf)
  * *Role:* Detects traces of LPG leaked from the greenhouse's space heaters.
* **Actuator Control:** [5V 1-Channel Low Level Trigger Relay Module](https://www.songle.com)
  * *Role:* Operates as an electronic switch to control automated equipment like fans or heaters.
* **Prototyping Accessories:** Full-sized breadboards, male-to-male/male-to-female jumper wires, pull-up resistors for the I2C bus lines, and a voltage divider network (1kΩ and 2kΩ resistors) to drop the MQ-5's 5V analog signal output safely down to the ESP32's 3.3V ADC tolerance.

---

## 3. Architecture Schematic Designs

*Note: The images below reference the circuit schematics uploaded to our project files.*

### Architecture A: Single-Node Multi-Sensor Topography
* **Description:** A standalone master node configuration. One single ESP32S reads telemetry data from both the MQ-5 Gas Sensor (via a voltage divider into an analog pin) and the DHT22 (via a digital pin with a 4.7kΩ pull-up resistor) while directly updating the local 1.3" OLED via an I2C interface (SDA/SCL pins).
* **Circuit Diagram:** ![Architecture A Diagram](architecture_a.png)

### Architecture B: Interfaced Dual-Node Topography
* **Description:** Distributed processing configuration. One ESP32S functions as a dedicated safety node monitoring the MQ-5 sensor. It directly interfaces with a second standalone ESP32S node that reads the DHT22 climate sensor using standard serial UART communication protocols (TX to RX, RX to TX, common Ground).
* **Circuit Diagram:** ![Architecture B Diagram](architecture_b.png)

### Architecture C: Relay-Isolated Dual-Node Topography
* **Description:** Hardware-isolated signaling configuration. One ESP32S samples the ambient climate using the DHT22 sensor. If parameters fall outside of threshold parameters, it changes the state of a 5V Low-Level Trigger Relay. The relay contacts close an input pin loop on a secondary ESP32S node which is actively handling gas safety with the MQ-5 sensor.
* **Circuit Diagram:** ![Architecture C Diagram](architecture_c.png)

---

## 4. Evidence of Groupwork

* **Discussion Date:** June 9, 2026
* **Discussion Summary & Task Distribution:**
  * **Member 1:** Setup the team's GitHub repository, formatted and managed the Markdown document compilation.
  * **Member 2:** Sourced component datasheets and calculated necessary resistor values for our logic safety matching.
  * **Member 3:** Drafted and exported the circuit schematic for Architecture A.
  * **Member 4:** Drafted and exported the circuit schematic for Architecture B.
  * **Member 5:** Drafted and exported the circuit schematic for Architecture C.
  * **Member 6:** Compiled agricultural data regarding Carnation micro-climates and soil parameters.

### Team Evidence Artifact
![Group Collaboration Proof](group_evidence.png)



















# ICS 4111: Embedded Systems & IoT
## Semester Project: Deliverable 1
**Course Cycle:** April - July 2026 
**Location Reference:** Flora Farms Greenhouses, Naivasha 
**Assigned Flower Type:** Carnations (*Dianthus caryophyllus*) 
**Group Members:** 1. Akinyi Stacy 168327
  2. Savayi Chelsea 150765
  3. Gitahi Mathenge Maribei 166078
  4. Njuru Nick Mugo 166915
  5. [Name 5 & Admission Number]
  6. [Name 6 & Admission Number]

---

## 1. Environmental Requirements for Carnation Growth
The table below documents the baseline characteristics required to optimize carnation growth in Flora Farms' controlled greenhouse environments:

| Metric | Optimal Range / Value | Characteristics & System Implications |
| :--- | :--- | :--- |
| **a. Optimal Temperature Range** |**$18^\circ\text{C} - 24^\circ\text{C}$** (Day) <br>**$10^\circ\text{C} - 15^\circ\text{C}$** (Night) | Highly temperature-sensitive. Night heating keeps values optimal. |
| **b. Optimal Relative Humidity Range** |**60% - 70%** | Prevents structural brittleness and limits fungal growth. |
| **c. Recommended Soil Type** | **Rich Sandy Loam / Loamy Sand**  | Critical for highly sensitive root drainage requirements. |
| **d. Optimal Soil Moisture Content** | **60% - 65%** water capacity | Managed via micro-drip networks to avoid root rot. |
| **e. Optimal Soil pH Range** | **5.5 - 6.5**  | Keeps essential micro-nutrients soluble. |
| **f. Sunlight Exposure Hours** | **13 hours** (Photoperiod)  | Facultative long-day plants requiring ample light. |

> **LPG Monitoring Note:** The greenhouse heating system runs on LPG. The embedded architecture utilizes the MQ-5 sensor to monitor for accidental leaks of methane, butane, or propane to protect crops and ensure site safety.

---

## 2. Prototyping Hardware Component List
[cite_start]Prototyping bill of materials for greenhouse implementation[cite: 14, 15]:
* [cite_start]**ESP32S DevKIT WiFi + BLE Module (30-Pin)** [cite: 19]
* [cite_start]**1.3" White IIC 128X64 OLED LCD** [cite: 18]
* [cite_start]**DHT22 AM2302 Temperature and Humidity sensor** [cite: 20]
* [cite_start]**MQ-5 LPG, natural gas, coal gas Sensor** [cite: 22]
* [cite_start]**5V 1-Channel Low Level Trigger Relay Module** [cite: 23]
* [cite_start]**Prototyping Tools:** Breadboards, Jumper Wires, 4.7kΩ pull-up resistor, 1kΩ and 2kΩ resistors (for 5V to 3.3V MQ-5 analog voltage division)[cite: 15, 29].

---

## 3. Datasheets & Product Documentation Links
* [cite_start]**ESP32S Module:** [ESP32-WROOM-32 Datasheet](https://www.espressif.com/sites/default/files/documentation/esp32-wroom-32_datasheet_en.pdf) [cite: 16, 19]
* [cite_start]**1.3" IIC OLED Display:** [Adafruit Monochrome OLED Page](https://learn.adafruit.com/monochrome-oled-breakouts) [cite: 16, 18]
* [cite_start]**DHT22 Climate Sensor:** [DHT22 Temperature-Humidity Datasheet](https://www.sparkfun.com/datasheets/Sensors/Temperature/DHT22.pdf) [cite: 16, 20]
* [cite_start]**MQ-5 Gas Sensor:** [MQ-5 Sensor Technical Data](https://www.sparkfun.com/datasheets/Sensors/Biometric/MQ-5.pdf) [cite: 16, 22]
* [cite_start]**5V 1-Channel Relay Module:** [Songle 5V Relay Specifications](https://components101.com/switches/5v-relay-module-pinout-features-applications-alternative-datasheet) [cite: 16, 23]

---

## 4. Architectural Schematic Diagrams
[cite_start]*Note: Schematics are exported from our design tool and referenced below[cite: 24, 30].*

### Architecture A: Single-Node Multi-Sensor Topography
* [cite_start]**Description:** 1 ESP32S connected directly to 1 MQ-5, 1 DHT22, and 1 OLED LCD[cite: 25].
* ![Architecture A Diagram](./images/architecture_a.png)

### Architecture B: Interfaced Dual-Node Topography
* [cite_start]**Description:** 1 ESP32S connected to 1 MQ-5 interfaced directly with another ESP32S connected to 1 DHT22[cite: 26].
* ![Architecture B Diagram](./images/architecture_b.png)

### Architecture C: Relay-Isolated Dual-Node Topography
* [cite_start]**Description:** 1 ESP32S connected to 1 DHT22 connected to 1 relay which is connected to another ESP32S connected to 1 MQ-5[cite: 27].
* ![Architecture C Diagram](./images/architecture_c.png)

---

## 5. Evidence of Groupwork
* [cite_start]**Discussion Date:** June 9, 2026 [cite: 68]
* **Task Distribution:**
    * [cite_start]*Member 1:* Handled GitHub repo initialization and structured final Markdown file[cite: 30, 62].
    * [cite_start]*Member 2:* Sourced component datasheets and validated web documentation links[cite: 16].
    * [cite_start]*Member 3:* Drafted Single-Node Architecture A schematic design[cite: 25].
    * [cite_start]*Member 4:* Drafted Interfaced Dual-Node Architecture B schematic design[cite: 26].
    * [cite_start]*Member 5:* Drafted Relay-Isolated Architecture C schematic design[cite: 27].
    * [cite_start]*Member 6:* Gathered botanical metrics for Carnations and compiled collaboration minutes[cite: 5, 6, 68].
* **Meeting Artifact:**
[cite_start]![Minutes of Meeting and Design Session](./images/group_evidence.jpg) [cite: 68]
