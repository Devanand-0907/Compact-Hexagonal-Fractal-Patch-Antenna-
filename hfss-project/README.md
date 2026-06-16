# ANSYS HFSS Simulation Guide

This folder contains details for modeling, meshing, and simulating the **Compact Hexagonal Fractal Patch Antenna** using **ANSYS HFSS (High Frequency Structure Simulator)**.

---

## 1. HFSS Project Setup

### 1.1 Geometry & Material Mapping
*   **Substrate:** Create a Box of size $49.41\text{ mm} \times 49.41\text{ mm} \times 1.6\text{ mm}$. Assign material as `FR4_epoxy` ($\epsilon_r = 4.4, \tan\delta = 0.02$).
*   **Ground Plane:** Create a Rectangle on the bottom surface ($Z = 0$). Assign boundary as `Perfect E` (PEC).
*   **Top Patch:** Create a solid regular hexagon of radius $b = 41.69\text{ mm}$ (outer radiating limit) centered at $(0,0,1.6)$. 
*   **Fractal Slots:** Subtract circular elements from the hexagonal patch using Boolean operations:
    *   Subtract Circle 1 (radius $c = 3.0\text{ mm}$) at coordinates defined in the coordinates table.
*   **Feed Line:** Create a microstrip rectangle of length $17.39\text{ mm}$ and width $d = 6.64\text{ mm}$ connecting the bottom edge to the patch.

### 1.2 Boundary Conditions (Air Box)
*   Create an Air Box surrounding the substrate.
*   **Sizing Rule:** The boundaries of the air box must be placed at least $\lambda/4$ away from the radiating edges in all directions to prevent back-reflection errors. At $2.4\text{ GHz}$:
    
    $$\lambda = \frac{3 \times 10^8}{2.4 \times 10^9} = 125\text{ mm} \implies \frac{\lambda}{4} \approx 31.25\text{ mm}$$
    
*   Assign the outer surfaces of the Air Box as `Radiation` boundary.

---

## 2. Excitation Setup (Microstrip Feed)
*   Create a vertical sheet at the edge of the microstrip line extending from the ground plane ($Z = 0$) to the top patch ($Z = 1.6\text{ mm}$).
*   Assign a **Lumped Port** or **Wave Port** to this sheet.
*   Set the reference integration line from the ground plane vertically up to the center of the copper feed strip, maintaining a $50\ \Omega$ characteristic impedance reference.

---

## 3. Analysis Setup & Meshing Solver
*   **Solution Frequency:** $2.4\text{ GHz}$
*   **Adaptive Solutions:**
    *   Maximum number of passes: `6 - 12`
    *   Convergence criteria: Maximum Delta S $< 0.02$
*   **Mesh Configuration:** HFSS utilizes a tetrahedral meshing scheme. Ensure that the boundary edges of the circular fractal slots have mesh refinement turned on to capture the dense fringing fields around the slots.
*   **Frequency Sweep:** 
    *   Type: `Interpolating` or `Fast`
    *   Range: $1.0\text{ GHz}$ to $3.0\text{ GHz}$
    *   Step size: $0.01\text{ GHz}$ (101 points)
