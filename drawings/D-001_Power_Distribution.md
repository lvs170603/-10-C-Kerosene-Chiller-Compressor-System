# DRAWING: D-001 POWER DISTRIBUTION SCHEMATIC

**Drawing Number:** D-001  
**Title:** 415V 3-Phase Main Power Distribution Schematic  
**Equipment:** `KIROSINE CHILLER -10 -01` & `KIROSINE CHILLER -10 -02`  
**Status:** VERIFIED  

## Schematic Diagram (Mermaid)
```mermaid
graph TD
    Incomer["415V AC 3-Phase 50Hz Supply"] --> MCCB["Schneider EasyPact MCCB"]
    MCCB --> Busbars["Distribution Busbars (R-Y-B)"]
    
    Busbars --> VMR["Minilec D2 VMR2 Phase Monitor"]
    Busbars --> EM["Selec EM368 Energy Meter (via CTs)"]
    
    Busbars --> KM1["KM-01: Comp 1 Primary (LC1D40A)"]
    Busbars --> KM2["KM-02: Comp 1 Secondary (LC1D40A)"]
    KM1 & KM2 --> CT1["Minilec S2 CTS1/80 (32-80A)"] --> Comp1["Compressor 1 Motor"]
    
    Busbars --> KM3["KM-03: Comp 2 Primary (LC1D40A)"]
    Busbars --> KM4["KM-04: Comp 2 Secondary (LC1D40A)"]
    KM3 & KM4 --> CT2["Minilec S2 CTS1/80 (32-80A)"] --> Comp2["Compressor 2 Motor"]
    
    Busbars --> KM5["KM-05: Primary Pump (LC1D12)"] --> OL1["LRD12"] --> Pump1["Primary Kerosene Pump"]
    Busbars --> KM6["KM-06: Secondary Pump (LC1D12)"] --> OL2["LRD12"] --> Pump2["Secondary Process Pump"]
    Busbars --> KM7["KM-07: Condenser Fan (LC1D09)"] --> Fan["Condenser Fan Motor"]
    Busbars --> SMPS["SMPS 120W (230VAC / 24VDC 5A)"]
```
