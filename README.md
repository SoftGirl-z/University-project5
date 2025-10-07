# 👶 Infant Incubator System
### *Arduino-Based Embedded Control and Node-RED Web Dashboard Integration*

This project — developed for **CMSE423: Embedded System Design** at **Eastern Mediterranean University** — presents a **cyber-physical system** for controlling and monitoring a **baby incubator** using **Arduino** and **Node-RED**.  
The system provides **temperature regulation**, **real-time monitoring**, and **bidirectional communication** between physical and digital components.

---

## 🧠 Project Overview

The **Infant Incubator System** (also called **DigiTerm-05**) integrates embedded hardware with a cloud-based dashboard. It continuously monitors the incubator’s air and body temperatures, applies proportional control via PWM, and allows remote supervision and configuration through a Node-RED interface.

💡 *Goal:*  
Maintain a safe and stable thermal environment for infants by combining real-time data acquisition, control, and user-friendly visualization.

---

## 🧩 Key Features

- 🌡️ **Dual Temperature Sensors (NTC)** for precise air and body monitoring  
- 🔁 **Proportional Control (P-Control)** to regulate heater output  
- 🖥️ **Node-RED Dashboard** for live visualization and remote commands  
- 🔌 **UART Communication** between Arduino and PC  
- ⚠️ **Alarm System** for over-temperature and cover-open detection  
- 🧾 **LCD Display** for local temperature and alarm readouts  
- 🔒 **Safety Mechanisms** — automatic cutoff above 37°C  

---

## 🛠️ Hardware & Software Components

| Type | Components |
|------|-------------|
| **Hardware** | Arduino UNO R3, NTC Thermistor (10kΩ, B=3900), Resistors, LEDs, 16×2 LCD, COMPIM (Serial Interface) |
| **Software** | Arduino IDE, Proteus 8.9, Node-RED v3.1.0, VSPE, SciLab + XCos |
| **Languages** | C/C++ (Arduino), Node.js (Node-RED) |
| **Simulation Tools** | Proteus ISIS & VSM, Virtual Oscilloscope, CMScope |

---

## ⚙️ System Architecture

1️⃣ **Low-End Unit (Arduino):**  
- Measures ThA (air) and ThB (body) via ADC  
- Computes error *(ThD – ThB)*  
- Generates PWM to control heater  
- Sends periodic UART data to PC  
- Receives commands like `(370)d` or `(15)s`  

2️⃣ **High-End Unit (Node-RED Dashboard):**  
- Reads UART data via COM port  
- Displays live gauges and charts for ThA, ThB, PP, alarms  
- Allows user to update ThD and sampling time (Ts)  
- Provides visual alerts for unsafe conditions  

---

## 🧮 Control Logic Summary

**Control Law:**  
\[
PP = K_p \times (ThD - ThB)
\]  
- \(K_p = 10\)  
- Output limited to 1 ≤ PP ≤ 99  

**PWM Cycle:**  
- Period = 10 s  
- Resolution = 0.1 s per step  
- Heater ON duration = \(PP\%\) of 10 s  

**Safety Cutoff:**  
- If \(ThA ≥ 37.0°C\) or \(ThB ≥ 37.0°C\) → Heater OFF  

---

## 🧪 Key Experiments & Results

| Test | Description | Result |
|------|--------------|--------|
| **LED Flash & UART Sync** | Verified 5s LED blink with 9600 baud UART output | ✅ Accurate timing, <2% error |
| **ADC Calibration** | Validated NTC readings 15–45°C | ✅ ±0.3°C precision |
| **P-Control Action** | Verified proportional heater response | ✅ Stable, linear response |
| **PWM Test** | 10s cycle with varying duty | ✅ <±0.1s deviation |
| **Node-RED Communication** | Real-time monitoring & control | ✅ Full bidirectional functionality |

---

## 🌐 Node-RED Dashboard

**Dashboard Features:**  
- Live gauges for ThA, ThB, PP, and alarms  
- Temperature charts (ThA/ThB vs Time)  
- Sliders for Desired Temp (ThD) & Sampling Time (Ts)  
- Real-time UART-based updates every 10s  
- Accessible locally via [http://127.0.0.1:1880/ui](http://127.0.0.1:1880/ui)

---

## 🧠 Simulation Summary

- **Modeling Tool:** SciLab Xcos  
- **CPS Model:** Combines physical (heater & thermistor) and cyber (controller) subsystems  
- **Result:**  
  - Achieved ThA = 37°C within 40s  
  - Overshoot ≤ 0.8°C  
  - Disturbance recovery within 25s  

---

## 🧑‍💻 Team Members

| Name | ID | Role |
|------|----|------|
| **Sohrab Memari** | 21008211 | Team Leader, System Designer |
| **Fadel Jermaine Serunjogi** | 21901874 | Hardware Integration & Modeling |
| **Ahmet Can Kartal** | 22002306 | Firmware Developer |
| **Dheyab Bin Ahmed** | 22703500 | Control Logic & PWM Design |
| **Hamit Bora Işık** | 21000059 | Testing & Validation |
| **Kaan Sulkalar** | 20000063 | Simulation & Analysis |
| **Nadir Deniz Memişoğlu** | 20300044 | Modeling & CPS Verification |
| **Zeynep Pelin Çolak** | 17300009 | Node-RED Dashboard & Documentation |

---

## 🏗️ Course Information

**Course:** CMSE423 – Embedded System Design  
**Instructor:** Prof. Dr. Hadi Işık Aybay  
**Semester:** Spring 2025  
**Department:** Computer Engineering, Eastern Mediterranean University  

---

## ✅ Conclusion

The **Infant Incubator System** successfully demonstrates a fully functional **cyber-physical control loop** integrating **Arduino-based temperature regulation** with a **Node-RED IoT dashboard**.  
It meets all technical and functional design requirements for precision, reliability, and safety in neonatal temperature management.  

---

## 🔗 References

- [Arduino Documentation](https://docs.arduino.cc/)  
- [Node-RED](https://nodered.org/)  
- [Proteus Design Suite](https://www.labcenter.com/)  
- [SciLab Xcos](https://www.scilab.org/)  
