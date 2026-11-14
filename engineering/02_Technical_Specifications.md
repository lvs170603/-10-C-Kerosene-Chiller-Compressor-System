# ENGINEERING DOCUMENT: 02_TECHNICAL_SPECIFICATIONS

**Document Number:** ED-CHIL-02  
**Revision:** Rev 1.0  
**Status:** APPROVED FOR ENGINEERING REFERENCE  
**Date:** 14-11-2026  
**Equipment Tags:** `KIROSINE CHILLER -10 -01` & `KIROSINE CHILLER -10 -02`  

---

## 1. Electrical Specifications
| Parameter | Specification | Status | Evidence / Reference |
| :--- | :--- | :--- | :--- |
| **Main Power Supply** | 415 V AC ± 10%, 3-Phase, 50 Hz | **VERIFIED** | Minilec VMR2 Rating & MCCB Incomer |
| **Main Circuit Breaker** | Schneider Electric EasyPact MCCB, 3-Pole | **VERIFIED** | Photo `12.47.53.jpeg` |
| **Control Voltage (PLC & Digital I/O)** | 24 V DC (Regulated, 5A, 120W SMPS) | **VERIFIED** | Photo `12.47.50.jpeg` |
| **Control Voltage (Relay Coils)** | 230 V AC / 24 V DC (Dual Bus) | **VERIFIED** | Engineering Notepad Pg 1 (`16.17.32 (1).jpeg`) |
| **Compressor Contactors** | 4x Schneider TeSys LC1D40A (40A AC-3, 24V Coils) | **VERIFIED** | Photos `12.47.52 (1).jpeg`, `16.15.54.jpeg` |
| **Auxiliary Contactors** | Schneider TeSys LC1D12 (Pumps), LC1D09 (Fan) | **VERIFIED** | Photo `12.47.54 (2).jpeg` |
| **Auxiliary Thermal Overloads** | Schneider TeSys LRD12 (Differential Bimetal) | **VERIFIED** | Photo `12.47.54 (2).jpeg` |
| **Motor Protection Relays** | 2x Minilec MPR D2 (Aux 415V, Trip Time 2/5s) | **VERIFIED** | Photos `12.47.53 (1).jpeg`, `12.47.55.jpeg` |
| **Current Transducers** | 2x Minilec S2 CTS1/80 (32 A to 80 A range) | **VERIFIED** | Photo `12.47.54 (1).jpeg` |
| **Voltage / Phase Relay** | Minilec D2 VMR2 (Unbalance: 4-20%, UV: 165-245V, OV: 230-310V) | **VERIFIED** | Photos `12.47.56 (1).jpeg`, `12.47.57.jpeg` |
| **Panel Energy Meter** | Selec EM368 Multifunction Meter (3-Ph, 4-Wire) | **VERIFIED** | Photo `12.47.49.jpeg` |

---

## 2. Automation & Controller Specifications
| Parameter | Specification | Status | Evidence / Reference |
| :--- | :--- | :--- | :--- |
| **PLC Hardware Platform** | Selec MiBRX Modular Micro PLC | **VERIFIED** | Hardware Faceplate (`12.47.55 (1).jpeg`) |
| **Digital Input Module** | Selec MIBRX-SC-DI06 (6 Channel 24VDC Opto) | **VERIFIED** | Module Label (`16.15.50 (1).jpeg`) |
| **Analog Input Module** | Selec MIBRX-SC-AI/RTD (3-Wire PT100 RTD) | **VERIFIED** | Terminal Wiring (`16.15.49 (1).jpeg`) |
| **Relay Output Modules** | Selec MIBRX-SC-RO (Form-A Relay, 5A 250VAC) | **VERIFIED** | Terminal Block (`16.15.52.jpeg`) |
| **HMI Model** | Selec ATSEL SP112-GT70-S1-CE | **VERIFIED** | Rear Nameplate (`12.47.48 (1).jpeg`) |
| **HMI Power Rating** | 20.4 to 28.8 V DC, 0.3 A | **VERIFIED** | Rear Nameplate (`12.47.48 (1).jpeg`) |
| **Communication Port** | Serial RS-485 (`COM3`), Modbus RTU | **VERIFIED** | Comm Error Screen (`16.16.03 (2).jpeg`) |
| **Baud Rate / Parity** | 19200 Baud, 8 Data Bits, 2 Stop Bits, No Parity | **VERIFIED** | Comm Error Screen (`16.16.03 (2).jpeg`) |

---

## 3. Chiller Operating Parameters (HMI Configured)
| Parameter | Programmed Value | Status | Evidence / Reference |
| :--- | :--- | :--- | :--- |
| **Temperature Setpoint** | **-10.0 °C** | **VERIFIED** | Settings Screen (`12.47.46.jpeg`) |
| **Temperature Differential** | **2.0 °C** (Cut-out: -10°C, Cut-in: -8°C) | **VERIFIED** | Settings Screen (`12.47.46.jpeg`) |
| **Fault Sensing Delay** | **10 Seconds** | **VERIFIED** | Settings Screen (`12.47.46.jpeg`) |
| **Float Feedback Delay** | **5 Seconds** | **VERIFIED** | Settings Screen (`12.47.46.jpeg`) |
| **Secondary Pump Delay** | **5 Seconds** | **VERIFIED** | Settings Screen (`12.47.46.jpeg`) |
| **Comp 1 2nd Winding Delay** | **1 Second** | **VERIFIED** | Settings Screen (`12.47.46.jpeg`) |
| **Comp 2 2nd Winding Delay** | **1 Second** | **VERIFIED** | Settings Screen (`12.47.46.jpeg`) |

---

## 4. Refrigeration Specifications
| Parameter | Specification | Status | Evidence / Reference |
| :--- | :--- | :--- | :--- |
| **Number of Compressors** | Two (2) Semi-Hermetic Reciprocating/Screw | **INFERRED** | Dual Contactors & Gauges |
| **Compressor Maker / Model** | **NOT AVAILABLE** | **FIELD VERIFICATION REQUIRED** | Missing machine compartment photos |
| **Refrigerant Type** | **NOT AVAILABLE** (Likely R404A / R507A / R22) | **FIELD VERIFICATION REQUIRED** | Standby Pressure ~145-150 PSI |
| **Circuit 1 Standby LP** | ~35 PSI (~2.4 bar) | **VERIFIED** | Panel Gauge 1 (`21.30.22.jpeg`) |
| **Circuit 1 Standby HP** | ~150 PSI (~10.3 bar) | **VERIFIED** | Panel Gauge 2 (`21.30.22.jpeg`) |
| **Circuit 2 Standby LP** | ~35 PSI (~2.4 bar) | **VERIFIED** | Panel Gauge 3 (`21.30.22.jpeg`) |
| **Circuit 2 Standby HP** | ~145 PSI (~10.0 bar) | **VERIFIED** | Panel Gauge 4 (`21.30.22.jpeg`) |
| **Solenoid Valves** | 2x Liquid Line Solenoids (`SOV 1`, `SOV 2`) | **VERIFIED** | Terminal Blocks & Notepad |
