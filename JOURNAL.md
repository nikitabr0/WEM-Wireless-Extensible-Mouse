# Motivation

About a month ago I started the MAWK (Modular Analog Wireless Keyboard) project, but at one point I realised it was getting too complex for me to even try finishing it with my current skills. So I decided to start WEM (Wireless Extensible Mouse) project with the goal of learning power management, RF circuits and SMD soldering to be able to use barebones MCU chips in my projects.


# What I've done

## 2026.01.17 - 2h
### Working environment, licences, MCU, firmware

Set up local and GitHub repositories.

Chose licences for firmware (MIT Licence) and hardware (CERN Open Hardware Licence Version 2 - Permissive)

Decided to use [nRF52840 QFN73](https://www.aliexpress.com/item/1005005069398861.html) for its good connectivity options and because I am going to use it later MAWK, so I can already gain some experience with it.

For the firmware I chose ZMK. It supports USB, BLE and allows using proprietary 2.GHz radio protocols, which I plan to employ fo the 2.4GHz USB dongle.

## 2026.01.18 - 2h
### Started schematic design

For battery charging I will be using [MCP73871 2CC](https://www.aliexpress.com/item/1005008336731440.html).

For the optical sensor I chose [PAW3395DM-T6QU with a LM19-LSI lens](https://www.aliexpress.com/item/1005009206404384.html)

USB protections: [MDD(Microdiode Semiconductor) SMF5.0A](https://www.lcsc.com/product-detail/C193402.html), [Littelfuse 1206L110THYR](https://www.lcsc.com/product-detail/C126818.html) on VBUS and [Leiditech TPD2EUSB30DRTR](https://www.lcsc.com/product-detail/C3040102.html) on data lines.

So far I've chosen the main componenets and done the USB-C port schematics.

![2026.01.18 schematic](<Images/2026.01.18 schematic.svg>)


## 2026.01.22 - 3h
### Voltage regulators, continuing with schematic

I found the MCP1801 series voltage regulators, which I'll be using to convert battery voltage to 3.3V and 1.8V.

I'll be using [MCP1801T-3302I/OT](https://www.lcsc.com/product-detail/C3040615.html) and [MCP1801T-1802I/OT](https://www.lcsc.com/product-detail/C556903.html).

For the button switches I decided to go with Omron D2Fs, as they're cheap, reliable and while they're not created for mouse buttons, they're widely available.

I implemented the battery charger and voltage regulators in the schematic and spent some time researching antennas. I'll try to fit a F-antenna in the up-left corner for the best RF characteristics.

![2026.01.22 schematic](<Images/2026.01.22 schematic.svg>)

## 2026.01.23 2.5h
### Mouse wheel encoder and schematics

Found [Kailh Mouse Scroll Wheel Encoder 9mm](https://www.aliexpress.com/item/1005001852115432.html), which I will be using. It's quite popular in DIY computer mice.

Added links to components' documentations to `PCB/Docs.md`.

The PAW3395DM-T6QU optical movement sensor needs a resistor to set the current to 50mA, but the datasheet provides resistances only for 2V and 1.9V (I'm using 1.8V). Using linear interpolation gave a resisitor value of 4.4 Ohms. Since the datasheet recommends a 1% tolerance (E96), I'll use a 4.53 Ohm resitor, just to be safe.

Completed optical sensor, mouse wheel encoder and extensions'/MCU flashing connectors. Also decided to use 0 Ohm resistors instead of solder bridge jumpers.

![2026.01.23 schematic](<Images/2026.01.23 schematic.svg>)


TODO: battery and its connectors, button switches.