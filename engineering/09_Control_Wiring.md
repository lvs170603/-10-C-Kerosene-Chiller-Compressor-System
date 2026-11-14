# ENGINEERING DOCUMENT: 09_CONTROL_WIRING

**Document Number:** ED-CHIL-09  
**Revision:** Rev 1.0  
**Status:** APPROVED FOR ENGINEERING REFERENCE  
**Date:** 14-11-2026  
**Equipment Tags:** `KIROSINE CHILLER -10 -01` & `KIROSINE CHILLER -10 -02`  

---

## 1. Control Power Distribution (24V DC & 230V AC)
The control panel incorporates a dual-voltage architecture:
1. **24V DC Bus:** Sourced from the DIN-rail mounted 120W SMPS (Output: 24V DC, 5A). Supplies power to:
   - Selec MiBRX Modular PLC CPU and modules.
   - Selec ATSEL SP112 HMI touch panel.
   - All digital input field safety switches (LP, HP, flow, overload feedbacks).
   - Schneider LC1D40A compressor contactor coils (Coil A1/A2 labeled 24V).
2. **230V AC Bus:** Sourced from Phase R to Neutral via control fuse / MCB. Supplies power to:
   - Auxiliary pump and fan contactor coils (`KM-05`, `KM-06`, `KM-07`).
   - Liquid line refrigerant solenoid valves (`SOV 1`, `SOV 2`).
   - Panel door indicator lamps (Red, Yellow, Green) and audible alarm buzzer.

---

## 2. Terminal Block Schedule (Detailed Ferrule Mapping)

### 2.1 Digital Input & Safety Rail (Left Terminal Strip)
| Terminal No | Ferrule Tag | Connected Device / Field Cable | Voltage | Logic State |
| :--- | :--- | :--- | :--- | :--- |
| **TB-01** | `24V` | SMPS +24V Distribution Common | +24V DC | Power Bus |
| **TB-02** | `0V` | SMPS 0V Return Common | 0V DC | Power Bus |
| **TB-03** | `X9 (LP1)` | Circuit 1 Low Pressure Switch NC/NO | +24V DC | Closed = Normal |
| **TB-04** | `X10 (HP1)` | Circuit 1 High Pressure Switch NC | +24V DC | Closed = Normal |
| **TB-05** | `X11 (MDL1)`| Compressor 1 Kriwan/PTC Module NC | +24V DC | Closed = Normal |
| **TB-06** | `X12 (OLL1)`| Compressor 1 Minilec MPR D2 Relay 95-96 | +24V DC | Closed = Normal |
| **TB-07** | `X13 (LP2)` | Circuit 2 Low Pressure Switch NC/NO | +24V DC | Closed = Normal |
| **TB-08** | `X14 (HP2)` | Circuit 2 High Pressure Switch NC | +24V DC | Closed = Normal |
| **TB-09** | `X15 (MDL2)`| Compressor 2 Kriwan/PTC Module NC | +24V DC | Closed = Normal |
| **TB-10** | `X16 (OLL2)`| Compressor 2 Minilec MPR D2 Relay 95-96 | +24V DC | Closed = Normal |
| **TB-11** | `X17 (FW)` | Kerosene Circulation Paddle Flow Switch | +24V DC | Closed = Flow OK |

### 2.2 Analog Temperature Sensor Rail (Slot 1 RTD)
| Terminal No | Ferrule Tag | Connected Instrument | Sensor Wire |
| :--- | :--- | :--- | :--- |
| **TB-RTD-01**| `RTD1-0` | TE-01: Chilled Kerosene Outlet Temp | Red (Element +) |
| **TB-RTD-02**| `RTD2-0` | TE-01: Chilled Kerosene Outlet Temp | White (Element -) |
| **TB-RTD-03**| `RTD3-0` | TE-01: Chilled Kerosene Outlet Temp | White (Compensation) |
| **TB-RTD-04**| `RTD1-1` | TE-02: Return Kerosene Inlet Temp | Red (Element +) |
| **TB-RTD-05**| `RTD2-1` | TE-02: Return Kerosene Inlet Temp | White (Element -) |
| **TB-RTD-06**| `RTD3-1` | TE-02: Return Kerosene Inlet Temp | White (Compensation) |

### 2.3 Power & Actuator Load Rail (Right Terminal Strip)
| Terminal No | Ferrule Tag | Connected Load | Voltage Rating |
| :--- | :--- | :--- | :--- |
| **TB-L1** | `R1, Y1, B1` | Primary Kerosene Pump Motor T1, T2, T3 | 415V AC 3-Phase |
| **TB-L2** | `R2, Y2, B2` | Secondary Process Pump Motor T1, T2, T3 | 415V AC 3-Phase |
| **TB-L3** | `R3, Y3, B3` | Condenser Fan Motor T1, T2, T3 | 415V AC 3-Phase |
| **TB-L4** | `NO8 (SOV 1)` | Circuit 1 Liquid Line Refrigerant Solenoid Valve Coil | 230V AC |
| **TB-L5** | `NO9 (SOV 2)` | Circuit 2 Liquid Line Refrigerant Solenoid Valve Coil | 230V AC |
| **TB-N** | `N` | Neutral Distribution Common | Neutral |
