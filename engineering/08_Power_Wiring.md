# ENGINEERING DOCUMENT: 08_POWER_WIRING

**Document Number:** ED-CHIL-08  
**Revision:** Rev 1.0  
**Status:** APPROVED FOR ENGINEERING REFERENCE  
**Date:** 14-11-2026  
**Equipment Tags:** `KIROSINE CHILLER -10 -01` & `KIROSINE CHILLER -10 -02`  

---

## 1. Incoming Power Supply & Distribution
The chiller electrical power system receives 415 V AC, 3-Phase, 4-Wire, 50 Hz power via bottom gland plates.

### 1.1 Incomer Switchgear
- **Main Breaker:** Schneider Electric EasyPact MCCB (Molded Case Circuit Breaker).
- **Incoming Busbars:** Heavy-gauge insulated copper busbars with heat-shrink sleeves color-coded:
  - **Red Phase (R):** Connected to MCCB Terminal L1.
  - **Yellow Phase (Y):** Connected to MCCB Terminal L2.
  - **Blue Phase (B):** Connected to MCCB Terminal L3.
- **Reference:** Photo `WhatsApp Image 2026-11-14 at 12.47.53.jpeg`.

---

## 2. Power Circuit Functional Architecture

```mermaid
flowchart TD
    Incomer["415V AC 3-Phase Supply"] --> MCCB["Schneider EasyPact MCCB"]
    MCCB --> Busbars["Distribution Busbars R-Y-B"]
    
    Busbars --> VMR["Minilec D2 VMR2 Phase Monitor"]
    Busbars --> EM["Selec EM368 Energy Meter (via CTs)"]
    
    Busbars --> KM1["KM-01: Comp 1 Primary (LC1D40A)"]
    Busbars --> KM2["KM-02: Comp 1 Secondary (LC1D40A)"]
    KM1 & KM2 --> CT1["Minilec S2 CTS1/80 Current Transducer"]
    CT1 --> Motor1["Compressor 1 Motor Terminals (U1-V1-W1 / U2-V2-W2)"]
    
    Busbars --> KM3["KM-03: Comp 2 Primary (LC1D40A)"]
    Busbars --> KM4["KM-04: Comp 2 Secondary (LC1D40A)"]
    KM3 & KM4 --> CT2["Minilec S2 CTS1/80 Current Transducer"]
    CT2 --> Motor2["Compressor 2 Motor Terminals (U1-V1-W1 / U2-V2-W2)"]
    
    Busbars --> KM5["KM-05: Primary Pump (LC1D12)"] --> OL1["LRD12 Thermal Overload"] --> Pump1["Primary Kerosene Pump Motor"]
    Busbars --> KM6["KM-06: Secondary Pump (LC1D12)"] --> OL2["LRD12 Thermal Overload"] --> Pump2["Secondary Process Pump Motor"]
    Busbars --> KM7["KM-07: Condenser Fan (LC1D09)"] --> Fan["Air-Cooled Condenser Fan Motor"]
    
    Busbars --> SMPS["120W SMPS (230VAC to 24VDC 5A)"]
```

---

## 3. Compressor Power Circuit Wiring
- **Starting Method:** Part-Winding Start (PW, 50% / 50% split).
- **Power Cables:** High-temperature multi-strand copper cables routed through slotted trunking.
- **Current Transducers:**
  - 3-phase power conductors pass through the window of the **Minilec S2 CTS1/80 Current Convertor** (Range 32 - 80 Amp) before reaching motor terminals.
  - Secondary output terminals from CTS1/80 connect to terminals 7, 8, 9, 10, 11, 12 of the **Minilec MPR D2** Motor Protection Relay.
- **Contactor Interlocking:** Contactors `KM-01` and `KM-02` operate in parallel during running conditions. `KM-01` provides starting torque; `KM-02` energizes 1.0 second later.
