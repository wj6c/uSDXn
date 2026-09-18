# uSDXn V1 Technical Notes

## Purpose

This document contains technical information, design decisions, component notes, and implementation details related to the uSDXn V1 hardware.

The purpose of this document is to complement the schematics and general hardware documentation.

Some values and implementation details may be updated as testing continues.

---

# 1. General Architecture

The uSDXn V1 is a 40-meter QRP SDR transceiver based on the uSDX concept.

The hardware is organized into two primary sections:

- Analog Core
- Controller

The Analog Core contains the RF and analog circuitry.

The Controller contains the microcontroller, display, encoder, buttons, and control interfaces.

This separation is intended to make the design easier to understand, test, modify, and expand.

---

# 2. Controller

The V1 Controller is based on the ATmega328P / Arduino Nano architecture.

The Controller provides:

- Frequency control
- Display control
- User interface
- PTT control
- CW input
- Control of the Si5351
- Communication with the Analog Core

The first V1 release uses an Arduino Nano style controller arrangement.

Future versions may experiment with alternative controllers while maintaining the modular concept.

---

# 3. Frequency Generation

The uSDXn V1 uses the Si5351 frequency synthesizer.

The Si5351 provides the clock signals required by the transceiver architecture.

The Controller communicates with the Si5351 using the appropriate digital control interface.

The Si5351 reference oscillator configuration must match the hardware and firmware configuration.

Common Si5351 modules may use different reference crystal frequencies, such as 25 MHz or 27 MHz.

The actual reference frequency used by a particular V1 build must be verified before configuring the firmware.

---

# 4. 40-Meter Operation

The initial uSDXn V1 design is intended for the 40-meter amateur radio band.

The target operating range is approximately:

7.0 MHz to 7.3 MHz

The RF filter and transmitter output network are designed around this band.

The exact operating range and frequency configuration depend on the firmware and hardware implementation.

---

# 5. RF Power Amplifier

The V1 RF power amplifier uses BS170 MOSFET devices.

The RF power stage contains multiple BS170 devices operating as the final RF amplifier.

The PCB provides individual transistor positions to allow builders to install the devices directly.

The design also allows experimentation with suitable socket arrangements where practical.

Direct soldering is generally preferred for RF experimentation because additional socket connections can introduce unwanted parasitic effects.

However, the final construction method is left to the builder.

---

# 6. RF Output Network

The RF output network is designed for 40-meter operation.

The current V1 design uses the following initial component values:

- LX2: 13 turns on T37-2
- C29: 820 pF
- C30: 300 pF
- C28: 1 nF
- LX1: 10 turns on T37-2
- C26: 300 pF
- C27: 1 nF

These values are based on the uSDX serial-resonance 40-meter filter approach.

The component values are considered initial values for the uSDXn V1 design and must be experimentally verified.

Verification should include:

- Resonant behavior
- Insertion loss
- RF output level
- Harmonic suppression
- Behavior into a 50-ohm load

NanoVNA, spectrum analyzer, oscilloscope, and suitable RF test equipment may be used for verification.

---

# 7. RF Filter Note

The RF output network should not be considered fully validated solely from calculated component values.

Inductor construction, component tolerances, PCB layout, transistor characteristics, and RF loading can affect the final response.

For this reason, the final RF filter should be measured on the assembled hardware.

Measured results should be documented for future revisions.

---

# 8. Power Supply

The V1 power supply provides regulated voltages for the radio circuitry.

The main power path includes:

- DC input
- Reverse-polarity protection
- Input filtering
- 8 V regulator
- 5 V regulator
- Additional filtering and decoupling

The current V1 design uses:

- C19: 470 uF / 35 V
- C20: 100 nF
- U7: L7808
- C18: 47 uF / 16 V
- C21: 100 nF
- U8: L7805
- C22: 47 uF / 16 V
- C24: 100 nF
- L1: BL02RN2R1M2
- C23: 47 uF / 16 V
- C25: 100 nF

Equivalent capacitor values may be used when electrically appropriate.

The replacement capacitor should have:

- Equal or greater capacitance where applicable
- Suitable voltage rating
- Suitable type for its circuit position

The power supply should be tested before connecting the complete radio.

---

# 9. Audio Amplifier

The V1 audio amplifier uses an LM386.

The current design includes:

- C3: 22 uF input coupling
- C4: 10 uF gain bypass
- C37: 4.7 uF optional bypass
- C5: 4.7 uF output coupling
- C6: 50 uF with R2 = 10 ohm Zobel network
- R26: 47 ohm output series resistor
- R1: 0 ohm

The amplifier configuration provides high LM386 gain.

The design does not use a physical volume potentiometer.

Volume control is intended to be handled through the digital control system and firmware.

Audio performance, gain, noise, and frequency response should be evaluated during V1 testing.

---

# 10. Audio Frequency Response

The audio section should provide an appropriate frequency response for amateur radio SSB operation.

The practical audio bandwidth should be evaluated during testing rather than assumed solely from component calculations.

Coupling capacitors and input/output impedances influence the low-frequency response.

The final values may be adjusted if testing indicates that changes are beneficial.

---

# 11. Front-Panel Audio Connectors

The V1 uses a K1-style dual-connector arrangement with:

- 3.5 mm connector
- 2.5 mm connector

The connectors are intended to provide microphone, PTT, speaker, and related accessory functions.

The 3.5 mm connector uses the following conceptual arrangement:

- Tip: +5 V
- Ring: Microphone +
- Sleeve: Microphone - / PTT / RX data

The PTT line is not intended to be permanently connected to ground at the connector.

PTT operation is achieved by pulling the PTT line to ground through the appropriate switch or external accessory.

The 2.5 mm connector provides the corresponding speaker and data connections.

The exact physical pin numbering must be verified against the connector datasheet and the selected PCB footprint before final PCB release.

---

# 12. External Speaker

The V1 uses a switched 2.5 mm connector arrangement for the external speaker connection.

The design provides a switched connection so that inserting an external speaker plug can disconnect the internal speaker.

The selected connector is:

HOOYA PJ-208B

LCSC: C2939152

The exact physical pin assignment must be verified against the manufacturer's mechanical and electrical documentation before final production.

---

# 13. CW Input

The V1 includes a basic CW input.

The current design uses a simple switch connected to the Controller.

The Controller can detect the switch state and use it as a CW input.

The initial V1 hardware does not attempt to implement a complete external dual-paddle keyer system.

Future versions may provide a dedicated three-terminal keyer interface using:

- DIT
- GND
- DAH

---

# 14. PCB Construction

The first official V1 hardware release is intended primarily for through-hole construction.

The purpose is to make the hardware accessible to builders who want to assemble and experiment with the radio themselves.

Surface-mount versions may be developed later.

The first release is therefore intentionally focused on accessibility rather than maximum component density.

---

# 15. Analog and Controller Separation

The modular architecture allows the Analog Core and Controller to be developed as separate functional sections.

The Analog Core can therefore be studied independently from the user-interface hardware.

The Controller can also be modified or replaced in future experimental versions.

This approach is intended to make the uSDXn platform useful for hardware experimentation beyond the initial V1 configuration.

---

# 16. Separate and Combined PCB Configurations

The uSDXn V1 development includes two related PCB concepts.

### Separate Configuration

The Analog Core and Controller are implemented as separate boards.

This configuration is useful for experimentation, testing, and modular development.

### Combined Configuration

The Analog Core and Controller can also be implemented together on a combined PCB.

The combined configuration provides a more compact complete transceiver while maintaining the same basic functional architecture.

Both configurations are part of the V1 development and release strategy.

---

# 17. Testing Equipment

The following equipment may be useful when testing and developing the uSDXn V1:

- Digital multimeter
- Oscilloscope
- NanoVNA
- Spectrum analyzer
- RF signal generator
- 50-ohm dummy load
- RF power measurement equipment

The exact test equipment required depends on the stage of development.

RF testing should be performed progressively and at appropriate power levels.

---

# 18. RF Testing

Initial transmitter testing should be performed into a suitable 50-ohm dummy load.

Do not use an antenna as the first RF load during transmitter testing.

Important measurements include:

- Supply current
- RF output power
- RF waveform
- Filter response
- Harmonic content
- Transmitter stability

The RF output filter should be verified before normal antenna operation.

---

# 19. Component Substitution

Component substitutions may be possible when the electrical characteristics remain appropriate.

When replacing a component, consider:

- Voltage rating
- Current rating
- Capacitance
- Resistance
- Inductance
- Frequency response
- Package type
- RF characteristics
- Physical dimensions

RF components require additional care because apparently equivalent components may behave differently at HF frequencies.

---

# 20. Design Verification

The uSDXn V1 should be considered an experimental open-hardware design until the complete hardware verification process has been completed.

Important areas for verification include:

- Power supply voltages
- Controller operation
- Frequency generation
- Receiver operation
- Audio performance
- Transmitter operation
- RF output filter
- Harmonic suppression
- Connector functionality
- Mechanical clearances
- PCB assembly

Measured results should be recorded whenever possible.

---

# 21. Future Development

The modular architecture provides a foundation for future experiments.

Possible future developments include:

- Alternative controllers
- Alternative displays
- Surface-mount implementation
- Additional amateur bands
- USB audio interface
- Digital-mode interface
- Alternative RF stages
- Additional experimental modules

These items are not part of the initial V1 specification unless explicitly included in the V1 release documentation.

---

# 22. Documentation Status

This document describes the current technical direction of uSDXn V1.

Values and implementation details may be revised as measurements and hardware testing continue.

When a change is made to the hardware, the corresponding documentation should be updated so that the repository remains synchronized with the current design.

---

# 23. Open Hardware License

The uSDXn V1 hardware is released under the CERN Open Hardware Licence Version 2 - Permissive (CERN-OHL-P-2.0).

The license allows the hardware design to be studied, copied, modified, manufactured, and distributed according to the terms of the license.

The applicable license and attribution notices must be retained with redistributed versions of the design.

---

**uSDXn V1**

Designed by Juan Carlos Berberena Gonzalez — WJ6C

QRP Sponsoring Organization, Inc. (QSO) — 501(c)(3)

CERN-OHL-P-2.0
