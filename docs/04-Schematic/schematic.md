# Schematics

![Humidity Sensing Subsystem schematic](KiCAD304_Humidity_SE.png)


- [Schematic PDF](KiCAD304_Humidity_SE.pdf)
- [Kicad project ZIP (includes custom symbol and footprint libraries)](KiCAD304_Humidity_SE.zip)
# Schematics


## Overview

This is the full schematic for my humidity sensing board. I split it into five sections so it's easier to follow: Power Input, Amplified Analog Sensor, Microcontroller, Team Ribbon Connector & UART, and Debug.

## How the Design Works and Meets Our Requirements

### Power Input

Power comes in from a 9 V wall adapter through a PJ-002A barrel jack. Right after the jack there's a 500 mA fast-blow fuse in a 5x20 mm holder, so if something shorts, the fuse blows and can be swapped out instead of damaging the board. My power budget shows the board draws about 60 mA at most from the adapter, so the fuse has around 8 times headroom for normal use while keeping us well under the team's 1.5 A limit (PR 6.1).

The fuse feeds an STMicroelectronics L7805CV, which turns the 9 V into a steady 5 V for the whole board. I used the 0.33 µF input and 0.1 µF output capacitors that its datasheet recommends. The L7805 also has built-in current limiting and thermal shutdown, which helps keep the 5 V rail from ever going above 5.5 V at the sensor or microcontroller (PR 6.2). A green LED on the 5 V rail lights up so I can see that the board has power.

### Amplified Analog Sensor

This is the main job of my board. The Sensirion SHT31-ARP-B puts out an analog voltage between 10 % and 90 % of its supply, which works out to about 0.5 V at 0 %RH and 4.5 V at 100 %RH. It's factory calibrated to ±2 %RH, which beats our ±3 %RH requirement (PR 2.1). The output is also ratiometric, meaning it scales with the supply voltage. Since the sensor and the PIC's ADC both run off the same 5 V rail, any small drift in the regulator cancels out instead of showing up as a humidity error.

The sensor can only drive about 100 µA and 5 nF, so I send its output straight into a Microchip MCP6001 op amp before any filtering. The op amp is set up as a non-inverting amplifier with a gain of 1.1, set by R11 and R12 (1 + 1 kΩ / 10 kΩ). That protects the sensor from being loaded down, and it stretches the signal to roughly 0.55 to 4.95 V so it uses more of the ADC's 0 to 5 V range without hitting the rails. The MCP6001 is rail-to-rail, so it can actually swing that close to 0 V and 5 V.

After the op amp, R3 and C6 form a low-pass filter with a cutoff around 16 Hz. Humidity changes over seconds which cuts out electrical noise without slowing down real readings. The PIC easily gets a fresh value at least every 2 seconds (PR 2.4).


### Microcontroller

The Nano reads the filtered humidity signal on RA0 and the sensor's temperature output on RA1 using its 12-bit ADC, and I'll use the ADC's built-in averaging for a little extra smoothing.

The Nano gets its power from my 5 V rail through the VTG pin, with a 0.1 µF bypass capacitor right next to it. VOFF is tied to ground, which the Curiosity Nano user guide says you have to do when you power the board externally, so its own regulator turns off and doesn't fight mine. Jumper JP9 lets me disconnect the Nano from the board's 5 V if I need to. Any pins I'm not using are marked as no connect and will be set as outputs driven low in my code so nothing is left floating.

### Team Ribbon Connector & UART

My board talks to Zander's hub board through a 2x4 IDC header using the class ribbon cable standard (PR 1.4). The hub sends on pin 1 and listens on pin 2, so my board receives on pin 1 (UART RX) and sends humidity readings on pin 2 (UART TX). Pin 8 is ground, and pins 3 through 7 aren't used.

One thing I had to work around is that our team agreed on 3.3 V UART signals, but my PIC runs at 5 V because the sensor needs it. On the TX side, R4 (1.8 kΩ) and R5 (3.3 kΩ) form a voltage divider that brings my 5 V signal down to about 3.2 V before it reaches the hub. On the RX side, I'll set RC3 to TTL input level so the PIC reads the hub's 3.3 V as a logic high, and R6 (1 kΩ) is in series to protect the pin. Jumpers JP2 and JP3 let me disconnect TX and RX from the ribbon, so I can test my board by itself before plugging into anyone else's (PR 2.5, PR 2.6).

### Debug

I added a few things to make testing easier. There's a yellow LED on RD0 that I'll blink in code so I know the program is running, and a red LED on RD1 that I can use however I need while debugging. There's also a pushbutton on RB0 with a 10 kΩ pull-up (R9) and an RC debounce made from R10 (1 kΩ) and C7 (1 µF), so one press doesn't register as several. There are ten test points on the power rails, the raw, amplified and filtered sensor signal, the temperature output, and both UART lines, and an 8-pin header (J4) brings out spare GPIO pins in case I need to add anything later.

### Component Ratings

Every part has a value and a rating listed. All capacitors are rated at least 25 % above the voltage they'll see. For example, C1 sees up to 12 V, so I used a 25 V part, and the 5 V rail uses 16 V parts. All resistors are 1/8 W with at least 50 % margin. The ones working hardest are the LED resistors, at about 27 mW each.
