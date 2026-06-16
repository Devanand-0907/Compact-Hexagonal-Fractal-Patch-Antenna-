# Academic Documentation & Literature Survey

This directory contains research documentation and design specs relating to the **Compact Hexagonal Fractal Patch Antenna**.

---

## 1. Theoretical Foundations
Fractal geometry is characterized by its **self-similarity** and **space-filling** properties. In antenna design, these properties are utilized for:
*   **Miniaturization:** Increasing the effective electrical current path length within a fixed physical boundary.
*   **Multi-band / Wideband Behavior:** The repetition of the geometric structures at different scales (iterations) introduces multiple resonant frequencies.

### Sierpinski Hexagonal Fractals
The Sierpinski fractal applied to a hexagon involves starting with a solid hexagonal boundary (Iteration 0) and systematically etching nested circular or hexagonal slots at scaled coordinates (Iteration 1, Iteration 2). 

For a hexagon of side length $S$, the area decreases by a scale factor, while the perimeter (current path length) scales exponentially:

$$P_n = P_0 \left(\frac{5}{3}\right)^n$$

Where:
*   $P_n$ is the perimeter at iteration $n$.
*   $P_0$ is the initial hexagonal perimeter ($6 \times S$).

---

## 2. Literature Survey Highlights
The design was optimized based on peer-reviewed literature:
1.  **Sierpinski Hexagonal-Shaped Fractals (Benkhadda et al., 2023):** Validated size reductions up to 45% using fractal slots compared to rectangular patches.
2.  **Hexagonal Arrays (Jadhav & Pawase, 2015):** Proved that the 120-degree angles of hexagonal elements reduce mutual coupling in array configurations compared to 90-degree rectangular structures.
3.  **Impedance Tuning (Balanis, 2005):** Standard coaxial and microstrip matching limits indicate that slot loading shifts the input impedance curve, allowing a direct feed line connection without complex matching networks.
