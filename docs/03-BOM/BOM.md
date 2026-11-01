---
title: Bill of Materials
---

# Bill of Materials

This is the full parts list for my humidity sensing subsystem. It covers every part on my schematic, plus the extras I need for breadboard testing, debugging and spares.

## How I chose the quantities

- **1 for the PCB**, matching the reference designators on the schematic.
- **1 breadboard version** where one exists. The MCP6001 only comes in tiny surface-mount packages, so I'm ordering the MCP6002 in a DIP-8 package to test the amplifier on a breadboard first. The L7805, pushbutton and pin headers are already through-hole, so they work on both.
- **1 to 2 spares** of each part in case something gets damaged during soldering. I ordered 2 spare SHT31 sensors because the DFN package is the easiest part to ruin.


## Debugging and expandability hardware

- **Test points TP1-TP10** (Keystone 5000 red, 5001 black for GND) on the power rails, sensor output, amplifier output, ADC input and both UART lines, so a meter or scope probe can clip on.
- **Jumpers JP1, JP2, JP3 and JP9** with removable shunts, so I can disconnect the sensor supply, either UART line or the Nano's VTG and test each section on its own.
- **J4 spare GPIO header** with 8 unused PIC pins for expansion.
- **Socketed Curiosity Nano** on female headers, so it can be removed or swapped without desoldering.
- **Replaceable fuse** held in PCB fuse clips.
- **Keyed 2x4 IDC header** for the team ribbon cable, so the cable can't be plugged in backwards.

## Parts list

All parts are ordered from Digi-Key on one purchase request.

| Ref | Description | Manufacturer | Part # | Qty on PCB | Qty ordered | Unit price | Line total | Supplier |
|---|---|---|---|:---:|:---:|---:|---:|---|
| U3 | Analog humidity/temperature sensor, ratiometric 0.5-4.5 V output, ±2 %RH, DFN-8 | Sensirion | [SHT31-ARP-B](https://www.digikey.com/en/products/detail/sensirion-ag/SHT31-ARP-B/5872251) | 1 | 3 | $5.00 | $15.00 | Digi-Key |
| U4 | Single rail-to-rail op amp, 1 MHz, SOT-23-5 | Microchip | [MCP6001T-I/OT](https://www.digikey.com/en/products/detail/microchip-technology/MCP6001T-I-OT/697158) | 1 | 3 | $0.30 | $0.90 | Digi-Key |
| U4 (breadboard) | Dual rail-to-rail op amp, 1 MHz, PDIP-8 (breadboard version of U4) | Microchip | [MCP6002-I/P](https://www.digikey.com/en/products/detail/microchip-technology/MCP6002-I-P/500875) | 0 | 2 | $0.45 | $0.90 | Digi-Key |
| U2 | 5 V 1.5 A linear regulator, TO-220 | STMicroelectronics | [L7805CV](https://www.digikey.com/en/products/detail/stmicroelectronics/L7805CV/585964) | 1 | 3 | $1.14 | $3.42 | Digi-Key |
| J1 | DC barrel jack, 2.0 mm pin, 5.5 mm OD, through-hole right angle | Same Sky (CUI Devices) | [PJ-002A](https://www.digikey.com/en/products/detail/same-sky-formerly-cui-devices/PJ-002A/96962) | 1 | 2 | $0.66 | $1.32 | Digi-Key |
| F1 | Fuse, 500 mA fast-acting, 250 V, 5 x 20 mm | Littelfuse | [0217.500HXP](https://www.digikey.com/en/products/detail/littelfuse-inc/0217-500HXP/777105) | 1 | 4 | $0.60 | $2.40 | Digi-Key |
| F1 | Fuse clip, 111 series, 10 A 250 V, through-hole, for 5 x 20 mm fuses | Littelfuse | [01110501Z](https://www.digikey.com/en/products/detail/littelfuse-inc/01110501Z/2518598?s=N4IgTCBcDaIAwEYlwKyIFogLoF8g) | 2 | 4 | $0.20 | $0.80 | Digi-Key |
| J2 | Four-wall shrouded header, 2x4 (8 pos), 2.54 mm, keyed, through-hole vertical | 3M | [N2508-6002-RB](https://www.digikey.com/en/products/detail/3m/N2508-6002-RB/2609703) | 1 | 2 | $2.31 | $4.62 | Digi-Key |
| J4, JP1, JP2, JP3, JP9 | Male pin header, 1x40, 2.54 mm, breakaway | Sullins | [PRPC040SAAN-RC](https://www.digikey.com/en/products/detail/sullins-connector-solutions/PRPC040SAAN-RC/2775214) | 1 | 3 | $1.23 | $3.69 | Digi-Key |
| U1 socket | Female socket header, 1x14, 2.54 mm, through-hole straight | Sullins | [PPTC141LFBN-RC](https://www.digikey.com/en/products/detail/sullins-connector-solutions/PPTC141LFBN-RC/810152?s=N4IgTCBcDaIMoFcA2SCWA7AzgAgAq4BUBhARgBYSAZAMQCEA5AWgCUiQBdAXyA) | 4 | 6 | $0.87 | $5.22 | Digi-Key |
| JP1, JP2, JP3, JP9 | Jumper shunt, 2 position, 2.54 mm | Sullins | [SPC02SYAN](https://www.digikey.com/en/products/detail/sullins-connector-solutions/SPC02SYAN/76375) | 4 | 6 | $0.10 | $0.60 | Digi-Key |
| SW1 | Tactile pushbutton, 6 x 6 mm, SPST-NO, through-hole | TE Connectivity | [1825910-6](https://www.digikey.com/en/products/detail/te-connectivity-alcoswitch-switches/1825910-6/1632536) | 1 | 3 | $0.13 | $0.39 | Digi-Key |
| D1 | LED, green, 0805 | Lite-On | [LTST-C171GKT](https://www.digikey.com/en/products/detail/liteon/LTST-C171GKT/386793) | 1 | 3 | $0.15 | $0.45 | Digi-Key |
| D2 | LED, yellow, 0805 | Lite-On | [LTST-C171YKT](https://www.digikey.com/en/products/detail/liteon/LTST-C171YKT/386807) | 1 | 3 | $0.13 | $0.39 | Digi-Key |
| D3 | LED, red, 0805 | Lite-On | [LTST-C171KRKT](https://www.digikey.com/en/products/detail/liteon/LTST-C171KRKT/386801) | 1 | 3 | $0.16 | $0.48 | Digi-Key |
| R1, R7, R8 | Resistor, 330 Ω, 5 %, 1/8 W, 0805 | Yageo | [RC0805JR-07330RL](https://www.digikey.com/en/products/detail/yageo/RC0805JR-07330RL/728311?s=N4IgTCBcDaIEoGEAMAOJBWAUnAtEg7AMyFJwAyIAugL5A) | 3 | 6 | $0.11 | $0.66 | Digi-Key |
| R2, R3, R9 | Resistor, 10 kΩ, 5 %, 1/8 W, 0805 | Yageo | [RC0805JR-0710KL](https://www.digikey.com/en/products/detail/yageo/RC0805JR-0710KL/728241?s=N4IgTCBcDaIEoGEAMAOJBWAUnAtEg7AIxIDSAMiALoC%2BQA) | 3 | 6 | $0.10 | $0.60 | Digi-Key |
| R4 | Resistor, 1.8 kΩ, 5 %, 1/8 W, 0805 | Yageo | [RC0805JR-071K8L](https://www.digikey.com/en/products/detail/yageo/RC0805JR-071K8L/728236?s=N4IgTCBcDaIEoGEAMAOJBWAUnAtEg7AIwDSKAMiALoC%2BQA) | 1 | 3 | $0.10 | $0.30 | Digi-Key |
| R5 | Resistor, 3.3 kΩ, 5 %, 1/8 W, 0805 | Yageo | [RC0805JR-073K3L](https://www.digikey.com/en/products/detail/yageo/RC0805JR-073K3L/728299?s=N4IgTCBcDaIEoGEAMAOJBWAUnAtEg7AMwDShAMiALoC%2BQA) | 1 | 3 | $0.11 | $0.33 | Digi-Key |
| R6, R10 | Resistor, 1 kΩ, 5 %, 1/8 W, 0805 | Yageo | [RC0805JR-071KL](https://www.digikey.com/en/products/detail/yageo/RC0805JR-071KL/728218?s=N4IgTCBcDaIEoGEAMAOJBWAUnAtEg7AIwDSAMiALoC%2BQA) | 2 | 4 | $0.11 | $0.44 | Digi-Key |
| R11 | Resistor, 1 kΩ, 1 %, 1/8 W, 0805 | Yageo | [RC0805FR-071KL](https://www.digikey.com/en/products/detail/yageo/RC0805FR-071KL/727444?s=N4IgTCBcDaIEoGEAMAOJBWAYnAtEg7AIwDSAMiALoC%2BQA) | 1 | 3 | $0.10 | $0.30 | Digi-Key |
| R12 | Resistor, 10 kΩ, 1 %, 1/8 W, 0805 | Yageo | [RC0805FR-0710KL](https://www.digikey.com/en/products/detail/yageo/RC0805FR-0710KL/727535?s=N4IgTCBcDaIEoGEAMAOJBWAYnAtEg7AIxIDSAMiALoC%2BQA) | 1 | 3 | $0.10 | $0.30 | Digi-Key |
| C1 | Capacitor, 0.33 µF, 50 V, X7R, 0805 | Samsung Electro-Mechanics | [CL21B334KBFNNNE](https://www.digikey.com/en/products/detail/samsung-electro-mechanics/CL21B334KBFNNNE/3886781?s=N4IgTCBcDaIMIBkwEYBCBmdAWA0qgYgHLECiIAugL5A) | 1 | 3 | $0.11 | $0.33 | Digi-Key |
| C2, C3, C4, C5 | Capacitor, 0.1 µF, 50 V, X7R, 0805 | Samsung Electro-Mechanics | [CL21B104KBCNNNC](https://www.digikey.com/en/products/detail/samsung-electro-mechanics/CL21B104KBCNNNC/3886661?s=N4IgTCBcDaIMIBkwEYBCyAMAWA0quAckXCALoC%2BQA) | 4 | 8 | $0.10 | $0.80 | Digi-Key |
| C6, C7 | Capacitor, 1 µF, 50 V, X7R, 0805 | KYOCERA AVX | [08055C105KAT2A](https://www.digikey.com/en/products/detail/kyocera-avx/08055C105KAT2A/3081236) | 2 | 5 | $0.78 | $3.90 | Digi-Key |
| TP2 | Test point, miniature, black, through-hole (Keystone 5001) | Keystone Electronics | [5001](https://www.digikey.com/en/products/detail/keystone-electronics/5001/255327?s=N4IgTCBcDaINIFMCeBnALgewHYIAQFYAGQgRhAF0BfIA) | 1 | 3 | $0.27 | $0.81 | Digi-Key |
| TP1,TP3-10 | Test point, miniature, red, through-hole (Keystone 5000) | Keystone Electronics | [5000](https://www.digikey.com/en/products/detail/keystone-electronics/5000/255326?s=N4IgTCBcDaINIFMCeBnALgewHYIAQFYAGYkAXQF8g) | 9 | 12 | $0.26 | $3.16 | Digi-Key |
| U1 | PIC18F57Q43 Curiosity Nano development board | Microchip | EV50E86A | 1 | 0 | - | - | Class kit |
| Off-board (J1) | AC/DC wall adapter, 9 V 1.2 A, 5.5 x 2.1 mm plug | CUI Devices | SWI12-9-N-P5 | 1 | 0 | - | - | Already owned |

## Cost summary

| | Cost |
|---|---:|
| Parts used to build one board | $22.06 |
| Full Digi-Key order with spares and breadboard parts | $52.51 |

Prices are qty-1 Digi-Key prices checked on October 30, 2026.

## Datasheets

- [SHT3x-ARP humidity sensor](Datasheet_SHT3x_ARP.pdf)
- [MCP6001/MCP6002 op amp](MCP6001-1R-1U-2-4-1-MHz-Low-Power-Op-Amp-DS20001733L.pdf)
- [L78 voltage regulator](DS_l78.pdf)
- [PIC18F57Q43 Curiosity Nano user guide](PIC18F57Q43-Curiosity-Nano-HW-UserGuide-DS40002186B.pdf)
- [3M 2500 series IDC header](ts0770.pdf)
- [Sullins female headers](Female_Headers.100_DS.pdf)
- [Littelfuse 111 series fuse clip](Littelfuse-Fuse-Clip-111-Datasheet-pdf.pdf)

## Downloads

- [BOM spreadsheet (Excel)](ELSAADY_FINAL_BOM304.xlsx)
- [Digi-Key purchase request (Excel)](EGR304_Purchase_Request_DigiKey_Elsaady.xlsx)
