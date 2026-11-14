# DRAWING: D-002 PLC ARCHITECTURE DIAGRAM

**Drawing Number:** D-002  
**Title:** Selec MiBRX Modular PLC Hardware & Module Slot Architecture  
**Equipment:** `KIROSINE CHILLER -10 -01` & `KIROSINE CHILLER -10 -02`  
**Status:** VERIFIED  

## Architecture Overview (Mermaid)
```mermaid
graph TD
    subgraph Selec_MiBRX_Rack["Selec MiBRX Modular PLC CPU (24V DC Supply)"]
        CPU["MiBRX Base Unit (LCD Display + Keypad Navigation)"]
        Slot1["Slot 1: MIBRX-SC-AI/RTD (Ch 0: Outlet PT100, Ch 1: Inlet PT100)"]
        Slot2["Slot 2: MIBRX-SC-DI06 (LP1, HP1, MDL1, OLL1, LP2, HP2, MDL2, OLL2, Flow)"]
        Slot3["Slot 3: Power & DI (24V Incomer, VMR, Pump FBKs, Comp FBKs)"]
        Slot4["Slot 4 & 5: MIBRX-SC-RO (Primary/Secondary Pumps, Fan, Comp 1 P/S)"]
        Slot6["Slot 6: MIBRX-SC-RO (Comp 2 P/S, SOV 1/2, Red/Yellow/Green Lamps, Buzzer)"]
    end
    
    HMI["Selec ATSEL SP112 HMI (7-Inch Touch)"] <-- RS-485 Modbus COM3 --> CPU
```
