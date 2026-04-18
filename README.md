# EFIS Hardware — 5-Inch Raspberry Pi IO Board

**Status:** Open Hardware — Experimental Amateur-Built Category  
**Form Factor:** 5-inch display, Raspberry Pi host  
**Files:** PCB Gerbers, BOM, Pick-and-Place, Schematic PDF, STEP model

---

## What This Is

This repository contains the **PCB hardware design files** for a 5-inch EFIS IO expansion board intended for use with a Raspberry Pi single-board computer running [pyEfis](../pyEfis). The IO board extends the Raspberry Pi with the physical interfaces needed to connect aircraft hardware: buttons, rotary encoders, analog inputs, CAN bus, and indicator outputs.

This is a companion hardware design to the [7-inch BeagleBone-based EFIS hardware](../efis-hardware-7-inch). The 5-inch RPi variant is lower cost and uses more readily available components.

## Repository Contents

| File | Description |
|---|---|
| `IO Board/Gerber Files/` | Fabrication-ready PCB Gerber files for the IO expansion board |
| `IO Board/IO Board - BOM.csv` | Bill of Materials with part numbers and quantities |
| `IO Board/IO Board - Pick and Place.csv` | Pick-and-place assembly file for SMT manufacturing |
| `IO Board/IO Board - Schematic.pdf` | Full schematic for review and assembly verification |
| `IO Board/IO Board.step` | 3D STEP model for mechanical integration and enclosure design |

## Hardware Stack

This board is designed around:
- **Raspberry Pi** (any model with 40-pin GPIO header) as the compute host
- **5-inch capacitive touchscreen display** (compatible RPi DSI or HDMI display)
- This IO board as the interface between the RPi and aircraft wiring

## Software

The IO board is designed to work with:
- **[pyEfis](../pyEfis)** — the EFIS display software running on the Raspberry Pi
- **[FIX-Gateway](../fix-gateway)** — the data broker that connects hardware inputs and sensor data to the display
- Raspberry Pi plugin modules in FIX-Gateway handle GPIO, SPI ADC (`rpi_mcp3008`), I2C sensors (`rpi_bno055`, `rpi_bmp085`), rotary encoders, and buttons

## Building and Ordering

1. **PCB fabrication:** Send the Gerber files to any PCB manufacturer (JLCPCB, PCBWay, OSH Park, etc.)
2. **Assembly:** Use the BOM and Pick-and-Place files for SMT assembly, or hand-solder using the schematic
3. **Verification:** Review `IO Board - Schematic.pdf` before assembly to confirm wiring to your specific display and RPi model
4. **Mechanical:** Import `IO Board.step` into your CAD tool for enclosure and panel cutout design

## Role in the MakerPlane / MAOS Ecosystem

This board provides the **physical hardware layer** for a low-cost primary flight display. Combined with [pyEfis](../pyEfis) and [FIX-Gateway](../fix-gateway), it forms a complete EFIS unit that can display attitude, airspeed, altitude, heading, moving map, and engine data sourced from the aircraft CAN-FIX network.

For MAOS integration, this hardware could serve as the cockpit display for MAOS avionics data published through FIX-Gateway.

## Important Disclaimer

> This is open hardware for Experimental Amateur-Built aircraft use only.  
> PCB designs have not been independently reviewed for airworthiness.  
> The builder is responsible for all fabrication, assembly, and installation decisions.
