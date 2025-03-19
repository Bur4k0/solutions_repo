# Gravity - Orbital Period and Orbital Radius

## Motivation
The relationship between the square of the orbital period and the cube of the orbital radius, known as **Kepler's Third Law**, is a cornerstone of celestial mechanics. This fundamental principle helps in determining planetary motions and understanding gravitational interactions, which is essential for analyzing satellite orbits, planetary systems, and even entire galaxies.

## Theory and Derivation
### Kepler's Third Law
According to **Newton's Law of Gravitation**, the gravitational force acting on a mass \(m\) orbiting a much larger mass \(M\) (such as a planet orbiting a star) is:

$ F = \frac{GMm}{r^2} $

For circular orbits, this force provides the necessary centripetal force to keep the object in orbit:

$
F = \frac{mv^2}{r}
$

By equating these two forces:

$
\frac{GMm}{r^2} = \frac{mv^2}{r}
$

Solving for \(v\):

$
v = \sqrt{\frac{GM}{r}}
$

Using the relationship between velocity, radius, and period:

$
v = \frac{2 \pi r}{T}
$

Replacing \(v\) in the previous equation:

$
\frac{2 \pi r}{T} = \sqrt{\frac{GM}{r}}
$

Squaring both sides and rearranging:

$
T^2 = \frac{4 \pi^2}{GM} r^3
$

This equation shows that:

$
T^2 \propto r^3
$

This is **Kepler's Third Law**. The square of the orbital period \( T \) is directly proportional to the cube of the orbital radius \( r \).

## Simulation
We will now verify this relationship using a simple Python simulation.

```python
import numpy as np
import matplotlib.pyplot as plt

# Constants
G = 6.67430e-11  # Gravitational constant (m^3 kg^-1 s^-2)
M = 5.972e24      # Mass of the Earth (kg)

# Function to calculate orbital period
def orbital_period(r):
    return 2 * np.pi * np.sqrt(r**3 / (G * M))

# Generate radii from 1e7 to 4e7 meters
radii = np.linspace(1e7, 4e7, 100)
periods = orbital_period(radii)

# Plotting
plt.figure(figsize=(10, 6))
plt.plot(radii, periods, label='Simulated Data')
plt.title('Orbital Period vs. Orbital Radius')
plt.xlabel('Orbital Radius (m)')
plt.ylabel('Orbital Period (s)')
plt.legend()
plt.grid(True)
plt.show()
```

### Explanation of the Simulation
- We define a function `orbital_period()` to calculate the orbital period \( T \) for a given radius \( r \) using the derived formula.
- We generate a range of radii from \(1 \times 10^7\) m to \(4 \times 10^7\) m.
- The result is plotted to visualize the relationship between orbital period and radius.

## Implications in Astronomy
- This relationship allows calculation of planetary masses and distances by observing the orbital characteristics of moons or satellites.
- For example, the Moon's orbit around Earth and the orbits of planets in the Solar System follow this law closely.

## Extension to Elliptical Orbits
- Kepler's Third Law can also be extended to elliptical orbits by using the **semi-major axis** \(a\) instead of \(r\) (valid for perfectly circular orbits).