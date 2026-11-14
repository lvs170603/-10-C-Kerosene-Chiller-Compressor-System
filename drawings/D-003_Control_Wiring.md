# DRAWING: D-003 CONTROL WIRING SCHEMATIC

**Drawing Number:** D-003  
**Title:** 24V DC & 230V AC Control Circuit Wiring Schematic  
**Equipment:** `KIROSINE CHILLER -10 -01` & `KIROSINE CHILLER -10 -02`  
**Status:** VERIFIED  

## Functional Diagram (Mermaid)
```mermaid
graph TD
    SMPS["SMPS 120W (24VDC 5A)"] -->|24V+| EStop["Emergency Stop Pushbutton"]
    EStop -->|+24V Bus| SafetyLoop["Field Safety Loop"]
    
    SafetyLoop --> LP1["X9: LP 1 Switch"] --> PLC_DI["Selec MiBRX Inputs"]
    SafetyLoop --> HP1["X10: HP 1 Switch"] --> PLC_DI
    SafetyLoop --> MDL1["X11: MDL 1 Module"] --> PLC_DI
    SafetyLoop --> OLL1["X12: OLL 1 Relay"] --> PLC_DI
    SafetyLoop --> Flow["X17: Flow Switch"] --> PLC_DI
    SafetyLoop --> VMR["X0: VMR2 Relay"] --> PLC_DI
    SafetyLoop --> PumpOL["X3: Pump OLL Relay"] --> PLC_DI
    
    PLC_DO["Selec MiBRX Outputs"] -->|NO-03| KM1["Comp 1 Pri KM-01 (24V Coil)"]
    PLC_DO -->|NO-04| KM2["Comp 1 Sec KM-02 (24V Coil)"]
    PLC_DO -->|NO-05| KM3["Comp 2 Pri KM-03 (24V Coil)"]
    PLC_DO -->|NO-06| KM4["Comp 2 Sec KM-04 (24V Coil)"]
    
    230V["230V AC Bus"] --> PLC_DO_HV["PLC Relay Contacts"]
    PLC_DO_HV -->|NO-00| KM5["Primary Pump Contactor (230V Coil)"]
    PLC_DO_HV -->|NO-01| KM6["Secondary Pump Contactor (230V Coil)"]
    PLC_DO_HV -->|NO-02| KM7["Condenser Fan Contactor (230V Coil)"]
    PLC_DO_HV -->|NO-08| SOV1["Liquid Line Solenoid Valve 1"]
    PLC_DO_HV -->|NO-09| SOV2["Liquid Line Solenoid Valve 2"]
```
