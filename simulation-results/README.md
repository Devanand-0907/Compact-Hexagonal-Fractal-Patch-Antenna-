# RF Simulation & Measurement Results Summary

This directory compiles the simulated data points extracted from the **ANSYS HFSS** solver and compares them to the vector network measurements of the physical prototype.

---

## 1. Comparative Results Table (at 2.4 GHz Center Frequency)

Below is a comparison of key RF performance metrics at the target $2.4\text{ GHz}$ resonance frequency:

| Performance Parameter | ANSYS HFSS Simulated Value | VNA Fabricated Measurement | Specification Requirement |
| :--- | :---: | :---: | :---: |
| **Resonant Frequency ($f_r$)** | $2.40\text{ GHz}$ | $2.42\text{ GHz}$ | $2.40\text{ GHz} \pm 50\text{ MHz}$ |
| **Return Loss ($S_{11}$)** | $-26.80\text{ dB}$ | $-21.40\text{ dB}$ | $\le -10\text{ dB}$ |
| **Voltage Standing Wave Ratio (VSWR)** | $1.096$ | $1.186$ | $\le 2.0$ |
| **Peak Gain (Directivity)** | $3.85\text{ dBi}$ | $3.52\text{ dBi}$ | $\ge 3.0\text{ dBi}$ |
| **Reflection Coefficient ($\Gamma$)** | $0.0457$ | $0.0851$ | $\le 0.316$ |
| **Power Transmission Efficiency**| $99.79\%$ | $99.27\%$ | $\ge 90.0\%$ |
| **Impedance Bandwidth ($S_{11} \le -10\text{ dB}$)** | $120\text{ MHz}$ | $145\text{ MHz}$ | $\ge 80\text{ MHz}$ |

---

## 2. Analysis & Discrepancy Discussion
The physical prototype exhibits a minor upward shift of $20\text{ MHz}$ in its resonant frequency ($2.42\text{ GHz}$ instead of $2.40\text{ GHz}$), accompanied by a slight decrease in return loss depth ($-21.40\text{ dB}$ compared to $-26.80\text{ dB}$). 

This deviation is common in RF design and is attributed to:
1.  **FR-4 Substrate Tolerance:** The dielectric constant of commercial FR-4 substrates can vary between $4.2$ and $4.6$, shifting the resonant frequency.
2.  **Fabrication Tolerance:** Chemical over-etching at the patch boundary or slot borders reduces the copper surface area, lowering the fringing capacitance and increasing the resonance frequency.
3.  **SMA Solder Parasitics:** The solder fillet between the SMA connector pin and the microstrip feed line introduces a capacitive shunt parasitic, slightly detuning the matching network.
