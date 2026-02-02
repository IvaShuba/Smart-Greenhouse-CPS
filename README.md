# 🌱 Smart Greenhouse CPS
A modular two‑node cyber‑physical system for automated plant monitoring and environmental control.  
Built with bare‑metal C, SPI communication, low‑power design, and a clean, scalable architecture.

---

## 🚀 Overview
This project implements a **Smart Greenhouse Cyber‑Physical System (CPS)** consisting of a **Master node** (Arduino‑based) and a **Slave node** (ATmega328PB, bare‑metal).  
The system monitors environmental conditions and controls actuators such as a fan, pump, LED lighting, and a servo‑driven ventilation door.

The architecture is modular, energy‑efficient, and designed for reliability and extensibility.

---

## 🏗 System Architecture

### **Master Node (Arduino)**
- Soil moisture sensor (ADC)
- DHT11 temperature & humidity sensor (digital protocol)
- Fan and pump control via optocoupler + MOSFET drivers
- LCD 16×2 display (I2C)
- SPI Master communication
- State‑machine logic for environmental control
- Serial logging and diagnostics to Node-Red

### **Slave Node (ATmega328PB, bare‑metal C)**
- Light sensor (ADC)
- Door position sensors (limit switches)
- Servo motor for ventilation door
- LED lamp control
- SPI Slave communication
- Deep sleep mode (WDT + INT1 wake‑up)
- Command‑based actuator control

---

## 🔌 Communication Protocol
- **SPI Mode 2**
- **Command‑based interface**, including:
  - `CMD_LED_ON / CMD_LED_OFF`
  - `CMD_DOOR_OPEN / CMD_DOOR_CLOSE`
  - `CMD_GET_SENSOR`
  - `CMD_GET_STATE`
- **Packet structure**
  - Timestamp  
  - Sensor values  
  - Actuator states  
  - Checksum  
  - End marker `0xAA`

---

## ⚙️ Features
- Modular firmware architecture (sensing / control / protocol / UI)
- Low‑power slave node with watchdog sleep
- Reliable SPI communication with checksum verification
- Deterministic state‑machine control logic
- LCD visualization of system state
- Logging system with configurable verbosity
- MOSFET‑driven actuators with optocoupler isolation
- Clear separation of sensing and actuation responsibilities


---

## 🔋 Power Management
- Slave node uses **SLEEP_MODE_PWR_DOWN**
- Wake‑up via **WDT interrupt** or **external INT1**
- Sensors and actuators activated only when required
- Significantly reduces idle power consumption

---

## 🧠 State Machine Logic
The master node controls:
- Fan activation based on temperature/humidity thresholds  
- Pump activation based on soil moisture  
- LED lighting based on light sensor data  
- Ventilation door based on environmental conditions  

All decisions follow a deterministic state‑machine model.

---

## 🛠 Hardware Highlights
- Optocoupler‑isolated MOSFET drivers for fan and pump  
- Servo‑controlled ventilation door  
- Analog and digital sensors  
- 5V logic with proper isolation and protection  
- Modular wiring for easy debugging and testing

---

## 🧪 Example Log Output        //2do



---

## 🎓 Skills Demonstrated
- Bare‑metal C programming (AVR)
- Interrupts, timers, watchdog, ADC
- SPI protocol design and implementation
- Low‑power embedded design
- Modular firmware architecture
- Hardware debugging and driver design
- State‑machine control logic
- LCD UI and serial diagnostics
- Node-Red data flow handling

---

## 📜 License
MIT License

---

## 📸 Photos
*(prototype, wiring, LCD...)*         //2do
