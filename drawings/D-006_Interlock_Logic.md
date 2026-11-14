# DRAWING: D-006 INTERLOCK LOGIC DIAGRAM

**Drawing Number:** D-006  
**Title:** Master Safety Interlock Logic Diagram  
**Equipment:** `KIROSINE CHILLER -10 -01` & `KIROSINE CHILLER -10 -02`  
**Status:** VERIFIED  

## Safety Logic Tree (Mermaid)
```mermaid
graph TD
    subgraph System_Permissives["System Permissives (Both Circuits Trip)"]
        EStop["Emergency Stop Healthy"]
        VMR["X0: Minilec VMR2 Voltage Healthy"]
        PumpOL["X3: Primary Pump Overload Healthy"]
        Flow["X17: Kerosene Flow Switch Closed"]
    end

    subgraph Circuit1_Permissives["Circuit 1 Permissives"]
        HP1["X10: HP 1 High Pressure Normal"]
        LP1["X9: LP 1 Low Pressure Normal"]
        MDL1["X11: MDL 1 Motor Temp Normal"]
        OLL1["X12: OLL 1 Motor Overload Normal"]
    end

    subgraph Circuit2_Permissives["Circuit 2 Permissives"]
        HP2["X14: HP 2 High Pressure Normal"]
        LP2["X13: LP 2 Low Pressure Normal"]
        MDL2["X15: MDL 2 Motor Temp Normal"]
        OLL2["X16: OLL 2 Motor Overload Normal"]
    end

    System_Permissives --> AND1((AND Gate))
    Circuit1_Permissives --> AND2((AND Gate))
    Circuit2_Permissives --> AND3((AND Gate))

    AND1 --> RunSystem["Enable System Operation"]
    RunSystem & AND2 --> RunC1["Permit Compressor 1 Operation"]
    RunSystem & AND3 --> RunC2["Permit Compressor 2 Operation"]
```
