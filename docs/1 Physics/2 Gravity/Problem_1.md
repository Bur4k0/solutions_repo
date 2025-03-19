# Problem 1: Orbital Period and Orbital Radius

## Motivation

The relationship between the square of the orbital period and the cube of the orbital radius, known as Kepler's Third Law, is a cornerstone of celestial mechanics. This simple yet profound relationship allows for the determination of planetary motions and has implications for understanding gravitational interactions on both local and cosmic scales. By analyzing this relationship, one can connect fundamental principles of gravity with real-world phenomena such as satellite orbits and planetary systems.

## Task Breakdown

1. Derive the relationship between $T^2$ and $r^3$ for circular orbits.
2. Discuss implications for astronomy (planetary masses, distances).
3. Analyze real-world examples (e.g., Moon’s orbit, Solar System planets).
4. Implement a computational model to simulate and verify the relationship (see HTML simulations).

## Derivation of Kepler’s Third Law for Circular Orbits

For a body in circular orbit around a central mass $M$:

Gravitational force:
$F_g = \frac{G M m}{r^2}$

Centripetal force:
$F_c = \frac{m v^2}{r}$

Equate:
$\frac{G M m}{r^2} = \frac{m v^2}{r}$

Simplify:
$v^2 = \frac{G M}{r}$

Velocity:
$v = \frac{2\pi r}{T}$
$v^2 = \frac{4\pi^2 r^2}{T^2}$

Substitute:
$\frac{4\pi^2 r^2}{T^2} = \frac{G M}{r}$

Result:
$T^2 = \frac{4\pi^2}{G M} r^3$

## Implications for Astronomy

1. **Calculating Planetary Masses**: Use $T$ and $r$ to find $M$ (e.g., Earth’s mass from the Moon).
2. **Determining Distances**: Compute $r$ for planets using $T$ and the Sun’s mass.
3. **Satellite Design**: Set orbital periods for satellites (e.g., geostationary).

## Real-World Examples

- **Moon’s Orbit**:
  - $r \approx 384,400 \, \text{km}$
  - $T \approx 27.32 \, \text{days}$
  - $M = 5.972 \times 10^{24} \, \text{kg}$ (Earth).
- **Earth’s Orbit**:
  - $r \approx 1 \, \text{AU} = 1.496 \times 10^8 \, \text{km}$
  - $T = 1 \, \text{year}$
  - $M = 1.989 \times 10^{30} \, \text{kg}$ (Sun).

## Simulations

The simulations are provided in separate HTML files:
- [Kepler’s Third Law Plot](kepler_third_law.html)
- [Moon’s Circular Orbit](moon_orbit.html)

Run the Python code below to generate the required plots, then view the HTML files in a browser.

```python
import numpy as np
import matplotlib.pyplot as plt

# Constants
G = 6.67430e-11
M_earth = 5.972e24
M_sun = 1.989e30

def orbital_period(r, M):
    return np.sqrt((4 * np.pi**2 * r**3) / (G * M))

r_moon = 384400e3
T_moon = 27.32 * 86400
r_earth = 1.496e11
T_earth = 365.25 * 86400

r_values = np.logspace(6, 12, 100)
T_earth_values = orbital_period(r_values, M_earth)
T_sun_values = orbital_period(r_values, M_sun)

# Plot 1: T^2 vs r^3
plt.figure(figsize=(10, 6))
plt.loglog(r_values**3, T_earth_values**2, label="Earth-centered orbits")
plt.loglog(r_values**3, T_sun_values**2, label="Sun-centered orbits")
plt.scatter([r_moon**3, r_earth**3], [T_moon**2, T_earth**2], color='red', label="Moon, Earth")
plt.xlabel("r³ (m³)")
plt.ylabel("T² (s²)")
plt.title("Kepler’s Third Law: T² vs r³")
plt.legend()
plt.grid(True, which="both", ls="--")
plt.savefig("kepler_plot.png")
plt.close()

# Plot 2: Moon’s orbit
theta = np.linspace(0, 2 * np.pi, 100)
x_moon = r_moon * np.cos(theta)
y_moon = r_moon * np.sin(theta)
plt.figure(figsize=(8, 8))
plt.plot(x_moon, y_moon, label="Moon’s Orbit")
plt.plot(0, 0, 'bo', label="Earth")
plt.axis("equal")
plt.xlabel("x (m)")
plt.ylabel("y (m)")
plt.title("Circular Orbit of the Moon")
plt.legend()
plt.grid(True)
plt.savefig("moon_orbit.png")
plt.close()