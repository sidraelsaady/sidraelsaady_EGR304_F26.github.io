## Introduction

This datasheet documents the **Humidity Sensing Subsystem** I designed for Team 202's
Environmental Monitoring Device in EGR 304. It walks through the design from block diagram
to component selection, schematic, and power budget, so a reader can understand what the
board does, why each part was chosen, and how it connects to the rest of the team's system.

## Project Summary

Team 202 is building an **Environmental Monitoring Device**: a set of four connected boards
that each measure part of the surrounding environment and report it to a central hub board
with an LCD display. Each teammate designs their own board, and the boards share data over
an 8-wire ribbon cable using the class connector standard.

My board measures **relative humidity**. A Sensirion SHT31-ARP-B analog sensor produces a
voltage proportional to humidity, an MCP6001 op amp amplifies it, an RC low-pass filter
removes noise, and the PIC18F57Q43 Curiosity Nano converts it to a number. The PIC then sends
the humidity reading to Zander Boward's hub board over UART, where it is displayed.

See the full system in our [team report](https://asu-egr304-2026-f-202.github.io/ASU-EGR304-2026-F-202/).

## My Contribution

I am responsible for the humidity sensing subsystem, from sensor selection through the
schematic and PCB. Use the sections below to navigate:

- [Block Diagram](01-Block-Diagram/Block-Diagram/): how power and signals flow through my board
- [Component Selection](02-Component-Selection/Component-Selection/): the options I compared and why I chose each part
- [Bill of Materials](03-BOM/BOM/): parts list for the board
- [Schematic](04-Schematic/schematic/): the full KiCad schematic with PDF and project files
- [Power Budget](05-Power-Budget/Power-Budget/): current draw and regulator/fuse sizing

To review the details listed of the material used to construct the subsection, you can review it in the ["BOM"](https://embedded-systems-design.github.io/EGR304DataSheetTemplate/03-BOM/BOM/) section of the datasheet.


