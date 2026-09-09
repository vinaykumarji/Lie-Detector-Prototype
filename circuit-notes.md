# Hardware / Circuit Notes

## Prototype components

- NE555 timer IC
- 1 kΩ resistor
- 5 kΩ + 6.8 kΩ resistance network
- 10 nF capacitor
- 100 nF capacitor
- 5 V supply
- Breadboard
- Jumper wires
- Skin-resistance/GSR sensing electrodes

## Prototype observation

The breadboard prototype demonstrates that changing the resistance in the timing network changes the NE555 output frequency.

For a standard astable configuration:

\[
f \approx \frac{1.44}{(R_A + 2R_B)C}
\]

The exact values should be verified against the actual wiring and component tolerances.

## Important design note

For a human-connected sensor, do not place a person directly into an unprotected NE555 timing node.

A better architecture is:

```text
Electrodes
   ↓
Safe low-current GSR/EDA sensing circuit
   ↓
Signal conditioning / resistance-to-voltage conversion
   ↓
NE555 timing control or oscillator stage
   ↓
Frequency output
   ↓
Microcontroller frequency measurement
```

This makes the sensing stage easier to calibrate and safer to characterize.

## Power

Use a low-voltage battery-powered source for human-connected experiments. Never use mains voltage on the sensing electrodes.
