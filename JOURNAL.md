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


## 2026.01.24 1.6h
### Took apart my current mouse and more schematics

Continued with schematics. Added switches and the recommended MCU wiring. Had to shift the symbols around to make some room for the MCU.

Made an explorative surgery on my current mouse and based on that made some decisions:

1. I will use [11mm version](https://www.aliexpress.com/item/1005007462295852.html) of the rotary encoder, the 9mm would probably be a little too short. Also I found a cheaper offer.

2. I will use [Kailh Silent Micro Switch MI627301D07](https://www.aliexpress.com/item/1005010180023487.html) instead of D2Fs. My current mouse has these and they make close to zero noise, which I really like.


Also realised that the last two schematics snapshots had the wrong date.
![2026.01.24 schematic](<Images/2026.01.24 schematic.svg>)


## 2026.01.25 4.5h
### Finished schematics

Decided to switch to [LT1761ES5-2](https://www.aliexpress.com/item/1005009716344832.html) for the optical sensor voltage regulator. It provides 2V instead of 1.8V, which should mean a more stable performance.

Will be using [this 1000mAh 3.7V Li-Po battery](https://www.aliexpress.com/item/32988574923.html).


Modified the power path:
1. [The ALPSALPINE SSSS223600 switch](https://www.lcsc.com/product-detail/C255513.html) allows to switch off the entire mouse, when it runs on battery power and also controls wireless communication mode.
2. [The 1N5817 diode](https://www.lcsc.com/product-detail/C727114.html) provides bypass power from USB at all times regardless of the switch's state.

Found some componenets:
- [Antenna inductor](https://www.lcsc.com/product-detail/C40353066.html)
- [32MHz crystal](https://www.lcsc.com/product-detail/C37635331.html)
- [Female USB-C](https://www.lcsc.com/product-detail/C7095263.html)


LEDs:
- [Blue - charging](https://www.lcsc.com/product-detail/C108412.html)
- [Green - power good](https://www.lcsc.com/product-detail/C5123492.html)
- [Red - low battery](https://www.lcsc.com/product-detail/C130114.html)

Added battery connector, finished the MCU wiring, made a footprint for Kailh switches and added them to the schematic.

![2026.01.25 schematic](<Images/2026.01.25 schematic.svg>)
![2026.01.25 PCB](<Images/2026.01.25 PCB.svg>)

I hope I'm finally done with the schematics!