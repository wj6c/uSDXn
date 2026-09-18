# uSDXn V1 Build Guide

## Introduction

The uSDXn V1 is a simple, buildable, open-source QRP SDR transceiver designed for experimentation, learning, and amateur radio development.

The first version is designed for the 40-meter amateur radio band and uses a modular architecture that separates the Analog Core from the Controller.

The goal of uSDXn is not to create the most advanced uSDX design, but to provide a practical platform that builders can assemble, understand, test, modify, and use as a basis for further experimentation.

---

## V1 Hardware

The uSDXn V1 is built around the following main elements:

- ATmega328P / Arduino Nano controller
- Si5351 frequency synthesizer
- Analog Core radio section
- 1602A LCD display
- Rotary encoder
- Push-button controls
- BS170 RF power devices
- LM386 audio amplifier
- Through-hole components wherever practical

The design is divided into two main functional sections:

### Analog Core

The Analog Core contains the radio circuitry, including:

- RF receive and transmit circuitry
- RF power amplifier
- RF filtering
- Audio circuitry
- Power supply
- External radio connections

### Controller

The Controller provides the digital control and user interface.

It includes:

- ATmega328P / Arduino Nano
- LCD interface
- Rotary encoder
- Push-button controls
- PTT control
- CW input
- Interface connections to the Analog Core

The modular architecture allows the Controller and Analog Core to be developed and experimented with independently.

---

## Before Building

Before starting construction, carefully review the available schematics and documentation in this repository.

Verify:

- Component values
- Component orientation
- Transistor orientation
- Diode orientation
- Electrolytic capacitor polarity
- Connector orientation
- Power connections
- Jumper and header positions
- PCB revision

Do not install power until the board has been visually inspected and basic continuity checks have been completed.

---

## Recommended Build Approach

The uSDXn V1 is intended to be built progressively rather than powered and tested as a completely assembled circuit for the first time.

A recommended general sequence is:

1. Review the schematics.
2. Review the PCB layout.
3. Identify all components.
4. Install passive components.
5. Install diodes and other polarized components.
6. Install transistors and semiconductor devices.
7. Install connectors and headers.
8. Install the controller and display connections.
9. Inspect all solder joints.
10. Perform continuity and resistance checks.
11. Test the power supply.
12. Test the Analog Core.
13. Test the Controller.
14. Connect the two sections.
15. Load appropriate firmware.
16. Perform receive testing.
17. Perform low-power transmit testing.
18. Test the RF output and filtering.
19. Connect an appropriate antenna system only after the RF section has been verified.

The exact assembly and testing sequence may be expanded as the V1 hardware is tested and additional information becomes available.

---

## Component Installation

### Resistors

Install resistors according to the schematic and BOM.

Check the resistance value before installation when practical, especially for components used in RF, bias, or amplifier circuits.

### Capacitors

Pay particular attention to polarized electrolytic capacitors.

Verify both capacitance and voltage rating before installation.

Ceramic and other non-polarized capacitors should also be checked against the schematic because capacitor values can be important in RF filtering, coupling, bypassing, and frequency-selective circuits.

### Diodes

Verify diode orientation against the PCB silkscreen and schematic.

### Transistors

Verify transistor type, orientation, and pin configuration before installation.

The RF power amplifier uses BS170 devices. Pay particular attention to their orientation and installation.

### Integrated Circuits

Install ICs only after confirming orientation and pin numbering.

Use appropriate precautions when handling CMOS and other static-sensitive devices.

---

## Controller Installation

The V1 Controller is based on the ATmega328P / Arduino Nano architecture.

Before connecting the Controller to the Analog Core:

- Verify the supply voltage.
- Verify the ground connections.
- Verify the interface connections.
- Check for accidental shorts between power and ground.
- Confirm the display and encoder connections.

The controller firmware is still under development. Existing compatible firmware may be used for experimentation when appropriate, but the hardware configuration should be verified before selecting firmware.

---

## Power-Up Procedure

Do not connect the RF output to an antenna during the initial electrical tests.

Before applying power:

1. Perform a visual inspection.
2. Check for solder bridges.
3. Check the polarity of electrolytic capacitors.
4. Check diode and transistor orientation.
5. Measure resistance between the main supply and ground.
6. Verify the power connector polarity.
7. Use a current-limited power supply when possible.

Apply power carefully and verify the supply rails before proceeding with further testing.

If abnormal current consumption, excessive heating, smoke, or unexpected voltage is observed, disconnect power immediately and investigate the cause.

---

## Receive Testing

Once the power supply and Controller have been verified, the receiver can be tested.

Initial receive testing should verify:

- Controller operation
- Display operation
- Frequency control
- Rotary encoder operation
- Push-button operation
- Audio output
- Receiver operation
- Frequency stability

Further receiver testing procedures will be documented as the V1 hardware testing progresses.

---

## Transmit Testing

Transmit testing should be performed progressively and at low power whenever possible.

Before connecting an antenna:

- Verify the transmitter control signals.
- Verify the RF output path.
- Verify the RF filtering.
- Check for abnormal current consumption.
- Use suitable RF test equipment and a dummy load.

A properly rated dummy load should be used for initial RF transmission tests.

Do not transmit into an open circuit.

NanoVNA, oscilloscope, spectrum analyzer, or other suitable RF test equipment may be used where appropriate.

---

## RF Output and Filter Testing

The V1 RF output network is designed for the 40-meter band.

The RF filter and output network should be experimentally verified before considering the hardware fully validated.

Measurements may include:

- Center frequency
- Insertion loss
- Harmonic suppression
- RF output level
- Transmitter current
- Behavior into a 50-ohm load

The final component values and test results will be documented as the V1 testing process is completed.

---

## Antenna Connection

Connect an antenna only after the transmitter and RF output have been verified with a suitable test load.

The antenna system should present an appropriate load for the radio.

The builder is responsible for ensuring that the antenna, feed line, connectors, and RF environment are suitable for operation.

---

## Troubleshooting

When troubleshooting the uSDXn V1, work systematically from the power supply toward the individual functional sections.

Recommended order:

1. Power supply
2. Controller
3. Display and user controls
4. Clock / frequency generation
5. Receiver
6. Audio amplifier
7. Transmitter
8. RF filter
9. Antenna interface

Do not modify several sections at the same time.

Make one change, perform a measurement, and record the result.

---

## Documentation and Revision

The uSDXn V1 is an experimental open-hardware project.

The design and documentation may continue to evolve as testing and community feedback identify improvements.

Builders are encouraged to document:

- Hardware modifications
- Component substitutions
- Test results
- Problems encountered
- Successful improvements
- Firmware experiments
- RF measurements

Useful observations and improvements may be incorporated into future revisions of the project.

---

## Open Hardware

uSDXn V1 is released as open hardware under the CERN-OHL-P-2.0 license.

Builders are encouraged to study, build, modify, and experiment with the design in accordance with the license.

When modifying the design, clearly document the changes and retain the applicable license and attribution information.

---

## Project Status

This Build Guide provides the general construction and testing approach for uSDXn V1.

Detailed component information, schematics, manufacturing files, testing results, and additional technical information are maintained in the corresponding sections of this repository.

Additional information will be added as the V1 hardware is tested and the project develops.

---

## Community

uSDXn is intended to be a community-oriented open-hardware project.

Builders, experimenters, and developers are encouraged to share their experiences, measurements, modifications, and ideas.

The objective is to make the project useful not only as a radio, but also as a platform for learning and experimentation.

---

**uSDXn V1**

Designed by Juan Carlos Berberena Gonzalez — WJ6C

QRP Sponsoring Organization, Inc. (QSO) — 501(c)(3)

CERN-OHL-P-2.0
