# uSDXn V1 Testing Procedure

## Purpose

This document provides a general testing procedure for the uSDXn V1 hardware.

The purpose is to verify the hardware progressively, identify problems before they can damage other circuits, and provide a repeatable method for testing the completed radio.

The recommended approach is to test each functional section before operating the complete transceiver.

---

# 1. General Safety

Before applying power:

- Inspect the PCB carefully.
- Check for solder bridges.
- Check component orientation.
- Check polarized components.
- Check transistor orientation.
- Check connector orientation.
- Verify the power input polarity.
- Verify that power and ground are not shorted.

Use a current-limited laboratory power supply whenever possible.

During initial testing, do not connect an antenna to the transmitter.

Use a suitable 50-ohm dummy load for initial RF transmission tests.

---

# 2. Required Test Equipment

The following equipment is recommended where available:

- Digital multimeter
- Current-limited DC power supply
- Oscilloscope
- NanoVNA
- RF signal generator
- Spectrum analyzer
- 50-ohm dummy load
- RF power measurement equipment

Not every test requires all of the equipment listed above.

The equipment should be appropriate for the frequency and power level being tested.

---

# 3. Visual Inspection

Before applying power, inspect the entire PCB.

Check:

- Solder joints
- Solder bridges
- Component placement
- Component orientation
- Connector installation
- Transistor installation
- Integrated circuit orientation
- Electrolytic capacitor polarity
- Diode polarity
- PCB damage
- Mechanical clearance

Compare the assembled PCB with the schematic and PCB layout.

Do not proceed until obvious assembly errors have been corrected.

---

# 4. Resistance and Continuity Checks

Before connecting the power supply, use a multimeter to check the main power input.

Verify that there is no direct short circuit between:

- Positive supply
- Ground

Check the resistance between the main supply and ground.

A low resistance reading should be investigated before power is applied.

Also check important power and ground connections throughout the board.

---

# 5. Power Supply Test

The power supply should be tested before the complete radio is powered.

Connect the board to a current-limited power supply.

Initially use a conservative current limit.

Apply power while monitoring:

- Supply voltage
- Supply current
- Regulator temperature

Verify the regulated voltage rails.

The V1 power supply includes:

- Main DC input
- 8 V regulation
- 5 V regulation
- Filtering and decoupling

Confirm that the measured voltages are appropriate before continuing.

If excessive current is observed, disconnect power and investigate the cause.

---

# 6. Controller Test

After the power supply has been verified, test the Controller.

Verify:

- ATmega328P operation
- Controller power
- Display power
- LCD operation
- Rotary encoder operation
- Push buttons
- PTT input
- CW input
- Communication with the Analog Core

The Controller should be tested independently as far as practical.

---

# 7. Display Test

Verify that the 1602A LCD powers correctly.

Check:

- Display illumination
- Display contrast
- Character operation
- Communication with the Controller

If the display does not operate correctly, verify:

- Supply voltage
- Ground
- Wiring
- Connector orientation
- LCD address or configuration where applicable
- Firmware configuration

---

# 8. Rotary Encoder Test

Verify the rotary encoder before proceeding to RF testing.

Turn the encoder slowly in both directions.

Confirm that the Controller detects:

- Clockwise rotation
- Counter-clockwise rotation

If the encoder includes a push switch, verify the switch operation separately.

---

# 9. Push Button Test

Verify each push button connected to the Controller.

Confirm that each button produces the expected electrical state.

The exact function of each button depends on the firmware configuration.

---

# 10. PTT Test

Test the PTT input before applying RF power.

Verify that the PTT line changes state correctly when the PTT switch or external microphone PTT is activated.

Confirm that the Controller detects the transition between receive and transmit states.

The PTT line should be tested independently from the RF power stage.

---

# 11. CW Input Test

Verify the basic CW input.

Confirm that pressing the CW switch produces the expected Controller input state.

The V1 hardware provides a basic CW input for experimentation.

More advanced external keyer arrangements may be implemented in future versions.

---

# 12. Si5351 Test

Verify communication between the Controller and the Si5351.

Confirm:

- Si5351 power
- I2C communication
- Reference oscillator operation
- Clock output

The reference oscillator frequency must match the configuration used by the hardware and firmware.

If the Si5351 module uses a different reference crystal frequency, the firmware configuration must be adjusted accordingly.

---

# 13. Frequency Verification

Use appropriate test equipment to verify the generated frequency.

A frequency counter, oscilloscope, spectrum analyzer, or other suitable instrument may be used.

Verify the frequency at the appropriate test point before connecting the transmitter to an antenna.

Record measured frequencies for future reference.

---

# 14. Receiver Test

After the frequency generation has been verified, test the receiver.

Verify:

- Frequency tuning
- Receiver response
- Audio output
- Audio amplifier operation
- Frequency stability

A suitable RF signal source may be used for controlled receiver testing.

Start with a low-level RF signal.

Avoid applying excessive RF levels to the receiver input.

---

# 15. Audio Amplifier Test

Verify the LM386 audio amplifier.

Check:

- Supply voltage
- Audio input
- Audio output
- Speaker operation
- External speaker output

Listen for:

- Excessive noise
- Oscillation
- Distortion
- Clipping
- Unexpected audio level

The audio amplifier should be evaluated at different volume settings.

Record any abnormal behavior for later investigation.

---

# 16. Transmitter Control Test

Before applying RF power, verify the transmitter control signals.

Confirm:

- PTT operation
- Transmit state
- Si5351 transmit signal
- Controller response
- RF amplifier control

Do not connect an antenna during this stage.

---

# 17. RF Power Amplifier Test

The RF power amplifier should initially be tested at low power.

Verify:

- Supply voltage
- Bias or drive conditions
- RF signal
- Device temperature
- Supply current

Monitor the current carefully.

Unexpectedly high current may indicate:

- Incorrect transistor orientation
- Soldering problems
- Incorrect bias
- RF oscillation
- Incorrect component values
- Output loading problems

Disconnect power immediately if abnormal heating or excessive current is observed.

---

# 18. RF Filter Test

The RF output filter should be verified before normal transmitter operation.

The initial V1 design uses a 40-meter RF filter.

The filter should be evaluated for:

- Passband behavior
- Insertion loss
- Resonance
- Harmonic attenuation

A NanoVNA or suitable RF measurement equipment may be used.

The measured response should be recorded.

---

# 19. Dummy Load Test

The first complete transmitter test should be performed into a suitable 50-ohm dummy load.

Do not use an antenna for the initial transmitter tests.

Verify:

- RF output
- Supply current
- Transmitter stability
- Output waveform
- Filter performance
- Harmonic content

Increase transmitter power gradually while monitoring the system.

---

# 20. Spectrum Analysis

Where a spectrum analyzer is available, inspect the RF output.

Check:

- Fundamental frequency
- Harmonic levels
- Spurious signals
- Transmitter stability

The RF output should be measured after the final RF filter and before connection to an antenna.

Record important measurements for future reference.

---

# 21. Antenna Test

Only after the transmitter has been verified into a suitable dummy load should an antenna system be connected.

Verify that:

- The antenna system is appropriate for the operating band.
- The feed line and connectors are suitable.
- The transmitter is operating normally.
- The RF output is stable.

Monitor transmitter current and RF behavior during the first antenna tests.

---

# 22. Mechanical Verification

Before considering the V1 assembly complete, verify the mechanical installation.

Check:

- Front-panel connectors
- 3.5 mm connector position
- 2.5 mm connector position
- CW switch clearance
- PCB mounting
- Connector access
- Cable clearance
- External module clearance

Particular attention should be given to the front-panel connector spacing and the area around the CW input.

---

# 23. Final Functional Test

After completing the individual tests, perform a complete functional test.

Verify:

- Power supply
- Controller
- Display
- Encoder
- Buttons
- PTT
- CW input
- Frequency generation
- Receiver
- Audio
- Transmitter
- RF filter
- Antenna interface

Record the final test results.

---

# 24. Test Results

Builders are encouraged to record their measurements.

Useful information includes:

- Supply voltage
- Supply current
- RF output power
- Operating frequency
- Filter response
- Harmonic levels
- Audio observations
- Temperature observations
- Problems encountered
- Modifications made

Test results can be useful for future hardware revisions.

---

# 25. Troubleshooting Approach

When a test fails, return to the last known working stage.

Do not change several circuits at the same time.

A recommended troubleshooting approach is:

1. Stop and disconnect power.
2. Identify the last successful test.
3. Review the schematic.
4. Inspect the PCB.
5. Check supply voltages.
6. Check continuity.
7. Check component orientation.
8. Check component values.
9. Make one change at a time.
10. Repeat the test.

Record the result of each change.

---

# 26. Verification Status

The uSDXn V1 hardware is an experimental open-hardware project.

Some measurements and performance characteristics are still subject to verification.

In particular, RF filter performance, transmitter behavior, audio performance, and complete system operation should be confirmed on assembled hardware.

The testing procedure will be expanded as additional measurements become available.

---

# 27. Documentation of Results

When useful measurements are completed, the results should be added to the project documentation.

Future revisions of this document may include:

- Measured RF filter response
- Measured transmitter output
- Harmonic measurements
- Receiver sensitivity measurements
- Audio measurements
- Supply current measurements
- Thermal observations
- Known issues
- Corrective actions

This allows the uSDXn community to benefit from measurements made by different builders.

---

**uSDXn V1**

Designed by Juan Carlos Berberena Gonzalez — WJ6C

QRP Sponsoring Organization, Inc. (QSO) — 501(c)(3)

CERN-OHL-P-2.0
