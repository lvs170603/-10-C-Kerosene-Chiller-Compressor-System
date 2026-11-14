# DRAWING: D-007 AUTOMATIC SEQUENCE FLOWCHART

**Drawing Number:** D-007  
**Title:** Automatic Operating Sequence Flowchart  
**Equipment:** `KIROSINE CHILLER -10 -01` & `KIROSINE CHILLER -10 -02`  
**Status:** VERIFIED  

## Operational Flowchart (Mermaid)
```mermaid
flowchart TD
    Boot["System Power ON (Selec PLC & HMI Boot)"] --> SafetyCheck{"Safety Permissives OK?<br>(VMR X0=1, E-Stop=1, OLL=1)"}
    SafetyCheck -- No --> HoldAlarm["Hold in Alarm State (Red Lamp + Buzzer)"]
    SafetyCheck -- Yes --> StartCmd{"AUTO Mode & START Pressed?"}
    StartCmd -- Yes --> StartPriPump["Energize Primary Pump KM-05 (NO-00)"]
    StartPriPump --> CheckFlow{"Flow Switch X17 Closed within 10s?"}
    CheckFlow -- No --> TripFlow["Trip: WATER_FLOW FAILURE Alarm"]
    CheckFlow -- Yes --> StartSecFan["Start Secondary Pump KM-06 & Condenser Fan KM-07<br>(after 5s delay)"]
    StartSecFan --> TempCheck{"Outlet Temp > -8.0°C?"}
    TempCheck -- No --> Standby["Maintain Pump Circulation (Compressors Idle)"]
    TempCheck -- Yes --> StartC1_P["Open SOV 1 & Energize Comp 1 Primary KM-01"]
    StartC1_P --> DelayPW1["Delay 1.0s (COMP_1 SECONDRY_WINDING_ON_DELAY)"]
    DelayPW1 --> StartC1_S["Energize Comp 1 Secondary KM-02"]
    StartC1_S --> Comp2Check{"Temp remains > -6.0°C after Stagger Delay?"}
    Comp2Check -- Yes --> StartC2["Start Comp 2 (SOV 2 + KM-03 + 1.0s + KM-04)"]
    Comp2Check -- No --> Chill["Chilling Cycle Active"]
    StartC2 --> Chill
    Chill --> CutoutCheck{"Outlet Temp <= -10.0°C?"}
    CutoutCheck -- Yes --> StopComps["Close SOVs -> Pumpdown & Cut-out Compressors"]
    StopComps --> TempCheck
```
