# DRAWING: D-004 COMPRESSOR CONTROL SCHEMATIC

**Drawing Number:** D-004  
**Title:** Dual Compressor Part-Winding Starter Schematics  
**Equipment:** `KIROSINE CHILLER -10 -01` & `KIROSINE CHILLER -10 -02`  
**Status:** VERIFIED  

## Staging & Part-Winding Sequence (Mermaid)
```mermaid
graph TD
    Start["Cooling Demand Active (Outlet > -8.0°C)"] --> SOV["Energize SOV 1 (NO-08)"]
    SOV --> KM1["Energize KM-01: Comp 1 Primary Winding (NO-03)"]
    KM1 --> Delay["Timer: COMP_1 SECONDARY_WINDING_ON_DELAY = 1.0s"]
    Delay --> KM2["Energize KM-02: Comp 1 Secondary Winding (NO-04)"]
    KM2 --> CheckDemand{"Temp > -6.0°C after Stagger Delay?"}
    CheckDemand -- Yes --> SOV2["Energize SOV 2 (NO-09)"]
    SOV2 --> KM3["Energize KM-03: Comp 2 Primary Winding (NO-05)"]
    KM3 --> Delay2["Timer: COMP_2 SECONDARY_WINDING_ON_DELAY = 1.0s"]
    Delay2 --> KM4["Energize KM-04: Comp 2 Secondary Winding (NO-06)"]
    CheckDemand -- No --> Running["Maintain Single Compressor Operation"]
```
