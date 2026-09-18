# uSDXn V1 Hardware Overview

## Introduction

The uSDXn V1 is a modular QRP SDR transceiver designed for the 40-meter amateur radio band.

The hardware is organized into two main functional sections:

- Analog Core
- Controller

This separation is one of the main design concepts of uSDXn.

The purpose is to keep the radio circuitry and the digital control circuitry organized as independent functional blocks, making the design easier to understand, build, test, modify, and develop.

---

## Main Hardware Architecture

The uSDXn V1 consists of:

- Analog Core
- Digital Controller
- Power Supply
- RF Transmitter
- RF Receiver
- Audio Amplifier
- Frequency Generation
- User Interface
- External radio connections

The Controller communicates with the Analog Core through defined electrical connections.

This architecture allows future controllers, displays, interfaces, and other experimental modules to be considered without requiring a complete redesign of the Analog Core.

---

# Analog Core

The Analog Core contains the main radio circuitry.

It is responsible for the RF, receive, transmit, frequency conversion, audio, and associated analog functions of the transceiver.

The Analog Core is divided into several functional areas.

## RF Receive Section

The receive section processes the incoming RF signal and converts it into the appropriate signals for the SDR architecture.

The receiver includes the analog RF path, frequency conversion, filtering, and audio processing required by the radio architecture.

The detailed circuit is documented in the Analog Core schematics provided in the Hardware directory.

---

## RF Transmit Section

The transmitter generates the RF output signal and drives the RF power amplifier.

The V1 transmitter uses BS170 devices in the RF power stage.

The transmitter includes:

- RF signal generation
- Driver circuitry
- RF power amplification
- RF filtering
- Antenna interface

The RF output network is designed for the 40-meter band.

The RF filter values are subject to experimental verification during the V1 testing process.

---

## Frequency Generation

The uSDXn V1 uses an Si5351 frequency synthesizer.

The Si5351 provides the clock and RF signals required by the transceiver architecture.

The frequency synthesizer is controlled by the ATmega328P-based Controller.

The exact frequency relationships and configuration are documented in the technical documentation and firmware-related material.

---

## Audio Section

The Analog Core includes the receive audio circuitry and an LM386 audio amplifier.

The LM386 provides the final audio amplification stage for the internal speaker or external audio connection.

The audio section is designed to remain simple and accessible for experimentation.

Audio component values and performance may be refined during testing.

---

# Controller

The Controller is based on the ATmega328P / Arduino Nano architecture.

It provides the digital control and user interface for the transceiver.

The Controller includes:

- ATmega328P microcontroller
- LCD interface
- Rotary encoder
- Push-button controls
- PTT control
- CW input
- Communication with the Analog Core

The Controller is intended to be relatively independent from the RF circuitry.

---

## Display

The V1 uses a standard 1602A LCD.

The display provides the user interface for frequency and other radio information.

The display interface is controlled by the ATmega328P.

Future versions may experiment with different display technologies while retaining the modular concept.

---

## Rotary Encoder

A mechanical rotary encoder is used for frequency control and user interaction.

The encoder provides rotational input to the Controller.

Additional push-button functions may be used for menu navigation and other radio controls.

---

## Push Buttons

The V1 includes simple push-button controls connected to the Controller.

These controls provide additional user input for radio operation.

The exact firmware functions assigned to the buttons may evolve as the uSDXn V1 firmware development progresses.

---

## PTT

The uSDXn V1 provides a PTT input for controlling transmit and receive operation.

The PTT interface is connected to the Controller so that the firmware can control the radio operating state.

The external microphone interface follows a K1-style dual-connector concept using 3.5 mm and 2.5 mm connections.

The exact connector pin assignments are documented in the corresponding schematic.

---

## CW Input

The V1 provides a basic CW input.

The initial design uses a simple switch-based input connected to the Controller.

The hardware leaves room for future experimentation with more advanced CW key or keyer arrangements.

---

# Power Supply

The uSDXn V1 includes an onboard power supply section.

The power supply provides the regulated voltages required by the different sections of the radio.

The V1 power architecture includes:

- DC power input
- Reverse-polarity protection
- Input filtering
- 8 V regulation
- 5 V regulation
- Additional filtering and decoupling

The power supply is documented separately in:

`Hardware/Analog_Core/uSDXn_V1_Power_Supply_Schematic.pdf`

The power supply should be tested independently before connecting power to the complete radio.

---

# External Connections

The V1 provides connections for the main external radio functions.

These include:

- Power
- Antenna
- Microphone
- Speaker / external audio
- PTT
- CW input
- Controller connections

The front-panel audio connections use a dual-connector arrangement consisting of:

- 3.5 mm connector
- 2.5 mm connector

This arrangement is intended to support commonly available microphone and accessory connections while maintaining a compact front-panel layout.

---

# Modular Architecture

One of the main goals of uSDXn is to separate the radio into functional modules.

The V1 architecture provides a clear distinction between:

```text
Controller
     │
     │
     ▼
Analog Core
     │
     ├── Receiver
     ├── Transmitter
     ├── RF Power Amplifier
     ├── RF Filter
     ├── Audio
     └── Antenna Interface
