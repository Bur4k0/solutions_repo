# Gravity

## Problem 1: Orbital Period and Orbital Radius

### Motivation
The relationship between the square of the orbital period and the cube of the orbital radius, known as Kepler's Third Law, is a cornerstone of celestial mechanics. This simple yet profound relationship allows for the determination of planetary motions and has implications for understanding gravitational interactions on both local and cosmic scales. By analyzing this relationship, one can connect fundamental principles of gravity with real-world phenomena such as satellite orbits and planetary systems.

### Task
- Derive the relationship between the square of the orbital period and the cube of the orbital radius for circular orbits.
- Discuss the implications of this relationship for astronomy, including its role in calculating planetary masses and distances.
- Analyze real-world examples, such as the Moon's orbit around Earth or the orbits of planets in the Solar System.
- Implement a computational model to simulate circular orbits and verify the relationship.

## Kepler's Third Law Derivation
Kepler's Third Law states:

$T^2 \propto R^3$

From Newton’s form of Kepler’s Law, we use the gravitational force as the centripetal force:

$F = \frac{GMm}{R^2} = m\frac{v^2}{R}$

Velocity in a circular orbit is given by:

$v = \frac{2\pi R}{T}$

Substituting:

$\frac{GM}{R^2} = \frac{4\pi^2 R}{T^2}$

Rearranging for \(T^2\):

$T^2 = \frac{4\pi^2}{GM} R^3$

This confirms Kepler’s Third Law.

## Implications for Astronomy
Kepler’s Third Law allows astronomers to:
- Determine the mass of celestial bodies by measuring the orbits of their satellites.
- Calculate distances between planets and stars based on orbital data.
- Understand the motion of exoplanets around distant stars using Doppler spectroscopy.

### Real-World Examples
- **Moon’s Orbit Around Earth**: Using Kepler’s Third Law, we can determine the Moon’s orbital period (about 27.3 days) given its average orbital radius of ~384,400 km.
- **Planets in the Solar System**: The relationship $T^2 \propto R^3$ holds for all planets orbiting the Sun, allowing astronomers to predict orbital periods of newly discovered celestial objects.

## Computational Model
A Python-based computational model can be used to simulate and verify Kepler’s Third Law.

```python
import numpy as np
import matplotlib.pyplot as plt
from scipy.constants import G

# Constants
M_earth = 5.972e24  # kg (mass of Earth)
R_earth = 6.371e6  # m (radius of Earth)

def orbital_period(radius, central_mass):
    return 2 * np.pi * np.sqrt(radius**3 / (G * central_mass))

# Generate orbital radii (in meters)
orbit_radii = np.linspace(R_earth + 300e3, R_earth + 42e6, 100)

# Compute orbital periods (in seconds)
orbit_periods = orbital_period(orbit_radii, M_earth)

# Convert to hours
orbit_periods_hours = orbit_periods / 3600

# Verify Kepler's Third Law
T_squared = orbit_periods**2
R_cubed = orbit_radii**3

# Plotting the relationship
plt.figure(figsize=(10, 5))
plt.plot(R_cubed, T_squared, label="$T^2$ vs. $R^3$")
plt.xlabel("Orbital Radius Cubed ($m^3$)")
plt.ylabel("Orbital Period Squared ($s^2$)")
plt.title("Verification of Kepler's Third Law")
plt.legend()
plt.grid()
plt.show()
```

[simulation3](simulation3.html)

### Explanation
- The script creates an orbital path using the HTML5 `<canvas>` element.
- A red dot moves along a circular trajectory to represent a satellite.
- The animation runs continuously using `requestAnimationFrame` to update the position of the orbiting body.

## Extending to Elliptical Orbits
Kepler’s Third Law applies to elliptical orbits by considering the semi-major axis $a$ instead of the radius $R$:

$T^2 = \frac{4\pi^2}{GM} a^3$

This means the orbital period still depends on the cube of the semi-major axis rather than just the radius.

## Conclusion
This document explains Kepler’s Third Law, derives its mathematical formulation, and provides interactive simulations and computational models to verify and visualize the concept. The law is fundamental in astrophysics and celestial mechanics, helping us understand planetary motions, satellite orbits, and exoplanetary systems.

