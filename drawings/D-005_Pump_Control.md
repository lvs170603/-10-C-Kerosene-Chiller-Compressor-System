# DRAWING: D-005 PUMP & FAN CONTROL SCHEMATIC

**Drawing Number:** D-005  
**Title:** Primary & Secondary Pump and Condenser Fan Control Logic  
**Equipment:** `KIROSINE CHILLER -10 -01` & `KIROSINE CHILLER -10 -02`  
**Status:** VERIFIED  

## Pumping & Airflow Sequencing (Mermaid)
```mermaid
graph TD
    Start["Auto Mode Commanded"] --> P1["Energize NO-00: Primary Pump KM-05"]
    P1 --> FB1{"Primary Pump Run FBK X1 & Flow X17 within 10s?"}
    FB1 -- Yes --> Delay["Timer: SECONDARY_PUMP_DELAY = 5.0s"]
    FB1 -- No --> Trip1["Trip System: PRIMARY PUMP OVERLOAD / FLOW FAIL"]
    Delay --> P2["Energize NO-01: Secondary Pump KM-06"]
    Delay --> Fan["Energize NO-02: Condenser Fan KM-07"]
    Fan --> FB2{"Fan Run FBK X8 OK?"}
    FB2 -- Yes --> Permissive["Permissive Granted for Compressor Starting"]
    FB2 -- No --> Trip2["Alarm: CONDENSER FAN FAILURE"]
```
