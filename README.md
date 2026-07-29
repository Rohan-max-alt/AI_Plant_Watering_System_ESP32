# AI-Powered Smart Plant Care System 🌿🤖

An intelligent IoT and AI-driven solution for automated plant monitoring and watering. Never let your plants dry out or suffer from overwatering again!

---

## 1. Project Overview & The Problem

I observed an issue and wanted to check if it was just me, so I did some research. I found out that out of every **100 houses, at least 25 have more than 10 plants**. After circulating a survey and gathering **269 responses** for this AI-powered device, I am certain this will be in every plant lover's house in the future.

### Pain Points Addressed:
* **Forgetting to water** plants regularly.
* **Overwatering**, which damages roots.
* **Underwatering**, causing plants to dry out.
* **Changing water requirements** across different seasons.
* **Busy lifestyles** making manual plant care difficult.

> *Usually, you buy a plant because you feel good about it—why not maintain it hassle-free?*

---

## 2. How It Works (The AI & Hardware)

Can AI take care of plants automatically? **Yes.** 

Our system continuously monitors soil moisture, measures surrounding temperature and humidity, predicts watering requirements, automatically triggers watering, and learns from historical data to minimize water wastage.

### Hardware Architecture:
* **ESP32 Microcontroller:** Chosen because it's affordable, powerful, has built-in Wi-Fi, and is perfect for IoT projects.
* **Capacitive Soil Moisture Sensor:** Continuously measures the soil moisture level without quick corrosion.
* **Relay Module & Mini Water Pump:** Automatically delivers water from a reservoir through silicone tubing when triggered.

### The AI Advantage:
Instead of relying on fixed moisture thresholds forever, the system logs sensor readings and watering events over time. Using a machine learning model, it predicts the optimal time to water each plant based on:
* Soil Moisture
* Temperature & Humidity
* Time Since Last Watering
* Seasonal Changes

---

## 3. Getting Started & Open Source

I wanted this project to be something anyone could build. That's why the complete project is **open-source**, including hardware designs, source code, wiring diagrams, and documentation. 

Whether you're a beginner, a student, or an experienced maker, you can replicate it, customize it, and contribute new features!

### Quick Setup Instructions:
1. **Hardware Wiring:** Connect your ESP32, capacitive soil sensor, and relay module according to the detailed pinout guide.
2. **Backend / AI Script:** Run the Python script (`app.py`) to host the Flask API and machine learning model.
3. **Firmware:** Flash your ESP32 using the Arduino IDE to send sensor payloads and handle automated pump triggers.


# AI_Plant_Watering_System_ESP32
Alternative (If using separate files):
If you want to keep them separated (e.g., in VS Code or PyCharm):

Make sure you save the first code block into a file named ai_plant_model.py.

Save the second code block into a file named app.py.

Ensure both files are saved inside the exact same folder/directory before running app.py.

## Requirementss:

Component,Component Pin,ESP32 Pin,Description
Soil Sensor,VCC,3.3V,Power Supply
Soil Sensor,GND,GND,Ground
Soil Sensor,AOUT,GPIO 36 (VP),Analog Moisture Reading
Relay Module,VCC,5V / VIN,Relay Logic Power
Relay Module,GND,GND,Ground
Relay Module,IN,GPIO 23,Pump Trigger Signal

## 1. Component List

* **ESP32 Microcontroller Board** (NodeMCU-32S or standard ESP32 DevKit V1)
* **Capacitive Soil Moisture Sensor v1.2** (Avoid resistive sensors, as they corrode quickly in wet soil)
* **5V Relay Module** (Single channel, to control the water pump)
* **Mini Submersible Water Pump** (3V - 6V)
* **External 5V Power Supply** (USB power bank or 5V 2A adapter — *Do not power the pump directly from the ESP32's 5V pin, as it can reset the board*)
* **Jumper Wires** (Male-to-Female and Male-to-Male)
* **Silicone Tubing**

---

## 2. Detailed Pinout Connections

### A. Capacitive Soil Moisture Sensor Connections
Capacitive sensors output an analog signal that changes based on water content.
* **VCC (Power):** Connect to **3.3V** on the ESP32 *(Note: While some sensors accept 5V, connecting VCC to 3.3V prevents analog reference voltage discrepancies).*
* **GND (Ground):** Connect to **GND** on the ESP32.
* **AOUT (Analog Output):** Connect to **GPIO 36 (VP / ADC0)** on the ESP32.

### B. Relay Module & Water Pump Connections
The relay acts as an electronic switch. The ESP32 triggers the relay, which in turn powers the pump using an external power supply.
* **DC+ / VCC (Relay Power):** Connect to **VIN / 5V** on the ESP32 (or directly to your external 5V positive rail).
* **DC- / GND (Relay Ground):** Connect to **GND** on the ESP32.
* **IN (Signal):** Connect to **GPIO 23** on the ESP32.

#### Water Pump Wiring:
* Connect the **Positive (+ / Red)** wire of the water pump to the **Common (COM)** terminal of the relay.
* Connect a wire from the **Normally Open (NO)** terminal of the relay to the **Positive (+)** terminal of your external 5V power supply.
* Connect the **Negative (- / Black)** wire of the pump directly to the **Negative (-)** terminal of the external 5V power supply.
* *(Make sure all Grounds—ESP32, Relay, and Power Supply—are common/tied together if using separate power sources).*

---

## 3. Quick Pin Reference Table

| Component | Component Pin | ESP32 Pin | Description |
| :--- | :--- | :--- | :--- |
| **Soil Sensor** | VCC | 3.3V | Power Supply |
| **Soil Sensor** | GND | GND | Ground |
| **Soil Sensor** | AOUT | GPIO 36 (VP) | Analog Moisture Reading |
| **Relay Module** | VCC | 5V / VIN | Relay Logic Power |
| **Relay Module** | GND | GND | Ground |
| **Relay Module** | IN | GPIO 23 | Pump Trigger Signal |
