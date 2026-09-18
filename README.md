# uSDXn V1

A simple, buildable, open-source QRP SDR transceiver for 40 meters.

> The goal is not to create the most advanced uSDX.
> The goal is to create one that you can actually build, understand, and experiment with.

## About uSDXn

uSDXn is an experimental QRP SDR transceiver project based on the uSDX concept, with a focus on simplicity, accessibility, experimentation, and home construction.

uSDXn V1 is an independent hardware development based on the uSDX concept and is designed as an open platform for builders, experimenters, and amateur radio operators.

The project emphasizes practical construction, modularity, learning, testing, and community collaboration.

## Relationship to uSDX

uSDXn is based on the uSDX concept and builds upon the work of Guido PE1NNZ and contributors to the original uSDX project.

The original uSDX project and its software remain credited to their respective authors and contributors.

uSDXn V1 is an independent hardware development and is not the original uSDX hardware design.

## uSDXn V1 Hardware

The first official uSDXn hardware release is designed for the 40-meter amateur radio band.

The V1 hardware includes:

- ATmega328P / Arduino Nano controller platform
- Si5351 frequency synthesizer
- 40-meter RF circuitry
- Analog Core radio architecture
- BS170 MOSFET transmitter stage
- LM386 audio amplifier
- Standard 1602A LCD
- Mechanical rotary encoder
- Push-button controls
- Through-hole components for practical community construction

The first V1 release is designed primarily for learning, experimentation, testing, and home construction.

Future versions may introduce additional hardware options, including more SMT-oriented designs and other controller platforms.

## Modular Architecture

uSDXn separates the radio into functional hardware sections.

### Controller

The Controller provides the user interface and control functions.

It may include:

- Microcontroller
- Display
- Rotary encoder
- Push buttons
- PTT control
- CW control
- Controller interface

The V1 controller platform is based on the ATmega328P / Arduino Nano.

### Analog Core

The Analog Core contains the main radio circuitry.

It includes:

- RF receive circuitry
- RF transmit circuitry
- Mixer and frequency-generation circuitry
- Audio circuitry
- Power amplifier
- RF filtering
- Associated analog functions

The Controller and Analog Core communicate through defined interfaces, allowing future controller and user-interface experiments without requiring a complete redesign of the radio.

## Hardware License

The uSDXn V1 hardware design is licensed under:

**CERN Open Hardware Licence Version 2 — Permissive (CERN-OHL-P-2.0)**

You are free to use, study, copy, modify, manufacture, and distribute products based on the covered hardware design, subject to the terms and conditions of the CERN-OHL-P-2.0 license.

Please retain the applicable copyright and license notices and identify modifications where required by the license.

See the `LICENSE` file in this repository for the complete license text.

## Repository Structure

```text
uSDXn/
├── BOM/
├── Documentation/
├── Firmware/
├── Hardware/
├── Manufacturing/
├── uSDX Community/
├── LICENSE
└── README.md
