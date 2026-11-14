# ENGINEERING DOCUMENT: 11_TROUBLESHOOTING_MANUAL

**Document Number:** ED-CHIL-11  
**Revision:** Rev 1.0  
**Status:** APPROVED FOR ENGINEERING REFERENCE  
**Date:** 14-11-2026  
**Equipment Tags:** `KIROSINE CHILLER -10 -01` & `KIROSINE CHILLER -10 -02`  

---

## 1. Purpose & Safety Instructions
This manual provides logical diagnostic flowcharts and step-by-step resolution procedures for operators and maintenance technicians servicing the -10°C Kerosene Chiller.

> [!CAUTION]
> **ELECTRICAL HAZARD:** Ensure the main Schneider MCCB is padlocked in the OFF position (LOTO) before inspecting contactors, terminal screws, or motor junction boxes. Never bypass pressure switches or overload relays.

---

## 2. High-Frequency Fault Diagnostic Procedures

### 2.1 Fault 01: "PRIMARY PUMP OVERLOAD" Active on HMI
- **HMI Message:** Popup banner `PRIMARY PUMP OVERLOAD`.
- **PLC Signal:** Input `X3` is de-energized (0V).
- **Physical Device:** Schneider TeSys `LRD12` Overload Relay attached to Contactor `KM-05`.
- **Root Causes:**
  1. Fluid Viscosity / Low Temperature Resistance: At sub-zero temperatures, kerosene or contaminated fluid viscosity increases, overloading the impeller.
  2. Mechanical Jamming: Foreign particles inside pump casing or worn bearings.
  3. Improper Current Setting: Thermal dial on `LRD12` set lower than motor Full Load Amperes (FLA).
  4. Single Phasing: Loose terminal screw on R1, Y1, or B1 phase.
- **Step-by-Step Diagnostic Procedure:**
  1. Isolate main power. Open control panel door.
  2. Inspect the test/reset indicator on `LRD12` relay (under `KM-05`). Verify if red trip flag is extended.
  3. Feel pump motor casing for excessive heat.
  4. Rotate pump shaft manually to ensure free rotation without binding.
  5. Check motor nameplate FLA and verify `LRD12` dial setting matches FLA (or 1.05x FLA).
  6. Measure winding resistance across R1-Y1, Y1-B1, B1-R1 using a calibrated digital multimeter; ensure balance within 2%.
  7. Press blue RESET button on `LRD12`.
  8. Close panel door, restore power, and press `FAULT RESET` on ATSEL SP112 HMI.

### 2.2 Fault 02: HMI Modbus Communication Error (`COM3 19200-8-2-NONE`)
- **HMI Message:** `Communication Error: No data response [1#0x513(13)]`.
- **Root Causes:**
  1. Emergency Stop button is depressed, removing 24V power to PLC CPU.
  2. 24V DC SMPS output breaker/fuse blown.
  3. Loose RS-485 serial communication wires (A/B) on HMI COM3 or PLC port.
- **Diagnostic Procedure:**
  1. Inspect the panel door Emergency Stop pushbutton. Twist clockwise to release if latched.
  2. Check blue LCD screen on Selec MiBRX PLC. If LCD is dark, check 24V DC power at SMPS output terminals.
  3. Check RS-485 shielded cable connections between HMI port COM3 and PLC serial port. Verify tight terminal screws.

### 2.3 Fault 03: High Pressure Alarm (`HP_1` / `HP_2` Trip)
- **PLC Signal:** Input `X10` (Circuit 1) or `X14` (Circuit 2) is OPEN (0V).
- **Physical Device:** Danfoss / Alco High Pressure Switch mounted on discharge line.
- **Root Causes:**
  1. Condenser fan not running (contactor `KM-07` not energized, fan motor overload, or blown fuse).
  2. Air-cooled condenser fins clogged with industrial dust, dirt, or debris.
  3. Non-condensable gases (air) in refrigeration circuit.
  4. Refrigerant overcharge.
- **Diagnostic Procedure:**
  1. Observe front panel HP pressure gauges. If discharge pressure exceeds 350-400 PSI, high pressure cutoff has engaged.
  2. Inspect condenser fan deck. Verify fan blades rotate freely and airflow is unobstructed.
  3. Inspect condenser coils. Clean fins using low-pressure compressed air or coil cleaner spray.
  4. Once discharge pressure cools below reset threshold, press the manual red reset pin on the mechanical HP switch.
  5. Clear alarm on HMI using `FAULT RESET`.

### 2.4 Fault 04: Low Pressure Alarm (`LP_1` / `LP_2` Trip)
- **PLC Signal:** Input `X9` (Circuit 1) or `X13` (Circuit 2) is OPEN (0V).
- **Root Causes:**
  1. Refrigerant leakage in circuit resulting in undercharge.
  2. Liquid line solenoid valve (`SOV 1` / `SOV 2`) failed to open (burnt coil or no 230V command from PLC `NO-08` / `NO-09`).
  3. Thermostatic expansion valve (TXV) powerhead lost charge or orifice blocked with ice/sludge.
  4. Moisture in system freezing across expansion orifice.
- **Diagnostic Procedure:**
  1. Observe LP pressure gauge on front panel. If suction pressure is below 15-20 PSI, verify static pressure.
  2. Check moisture indicator sight glass on liquid line. If yellow, moisture is present in refrigerant; replace filter drier core.
  3. Check 230V AC voltage at solenoid valve coil terminals during compressor start command. Verify magnetic pull using a solenoid tester.
  4. Conduct electronic refrigerant leak detection across flare joints, valve stems, and brazed fittings.

### 2.5 Fault 05: Kerosene Temperature Not Reaching -10.0 °C
- **Symptoms:** Compressors running continuously, but outlet temperature stalls above -5.0°C.
- **Root Causes:**
  1. Secondary process heat load exceeding chiller refrigeration capacity.
  2. Fouled / scaled evaporator plate heat exchanger reducing heat transfer coefficient.
  3. Low kerosene circulation flow rate.
  4. One compressor tripped or running with degraded compressor valves.
- **Diagnostic Procedure:**
  1. Verify both Compressor 1 and Compressor 2 are running simultaneously. Check current on Selec EM368 meter.
  2. Measure temperature differential between Inlet (`TE-02`) and Outlet (`TE-01`). Expected $\Delta T$ is typically 3.0°C to 5.0°C.
  3. Measure suction line superheat at compressor service valve (expected: 5K to 8K).
  4. Inspect reactor skid PHE-A01 for thermal bypass or excessive process flow.
