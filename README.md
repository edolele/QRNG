# QRNG
Quantum Random Number Generator

[circuit diagram](img/circuit.png)

# Motivation
The QRNGv1 was originally a proof of concept for quantum technology applications, specifically in this case for the generation of entropy which has a broad range of uses from generating graphics to encryption keys.

# How It Works
The device uses a polarizing beam splitter to split a laser pulse into two beams with a 50/50 probability of a photon in the beam traveling either path. The photons actually travel as a wave, meaning they both pass through and are reflected by the beam splitter. This creates what's known as the superposition of light where the light remains in both paths able to interfere with itself until it is measured and collapses out of superposition.

The equivalent quantum logic gate would be the Hadamard gate, in QASM code:

```qasm
creg c0[1];
h q[1];
measure q[1] -> c0;
```

# Hardware Requirements
- Arduino Uno (or similar)
- Breadboard
- 2x Photoresistors
- 1x 50/50 Polarizing beam splitter
- 1x Laser Diode

# Software Requirements
- Arduino IDE (for programming the Arduino)

# Firmare
Firmware can be found in the respective design folders labelled according to version. The schematics as well are labelled with the version of firmware which supports them.

# How To Use
Currently the QRNG arduino operates via the Arduino Serial Monitor, you can issue single letter commands to it. We plan to add support for the device with our [Qubit Controller](https://github.com/Spooky-Manufacturing/Qubit-Controller) in the near future.

## Available Commands
- v : Version, returns the current firmware verison
- t : Test command, should return 'Success!' on the monitor
- e : Enables extraneous information
- r : Returns a random bit generated by the RNG
- h : Produces a hadamard operation on the qubit, returning the measured angle of the qubit

