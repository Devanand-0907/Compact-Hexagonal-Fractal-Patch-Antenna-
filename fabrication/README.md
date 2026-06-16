# Hardware Fabrication and VNA Testing Guide

This folder outlines the steps to fabricate the **Compact Hexagonal Fractal Patch Antenna** on an FR-4 PCB board and verify it using standard RF test equipment.

---

## 1. PCB Prototyping Flow

The physical prototype is constructed using standard double-sided copper-clad PCB fabrication:

```
  +-----------------------------------------------------------+
  |                   1. Gerber Export                        |
  |     (Export top copper, bottom copper, and outline files) |
  +------------------------------+----------------------------+
                                 |
                                 v
  +------------------------------+----------------------------+
  |                 2. Board Lamination & UV                  |
  |    (Apply dry-film photoresist, expose layout under UV)   |
  +------------------------------+----------------------------+
                                 |
                                 v
  +------------------------------+----------------------------+
  |                 3. Ferric Chloride Etching                |
  | (Submerge in FeCl3 solution to etch away unwanted copper)  |
  +------------------------------+----------------------------+
                                 |
                                 v
  +------------------------------+----------------------------+
  |                   4. Drill & Edge Launch                  |
  |       (Drill substrate boundaries and deburr edges)       |
  +------------------------------+----------------------------+
                                 |
                                 v
  +------------------------------+----------------------------+
  |                5. SMA Connector Soldering                 |
  |   (Solder the 50 Ohm SMA pin to feedline, shield to ground)|
  +-----------------------------------------------------------+
```

---

## 2. RF Testing & Measurement Protocol

Once the prototype is soldered, the return loss ($S_{11}$) and impedance matching are verified:

### 2.1 Vector Network Analyzer (VNA) Calibration
Before connecting the antenna:
1.  Turn on the VNA (e.g., Keysight/Rohde & Schwarz) and allow it to reach thermal stability.
2.  Perform a **1-Port Calibration** at the end of the coaxial coaxial test cable using the **SOL** standard kit:
    *   **Short:** Connect the short standard and sweep.
    *   **Open:** Connect the open standard and sweep.
    *   **Load:** Connect the $50\ \Omega$ load standard and sweep.
3.  Store the calibration. This shifts the calibration plane directly to the SMA connector interface, removing the electrical delay and loss of the testing cables.

### 2.2 Measurement
1.  Connect the fabricated antenna SMA connector to VNA Port 1.
2.  Set the VNA sweep range from $1.0\text{ GHz}$ to $3.0\text{ GHz}$.
3.  Display the $S_{11}$ return loss trace in dB format.
4.  Capture the resonant dips (they should align close to $2.4\text{ GHz}$).
5.  Display the VSWR trace and verify that at resonance, VSWR $\le 2.0$.
