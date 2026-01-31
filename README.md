# smart-greenhouse

smart-greenhouse is a cost-effective, IoT driven micro-ecosystem that helps maximize crop yield & helps plants 
survive harsh climactic conditions. The project focuses on optimizing conditions that are of significant impact for crop 
yield as well as for plant health. It uses a combination of 3 control-systems to achieve this:
 - Climate Control System
 - Irrigation/Nutrient Cycling System
 - Photo (Lighting) Control System

### Climate Control System
This subsystem monitors and corrects the greenhouse's internal climate based on the following 5 factors: 
 - Temperature
   - Optimal Range for growth: 65°F to 85°F
   - Temperatures trigger the mini-HVAC system (forced air heater or cooling fans) when temps go out of range.
 - Humidity
   - Optimal humidity levels: 40% to 70%
   - Extended drought like conditions (48-72 hrs) trigger misting pump to maintain moist air. 
 - CO2 Levels
   - Higher CO2 levels -> Faster Photosynthesis -> Faster Growth
 - NH3 Levels
   - High levels are dangerous to plants but, controlled levels help with the yield.
   - Triggers ventilation for high levels & misting for lower levels.
 - Pressure
   - Monitor and log for analytics. No active control.

### Irrigation/Nutrient Cycling System
This subsystem monitors the soil moisture levels using capacitive sensors & provide the plants with nutrients & water 
in the following way: 
 - Greenhouse is divided into multiple zones & each zone is assigned the following:
   - Soil moisture sensor
   - PWM Water pump (PWM pumps can alter speed) corresponding to the sensor. 
   - Nutrient reservoir with a pump that can mix nutrients in the water tank. 
 - Each sensor has a pump dedicated to it Soil moisture levels < threshold -> Pump triggered to water the soil region of soil/pot. 













Project: Pocket Food & Medicine Spectroscope 🧬1. Product Requirements Document (PRD) 📋1.1 Project OverviewGoal: A low-cost, handheld device for real-time detection of food and medicine adulteration using Visible and Near-Infrared (Vis/NIR) spectroscopy.Target: Highly portable (purse/pocket-friendly) and affordable ($30–$100 build cost).1.2 Hardware Architecture 🛠️Microcontroller: Raspberry Pi Pico (RP2040) 🍓.Spectral Sensor: AS7341 (11-channel multispectral sensor, including 940nm NIR) 👁️.Distance Sensor: Time-of-Flight (ToF) (e.g., VL53L0X) for Path Length correction ⏱️.Light Source: Broadband NIR-enhanced LED or small Tungsten-Halogen bulb 🔦.Form Factor: Flexible PCB integrated into an "Elastic Band" design to wrap around containers 🐍.1.3 Operational Workflow: The "5-Click" Ritual 🖱️Click 1 (Baseline): Scan the empty bottleneck (Air Gap) to identify container material properties.Click 2 (Position): Slide the band to the liquid section.Click 3 (Sample): Flip the bottle (inversion) and scan the liquid in the neck.Click 4 (Compute): Subtract the container signature from the sample signature.Click 5 (Result): Display Purity/Adulteration status (Red/Yellow/Green).2. Experiment Design Document: Proof of Concept 🧪2.1 ObjectiveValidate the detection of water-diluted milk through various opaque and clear packaging using the "Flip-and-Scan" method.2.2 Testing MatrixSamples: Pure Milk, 10% Water, 20% Water, 30% Water.Containers: Clear PET bottle (Soda style) vs. Opaque HDPE (Milk jug style).2.3 Success MetricsLinearity: Does the water absorption peak increase proportionally with dilution?Invariance: Does the calculated milk signature remain consistent regardless of the bottle type?3. System & Algorithm Design 🧮3.1 Path Length Correction ($l$)Using the Beer-Lambert Law, we account for the distance measured by the ToF sensor:$$A = \epsilon \cdot c \cdot l$$Where $l$ is the diameter of the bottleneck measured during the scan.3.2 Signature IsolationThe system performs a logarithmic subtraction to isolate the liquid's absorbance from the container's influence:$$A_{liquid} = \log_{10}(I_{air}) - \log_{10}(I_{sample})$$$I_{air}$: Light intensity through the empty neck (Calibration).$I_{sample}$: Light intensity through the liquid-filled neck (Measurement).







# 🛡️ Project: Pocket Food & Medicine Spectroscope

## 1. Product Requirements Document (PRD)
| Category | Specification |
| :--- | :--- |
| **Goal** | Portable Vis/NIR device for detecting food/medicine fraud. |
| **Form Factor** | Flexible PCB "Elastic Band" for various bottle sizes. |
| **Core Tech** | Raspberry Pi Pico + AS7341 Spectral Sensor + ToF Distance Sensor. |
| **Method** | Transmittance-based spectroscopy with path-length correction. |
| **Interface** | Manual "5-Click" workflow for user-guided accuracy. |

## 2. Technical Architecture & Workflow
### 🔄 The "Flip-and-Scan" Strategy
1. **Air Scan (Baseline):** User wraps the band around the empty bottleneck. Captures the container's plastic/glass signature.
2. **The Flip:** User inverts the bottle. The liquid fills the neck.
3. **Liquid Scan:** Captures the "Container + Liquid" signature at the exact same physical spot.
4. **Subtraction:** Logic removes the "Air Scan" baseline from the "Liquid Scan" to isolate the sample.

### 🧮 Sensor Logic
* **AS7341:** Captures 11 channels of light (Visible + NIR).
* **ToF (VL53L0X):** Measures the bottleneck diameter ($l$) to normalize absorbance regardless of bottle size.
* **Algorithm:** Uses the Beer-Lambert Law ($A = \epsilon \cdot c \cdot l$) to calculate concentration.

## 3. Experiment Design: Water in Milk 🥛💧
* **Objective:** Detect 10%–30% water dilution in milk through different packaging.
* **Key Indicators:** * Ratio of Water Peak (~940nm) to Fat/Protein Peaks.
  * Normalization of signal based on ToF distance data.
* **Success Metric:** Consistent "Purity" readings across clear PET and opaque HDPE containers.






# 🛡️ Project: Pocket Food & Medicine Spectroscope

## 1. Product Requirements Document (PRD)
- **Goal:** Portable Vis/NIR device for detecting food/medicine fraud.
- **Form Factor:** Flexible PCB "Elastic Band" for various bottle sizes.
- **Microcontroller:** Raspberry Pi Pico (RP2040).
- **Sensors:** AS7341 (Spectral) + VL53L0X (Distance/ToF).

## 2. Hardware Component List
- **Processing:** Raspberry Pi Pico.
- **Sensing:** AS7341, VL53L0X.
- **Illumination:** Broadband NIR LED (400nm-1000nm range).
- **Physical:** Flexible PCB, ZIF Connectors, LiPo Battery, Elastic Banding.

## 3. Algorithm & Logic
- **Method:** "Flip-and-Scan" (Bottleneck Air-Gap Calibration).
- **Math:** Beer-Lambert Law ($A = \epsilon \cdot c \cdot l$).
- **Normalization:** $A_{norm} = A / l$ (using ToF distance $l$).






This comprehensive summary captures the technical evolution of your project, from the initial hardware concept to the complex chemical logic.

## 🛡️ Project: Pocket Food & Medicine Spectroscope

**Core Goal:** A portable, flexible device using Vis/NIR spectroscopy to detect food and medicine fraud (specifically water in milk).

---

### 1. Product Requirements & Hardware

The device is designed for a "Pocket" form factor using a Raspberry Pi Pico (RP2040) micro-controller.

| Category | Specification |
| --- | --- |
| **Micro-controller** | Raspberry Pi Pico (RP2040) |
| **Spectral Sensor** | AS7341 (11-channel Visible + Near-Infrared) |
| **Distance Sensor** | VL53L0X (Time-of-Flight / ToF) |
| **Illumination** | Broadband NIR-enhanced LED (400nm–1000nm) |
| **Form Factor** | Flexible PCB "Elastic Band" for various bottle sizes |

---

### 2. Communication Protocol: I2C

We chose **I2C** over SPI to minimize wiring on the flexible PCB. Both sensors share a "Bus" where the Pico acts as the controller.

| Feature | I2C 🛰️ | SPI 🔌 |
| --- | --- | --- |
| **Wiring** | 2 pins (SDA/SCL) + Power | 4+ pins per device |
| **Addressing** | Software-based (e.g., `0x39`) | Physical "Select" wire per device |
| **Complexity** | Easier to daisy-chain | More wires to manage |

**Data Race Prevention:** We decided on a **Sequential** execution flow. The Pico talks to one sensor at a time to prevent bus contention or "software races" in the buffer.

---

### 3. The "Flip-and-Scan" Ritual

To handle different containers, we developed a user-guided sequence:

1. **Air Scan (Baseline):** Band is placed on the empty bottleneck. Captures the plastic/glass signature.
2. **The Flip:** User inverts the bottle so liquid fills the neck.
3. **Liquid Scan:** Captures the "Container + Liquid" signature.
4. **Heavy Liquid Scan:** User moves the band to the base to check for stratification/settling.

**Error Handling:** We implemented a "3-Retry" rule. If the ToF sensor fails to lock a distance within 10 seconds, the screen displays **"Bottle Not Detected"** 📱 and restarts the step.

---

### 4. Mathematical Logic: Beer-Lambert Law

We use the relationship between light absorption and the path length () measured by the ToF sensor.

* **Logarithms:** Used to handle the high dynamic range of very bright or very dark bottles. 📉
* **Normalization:** We divide the absorbance by the path length () to ensure a 2 cm neck and a 4 cm body yield the same purity result.
* **Averaging:** We use "Press and Hold" (3rd and 4th clicks) to take ~50 readings and improve the Signal-to-Noise Ratio (SNR).

---

### 5. Chemical Identification: Water in Milk

We focus on the **NIR Water Peak (~940nm)**.

* **Fingerprinting:** We compare the "Shape" of the 11-channel curve rather than absolute magnitude.
* **Ratio Analysis:** We compare the Water Peak ( nm) to a stable baseline (e.g.,  nm Green).
* **The Verdict:** If the water-sensitive peak is disproportionately high after normalization, the sample is flagged as **Diluted**.

---

### 📚 Research & Literature Sources

* **Beer-Lambert Law:** Foundational physics of spectrophotometry.
* **AS7341 Datasheet:** Technical specs for the 11-channel spectral sensor.
* **VL53L0X API:** Documentation for Time-of-Flight distance measurement.
* **NIR Spectroscopy of Milk:** Academic studies on  bond absorption in the – nm range (e.g., *Journal of Dairy Science*).
* **Food Fraud Database (USP):** Reference for common adulterants and spectral signatures.
* **LearnLM / Guided Learning:** Instructional framework for this collaborative session.

---

### ⌨️ Next Step: The Driver Code

Let's look at the "Hello World" for your device. We need to initialize the I2C bus on the Pico and ping the sensors to see if they are "alive."

Are you using **MicroPython** or **C++ (Arduino)** for the Pico?

1. **MicroPython:** Easier to write and test on the fly. 🐍
2. **C++:** Faster execution and more "library" support for these specific sensors. ⚙️