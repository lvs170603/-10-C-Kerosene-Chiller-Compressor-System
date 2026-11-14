# ENGINEERING DOCUMENT: 01_PROJECT_OVERVIEW

**Document Number:** ED-CHIL-01  
**Revision:** Rev 1.0  
**Status:** APPROVED FOR ENGINEERING REFERENCE  
**Date:** 14-11-2026  
**Equipment Tags:** `KIROSINE CHILLER -10 -01` & `KIROSINE CHILLER -10 -02`  
**System OEM:** R I INDUSTRIES  

---

## 1. Executive Summary
This document provides the high-level project description, system objectives, and functional boundaries for the two packaged -10°C Low-Temperature Kerosene Chillers installed at the industrial processing facility. The equipment serves as the primary low-temperature refrigeration source for a Single Fluid Heating & Cooling System manufactured by Schematic Engineering Industries, providing chilled kerosene to temperature-controlled chemical reactor jackets (Reactor Tags: `RE-1101` and `RE-1109`).

---

## 2. Equipment Identification & Baseline Data
| Engineering Field | Data / Value | Evidence / Verification Status |
| :--- | :--- | :--- |
| **Equipment Tag 01** | `KIROSINE CHILLER -10 -01` | **VERIFIED** (Control Panel Upper Placard) |
| **Equipment Tag 02** | `KIROSINE CHILLER -10 -02` | **VERIFIED** (Control Panel Enclosure Sticker) |
| **Original Equipment Manufacturer (OEM)** | R I INDUSTRIES ("We honour commitments with integrity") | **VERIFIED** (Metal Nameplate & Splash Screen) |
| **Chiller Configuration** | Packaged Air-Cooled Liquid Chiller (Dual Circuit) | **VERIFIED** (Physical Enclosure & Gauges) |
| **Secondary Coolant / Brine** | Industrial Kerosene | **VERIFIED** (Placards & Process Skid P&ID) |
| **Design Chilled Fluid Outlet Temp** | **-10.0 °C** | **VERIFIED** (PLC HMI Programmed Setpoint) |
| **Refrigeration Circuits** | Two (2) Independent Hermetic/Semi-Hermetic Circuits | **VERIFIED** (Dual Contactors, Gauges, HP/LP) |
| **Compressor Staging / Starting** | Part-Winding Start (PW) with 1.0s Inter-Winding Delay | **VERIFIED** (Dual 40A Contactors per Compressor) |
| **Automation Controller** | Selec MiBRX Modular Micro PLC | **VERIFIED** (Hardware Faceplate) |
| **Operator Interface** | Selec ATSEL SP112 7" Color Touchscreen HMI | **VERIFIED** (Model SP112-GT70-S1-CE) |
| **Process Integration** | Single Fluid Skid (Schematic Engineering Industries) | **VERIFIED** (Process Stahl HMI Screens) |

---

## 3. Process Architecture & System Purpose
The primary function of each chiller unit is to chill recirculating kerosene from an ambient return temperature down to **-10.0 °C**. Kerosene is selected as the low-temperature secondary refrigerant due to its low freezing point (below -40°C), relatively low viscosity at sub-zero temperatures, and compatibility with low-temperature chemical synthesis processes.

### 3.1 Primary & Secondary Fluid Circuits
1. **Primary Kerosene Circulation Loop:**
   - Kerosene is drawn from a cold buffer tank / return header by the **Primary Kerosene Pump** (`KM-05`, controlled by PLC DO `NO-00`).
   - The fluid passes through the Chiller Evaporator (Plate Heat Exchanger or Shell & Tube) where heat is transferred to the boiling refrigerant.
   - Fluid flow confirmation is verified by paddle flow switch `X17` (`WATER_FLOW`).
2. **Secondary Process Delivery Loop:**
   - The **Secondary Process Pump** (`KM-06`, controlled by PLC DO `NO-01`) circulates chilled kerosene across the facility to Plate Heat Exchanger `PHE-A01` on the Reactor Skid (`RE-1101` / `RE-1109`).
   - Modulating three-way or control valves (`TCV_A01`) on the reactor skid blend fluid into the reactor jacket to maintain precise reaction temperatures.

---

## 4. Verification Evidence & Traceability
- **Placard Verification:** Photograph `WhatsApp Image 2026-11-14 at 21.30.22.jpeg` confirms enclosure dimensions, 4 panel pressure gauges, and the label `KIROSINE CHILLER -10 -02`.
- **Panel Internal Verification:** Photograph `WhatsApp Image 2026-11-14 at 12.47.48.jpeg` confirms unit `01` panel layout, Schneider switchgear, Minilec relays, and Selec automation hardware.
