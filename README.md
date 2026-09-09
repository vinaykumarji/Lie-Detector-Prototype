# NE555 Lie Detector Prototype

> **Educational electronics prototype:** a resistance-to-frequency experiment using an NE555 timer.

This project explores a simple observation:

**When the resistance in an NE555 timing circuit changes, the output frequency also changes.**

Human skin has electrical resistance/impedance that can vary with factors such as sweating, skin contact, temperature, and emotional arousal. A skin-resistance sensor can therefore be used as an input to an NE555-based oscillator, allowing changes in skin conductance to appear as changes in oscillator frequency.

The prototype is intended for **learning and experimentation**, not as a scientifically validated lie detector.

## Project idea

The basic signal chain is:

```text
Human skin
   │
   ▼
Skin-resistance / GSR sensor
   │
   ▼
Resistance-dependent NE555 oscillator
   │
   ▼
Frequency changes
   │
   ▼
Frequency measurement
   │
   ▼
Baseline comparison
   │
   ▼
Experiment / visualization
```

During an experiment, a baseline can first be recorded while asking neutral questions such as:

- What is your name?
- What is your age?
- What is your favorite color?

Then questions with known or experimental answers can be asked while monitoring the frequency.

The important measurement is **change from the person's own baseline**, rather than one universal frequency threshold.

## Hardware

The first breadboard prototype uses an **NE555 timer IC** as the oscillator.

Components visible in the prototype:

- NE555 timer IC
- 1 kΩ resistor
- 5 kΩ + 6.8 kΩ resistance network
- 10 nF capacitor
- 100 nF capacitor
- 5 V supply
- Breadboard and jumper wires
- Human skin-resistance/GSR sensor for the sensing stage

Prototype photo:

![NE555 breadboard prototype](images/ne555_breadboard_prototype.jpg)

## NE555 frequency principle

For a standard NE555 astable oscillator:

\[
f \approx \frac{1.44}{(R_A + 2R_B)C}
\]

where:

- \(R_A\) is the first timing resistance
- \(R_B\) is the second timing resistance
- \(C\) is the timing capacitor
- \(f\) is the oscillator frequency

Therefore, changing the timing resistance changes the oscillator frequency.

For the actual sensor implementation, the exact formula depends on how the skin sensor is connected to the NE555 timing network. The resistance should be measured/calibrated experimentally rather than assuming that the nominal resistor values shown in the prototype are the final sensing values.

## Experimental method

### 1. Establish a baseline

Attach the sensor consistently and allow the subject to relax.

Record:

- skin resistance/conductance
- NE555 frequency
- time
- question being asked
- subject response

Ask several neutral questions first.

### 2. Ask test questions

Ask questions whose answers are already known to the experimenter.

Record the same measurements.

### 3. Compare against baseline

Instead of using a fixed "lie frequency", calculate the change:

\[
\Delta f = f_{test} - f_{baseline}
\]

A percentage change can also be useful:

\[
\%\Delta f =
\frac{f_{test}-f_{baseline}}{f_{baseline}}\times100
\]

Large changes may indicate physiological arousal, but they **do not prove that a person is lying**.

## Why this works

Human skin is not a fixed resistor.

Skin conductance can change with:

- sweating
- stress/arousal
- temperature
- pressure/contact area
- electrode placement
- movement
- hydration
- individual physiology

A galvanic skin response (GSR/EDA) sensor is normally used to observe changes in skin conductance. In this project, those changes are converted into a frequency change using the NE555 oscillator.

## Important limitation

This project should be called a **lie-detector prototype** only in the context of an educational project. It is **not a reliable lie detector**.

A frequency change can mean that the subject experienced physiological arousal. It cannot uniquely distinguish:

- lying
- nervousness
- fear
- surprise
- excitement
- embarrassment
- physical movement
- temperature/sweat changes

A proper research-grade deception assessment requires controlled experiments, validated instrumentation, signal processing, and statistical analysis.

## Suggested future improvements

- Replace the manual resistance network with a calibrated GSR/EDA sensor front-end.
- Add a microcontroller to measure NE555 frequency automatically.
- Use an interrupt/input-capture method for accurate frequency measurement.
- Send frequency data to a PC or mobile application.
- Plot frequency and skin conductance in real time.
- Add baseline normalization.
- Add moving-average / low-pass filtering.
- Record timestamped question and response events.
- Test multiple subjects and repeated trials.
- Compare neutral and test-question responses statistically.
- Add electrode/contact-quality detection.
- Use isolated, battery-powered sensing for safer human-connected experiments.

## Safety

The prototype should use a **low-voltage, battery-powered supply** when connected to a person.

Do not connect a human subject to mains-powered circuits or unsafe external power supplies.

Use appropriate current limiting and a properly designed sensing front-end. The breadboard shown here is a learning prototype, not a medically certified device.

## Repository structure

```text
NE555-Lie-Detector-Prototype/
├── README.md
├── LICENSE
├── .gitignore
├── docs/
│   ├── methodology.md
│   └── experiment-log-template.md
├── hardware/
│   └── circuit-notes.md
└── images/
    └── ne555_breadboard_prototype.jpg
```

## Status

**Current stage:** NE555 resistance-to-frequency prototype.

The next major stage is automatic frequency measurement and data logging.

## License

MIT License. See `LICENSE`.

## Author

Electronics / signal-processing educational project.
