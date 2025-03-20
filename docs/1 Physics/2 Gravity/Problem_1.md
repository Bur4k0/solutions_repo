# Kepler's Third Law: Orbital Period and Radius in Circular Orbits

## Introduction
Kepler's Third Law establishes a profound connection between the square of an object's orbital period ($T^2$) and the cube of its orbital radius ($r^3$) for bodies in gravitational orbits. Originally an empirical observation by Johannes Kepler, it was later grounded in Newtonian mechanics. This relationship is fundamental to celestial mechanics, enabling us to probe the masses of celestial bodies and their orbital characteristics. Here, we derive this law for circular orbits, explore its astronomical implications, analyze real-world examples, and simulate it computationally using Python.

## Derivation of the Relationship
For a body of mass $m$ orbiting a central body of mass $M$ in a circular orbit with radius $r$, the gravitational force provides the necessary centripetal force.

### Step 1: Gravitational Force
The gravitational force is:
$
F_g = \frac{G M m}{r^2}
$
where $G$ is the gravitational constant ($6.674 \times 10^{-11} \, \text{m}^3 \text{kg}^{-1} \text{s}^{-2}$).

### Step 2: Centripetal Force
For circular motion at velocity $v$, the centripetal force is:
$
F_c = \frac{m v^2}{r}
$

### Step 3: Equate Forces
Since $F_g = F_c$:
$
\frac{G M m}{r^2} = \frac{m v^2}{r}
$
Cancel $m$ (assuming $m \neq 0$):
$
\frac{G M}{r^2} = \frac{v^2}{r}
$
Multiply by $r$:
$
\frac{G M}{r} = v^2
$

### Step 4: Relate Velocity to Period
The orbital velocity is the circumference divided by the period $T$:
$
v = \frac{2\pi r}{T}
$
So:
$
v^2 = \left(\frac{2\pi r}{T}\right)^2 = \frac{4\pi^2 r^2}{T^2}
$

### Step 5: Substitute and Solve
Substitute $v^2$ into the force equation:
$
\frac{G M}{r} = \frac{4\pi^2 r^2}{T^2}
$
Multiply both sides by $T^2$ and divide by $G M$:
$
T^2 = \frac{4\pi^2 r^3}{G M}
$
Thus:
$
T^2 = k r^3
$
where $k = \frac{4\pi^2}{G M}$ is a constant for a given central mass $M$. This is Kepler's Third Law for circular orbits: $T^2 \propto r^3$.

## Astronomical Implications
This relationship is a cornerstone of astronomy:
- **Mass Determination**: If $T$ and $r$ are measured (e.g., for a moon or satellite), $M$ can be calculated:
  $
  M = \frac{4\pi^2 r^3}{G T^2}
  $
  This is how we estimate the masses of planets and stars.
- **Distance Measurement**: Knowing $M$ (e.g., the Sun’s mass) and $T$ allows computation of $r$, aiding in mapping orbital systems.
- **Satellite Orbits**: Engineers use this to design orbits for artificial satellites, balancing period and altitude.
- **Cosmic Scales**: It applies to binary stars, exoplanets, and even galaxy clusters, linking local gravity to cosmic dynamics.

## Real-World Examples
### 1. Moon’s Orbit Around Earth
- $r = 384,400 \, \text{km} = 3.844 \times 10^8 \, \text{m}$
- $T = 27.32 \, \text{days} = 2.36 \times 10^6 \, \text{s}$
- $M_{\text{Earth}} \approx 5.972 \times 10^{24} \, \text{kg}$
- $G = 6.674 \times 10^{-11} \, \text{m}^3 \text{kg}^{-1} \text{s}^{-2}$

Calculate:
$
T^2 = (2.36 \times 10^6)^2 = 5.57 \times 10^{12} \, \text{s}^2
$
$
r^3 = (3.844 \times 10^8)^3 = 5.68 \times 10^{25} \, \text{m}^3
$
$
\frac{T^2}{r^3} \approx 9.8 \times 10^{-14} \, \text{s}^2 \text{m}^{-3}
$
$
\frac{4\pi^2}{G M} \approx 9.9 \times 10^{-14} \, \text{s}^2 \text{m}^{-3}
$
The close agreement validates the law (minor discrepancies reflect the Moon’s elliptical orbit).

### 2. Earth’s Orbit Around the Sun
- $r = 1 \, \text{AU} = 1.496 \times 10^{11} \, \text{m}$
- $T = 365.25 \, \text{days} = 3.156 \times 10^7 \, \text{s}$
- $M_{\text{Sun}} \approx 1.989 \times 10^{30} \, \text{kg}$

$
T^2 = (3.156 \times 10^7)^2 \approx 9.96 \times 10^{14} \, \text{s}^2
$
$
r^3 = (1.496 \times 10^{11})^3 \approx 3.347 \times 10^{33} \, \text{m}^3
$
$
\frac{T^2}{r^3} \approx 2.98 \times 10^{-19} \, \text{s}^2 \text{m}^{-3}
$
$
\frac{4\pi^2}{G M} \approx 2.98 \times 10^{-19} \, \text{s}^2 \text{m}^{-3}
$
Another confirmation of the law’s universality.

## Computational Model
Below is a Python script to simulate a circular orbit and verify the relationship. It plots the orbit and checks $T^2 \propto r^3$ across multiple radii.

```python
import numpy as np
import matplotlib.pyplot as plt

# Constants
G = 6.674e-11  # m^3 kg^-1 s^-2
M = 5.972e24   # kg (Earth)

# Function to calculate period
def orbital_period(r, G, M):
    return np.sqrt((4 * np.pi**2 * r**3) / (G * M))

# Simulate Moon’s orbit
r_moon = 3.844e8  # m
T_moon = orbital_period(r_moon, G, M)
t = np.linspace(0, T_moon, 1000)
theta = (2 * np.pi / T_moon) * t
x = r_moon * np.cos(theta)
y = r_moon * np.sin(theta)

# Plot orbit
plt.figure(figsize=(6, 6))
plt.plot(x, y, label="Moon’s Orbit")
plt.plot(0, 0, 'yo', label="Earth")
plt.axis('equal')
plt.title("Circular Orbit Simulation (Moon)")
plt.xlabel("x (m)")
plt.ylabel("y (m)")
plt.legend()
plt.grid()
plt.show()

# Verify T^2 vs r^3
r_values = np.logspace(7, 9, 5)  # Various radii (10^7 to 10^9 m)
T_values = [orbital_period(r, G, M) for r in r_values]
T2 = np.array(T_values)**2
r3 = r_values**3

# Plot T^2 vs r^3
plt.figure(figsize=(8, 5))
plt.loglog(r3, T2, 'bo-', label="Simulated Data")
plt.loglog(r3, (4 * np.pi**2 / (G * M)) * r3, 'r--', label="Kepler’s Law")
plt.title("T² vs r³ Relationship")
plt.xlabel("r³ (m³)")
plt.ylabel("T² (s²)")
plt.legend()
plt.grid()
plt.show()

# Check constant
for r, T in zip(r_values, T_values):
    print(f"r = {r:.2e} m, T²/r³ = {T**2/r**3:.2e} s²/m³, 4π²/(GM) = {4 * np.pi**2 / (G * M):.2e} s²/m³")
```

### Output Explanation
- **Orbit Plot**: Shows the Moon’s circular path around Earth, centered at (0,0).
- **$T^2$ vs $r^3$ Plot**: A log-log plot confirms the linear relationship (slope = 1), with the theoretical line matching the simulated points.
- **Console Output**: Compares the computed ratio $T^2 / r^3$ to the constant $4\pi^2 / (G M)$, verifying consistency.

## Extension to Elliptical Orbits
For elliptical orbits, Kepler’s Third Law generalizes to:
$
T^2 = \frac{4\pi^2}{G M} a^3
$
where $a$ is the semi-major axis (half the longest diameter of the ellipse), not the radius, since the orbit isn’t circular. The derivation involves angular momentum conservation and energy, but the form remains $T^2 \propto a^3$. This applies to:
- **Planets**: Most Solar System orbits are slightly elliptical (e.g., Earth’s eccentricity is ~0.017).
- **Comets**: Highly elliptical orbits (e.g., Halley’s Comet) still obey this law using $a$.
- **Binary Systems**: Elliptical orbits of stars or black holes follow the same principle, with $M$ as the total system mass.

The circular case is a special instance where $r = a$. For simulation, an elliptical orbit requires solving Kepler’s equation numerically or using parametric equations ($x = a \cos t$, $y = b \sin t$, adjusted for time), but the $T^2 \propto a^3$ relationship holds.

## Conclusion
Kepler’s Third Law ties gravitational physics to observable orbits, from the Moon to distant exoplanets. Its derivation reveals the balance of forces, while its applications unlock celestial secrets. Simulations confirm its precision, and its extension to elliptical orbits broadens its reach, making it a timeless tool in understanding the cosmos.

[kepler_third_law](kepler_third_law.html)