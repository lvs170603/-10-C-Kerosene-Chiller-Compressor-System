# ENGINEERING DOCUMENT: 12_MAINTENANCE_MANUAL

**Document Number:** ED-CHIL-12  
**Revision:** Rev 1.0  
**Status:** APPROVED FOR ENGINEERING REFERENCE  
**Date:** 14-11-2026  
**Equipment Tags:** `KIROSINE CHILLER -10 -01` & `KIROSINE CHILLER -10 -02`  

---

## 1. Preventive Maintenance Philosophy
Routine preventive maintenance is critical to ensure operational reliability, prevent catastrophic compressor failure, avoid kerosene contamination, and maintain thermodynamic efficiency for the -10°C process chilling duty.

---

## 2. Maintenance Schedule

### 2.1 Daily Operational Checks (Operator Shift Log)
- Record Chilled Kerosene Outlet Temperature on ATSEL SP112 HMI (Target: -10.0°C).
- Record Circuit 1 and Circuit 2 Suction (LP) and Discharge (HP) pressures from front panel gauges.
- Check panel pilot lamps (R, Y, B healthy; no Red trip lamp).
- Check Selec EM368 energy meter for balanced 3-phase running currents.
- Inspect liquid line sight glasses for pure liquid flow (no vapor bubbles).
- Inspect compressor crankcase oil sight glasses for proper oil level (between 1/4 and 3/4 glass).

### 2.2 Weekly Maintenance Tasks
- Inspect air-cooled condenser coils for surface dust, leaves, or chemical deposits.
- Check Primary and Secondary Kerosene circulation pump glands/mechanical seals for leakage.
- Verify operation of panel cooling fan and clean air filter pad on panel door.
- Verify HMI alarm history log for intermittent warnings.

### 2.3 Monthly Maintenance Tasks
- Clean air-cooled condenser coils using pressurized nitrogen or approved coil cleaning solvent.
- Inspect compressor contactors (`KM-01` to `KM-04`) for contact pitting, carbon buildup, or chatter.
- Check all terminal block screws in the electrical panel for torque tightness (thermal cycling causes loosening).
- Test manual trip mechanism on Schneider `LRD12` thermal overload relays and Minilec `MPR D2`.
- Check kerosene expansion tank level and inspect for water contamination.

### 2.4 Quarterly Maintenance Tasks
- Perform complete electronic refrigerant leak test across all joints, flanges, and service valves.
- Calibrate PT100 temperature sensors (`TE-01`, `TE-02`) against a certified reference probe at 0°C ice point.
- Check compressor motor insulation resistance (Megger test at 500V DC; minimum acceptable: > 5 Megohms).
- Verify trip setpoints of Minilec `D2 VMR2` (Under-voltage, Over-voltage, Phase unbalance).

### 2.5 Annual Overhaul Tasks
- Replace liquid line filter drier cores.
- Test compressor lubricant acidity and moisture content; replace oil and clean suction screen if degraded.
- Inspect and test calibration of mechanical HP and LP safety pressure switches.
- Inspect evaporator plate heat exchanger for fouling or kerosene wax deposition.
