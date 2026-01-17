# Motivation

About a month ago I started the MAWK (Modular Analog Wireless Keyboard) project, but at one point I realised it was getting too complex for me to even try finishing it with my current skills. So I decided to start WEM (Wireless Extensible Mouse) project with the goal of learning power management, RF circuits and SMD soldering to be able to use barebones MCU chips in my projects.


# What I've done

## 2026.01.17 2h
### Working environment, licences, MCU, firmware

Set up local and GitHub repositories.

Chose licences for firmware (MIT Licence) and hardware (CERN Open Hardware Licence Version 2 - Permissive)

Decided to use nRF52840 for its good connectivity options and because I am going to use it later MAWK, so I can already gain some experience with it.

For the firmware I chose ZMK. It supports USB, BLE and allows using proprietary 2.GHz radio protocols, which I plan to employ fo the 2.4GHz USB dongle.