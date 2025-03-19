# Problem 1
# Gravity Analysis in Celestial Mechanics and Space Exploration

This document addresses three key problems: Kepler's Third Law, escape and cosmic velocities, and trajectories of a payload released near Earth. Each section includes theoretical derivations, astronomical implications, and Python simulations.

---

## Problem 1: Orbital Period and Orbital Radius

### Derivation of Kepler’s Third Law for Circular Orbits

Kepler’s Third Law relates the square of the orbital period \( T^2 \) to the cube of the orbital radius \( r^3 \). For circular orbits:

Gravitational force:
\[ F_g = \frac{G M m}{r^2} \]

Centripetal force:
\[ F_c = \frac{m v^2}{r} \]

Equating:
\[ \frac{G M m}{r^2} = \frac{m v^2}{r} \]

Simplify:
\[ v^2 = \frac{G M}{r} \]

Velocity and period:
\[ v = \frac{2\pi r}{T} \]
\[ v^2 = \frac{4\pi^2 r^2}{T^2} \]

Substitute:
\[ \frac{4\pi^2 r^2}{T^2} = \frac{G M}{r} \]

Result:
\[ T^2 = \frac{4\pi^2}{G M} r^3 \]

### Implications for Astronomy

- **Planetary Masses**: The Moon’s orbit can estimate Earth’s mass.
- **Distances**: Planetary orbits around the Sun determine distances.
- **Satellite Orbits**: Used to design orbits with specific periods (e.g., geostationary).

### Real-World Examples

- **Moon**: \( r \approx 384,400 \, \text{km} \), \( T \approx 27.32 \, \text{days} \)
- **Earth**: \( r \approx 1 \, \text{AU} \), \( T = 1 \, \text{year} \)

### Python Simulation

```python
import numpy as np
import matplotlib.pyplot as plt

G = 6.67430e-11  # m^3 kg^-1 s^-2
M_earth = 5.972e24  # kg
M_sun = 1.989e30  # kg

def orbital_period(r, M):
    return np.sqrt((4 * np.pi**2 * r**3) / (G * M))

r_moon = 384400e3  # meters
T_moon = 27.32 * 86400  # seconds
r_earth = 1.496e11  # 1 AU in meters
T_earth = 365.25 * 86400  # seconds

r_values = np.logspace(6, 12, 100)  # meters
T_earth_values = orbital_period(r_values, M_earth)
T_sun_values = orbital_period(r_values, M_sun)

plt.figure(figsize=(10, 6))
plt.loglog(r_values**3, T_earth_values**2, label="Earth-centered orbits")
plt.loglog(r_values**3, T_sun_values**2, label="Sun-centered orbits")
plt.scatter([r_moon**3, r_earth**3], [T_moon**2, T_earth**2], color='red', label="Moon, Earth")
plt.xlabel("r³ (m³)")
plt.ylabel("T² (s²)")
plt.title("Kepler's Third Law: T² vs r³")
plt.legend()
plt.grid(True, which="both", ls="--")
plt.show()
Extension to Elliptical Orbits
For elliptical orbits, the semi-major axis ( a ) replaces ( r ):
[ T^2 = \frac{4\pi^2}{G M} a^3 ]

Problem 2: Escape Velocities and Cosmic Velocities
Definitions
First Cosmic Velocity (Orbital Velocity): [ v_1 = \sqrt{\frac{G M}{r}} ]
Second Cosmic Velocity (Escape Velocity): [ v_2 = \sqrt{\frac{2 G M}{r}} ]
Third Cosmic Velocity: Speed to escape a star system (approximated).
Derivations
Escape Velocity: Total energy must be zero: [ \frac{1}{2} m v^2 - \frac{G M m}{r} = 0 ] [ v = \sqrt{\frac{2 G M}{r}} ]
Calculations
Earth: ( r = 6.371 \times 10^6 , \text{m} ), ( M = 5.972 \times 10^{24} , \text{kg} )
( v_1 = 7.9 , \text{km/s} )
( v_2 = 11.2 , \text{km/s} )
Mars: ( r = 3.39 \times 10^6 , \text{m} ), ( M = 6.417 \times 10^{23} , \text{kg} )
( v_1 = 3.5 , \text{km/s} )
( v_2 = 5.0 , \text{km/s} )
Jupiter: ( r = 6.991 \times 10^7 , \text{m} ), ( M = 1.898 \times 10^{27} , \text{kg} )
( v_1 = 42.1 , \text{km/s} )
( v_2 = 59.5 , \text{km/s} )
Importance in Space Exploration
Satellites: ( v_1 ) for low orbits.
Missions: ( v_2 ) to leave Earth; ( v_3 ) for interstellar travel.
def orbital_velocity(M, r):
    return np.sqrt(G * M / r) / 1000  # km/s

def escape_velocity(M, r):
    return np.sqrt(2 * G * M / r) / 1000  # km/s

bodies = {
    "Earth": (5.972e24, 6.371e6),
    "Mars": (6.417e23, 3.39e6),
    "Jupiter": (1.898e27, 6.991e7)
}

velocities = {name: (orbital_velocity(M, r), escape_velocity(M, r)) for name, (M, r) in bodies.items()}

plt.figure(figsize=(10, 6))
for name, (v1, v2) in velocities.items():
    plt.bar([f"{name} v1", f"{name} v2"], [v1, v2])
plt.ylabel("Velocity (km/s)")
plt.title("Orbital and Escape Velocities")
plt.show()
Problem 3: Trajectories of a Freely Released Payload
Possible Trajectories
Elliptical: ( v < v_2 )
Parabolic: ( v = v_2 )
Hyperbolic: ( v > v_2 )
Numerical Analysis
Equations of motion:
[ \ddot{x} = -\frac{G M x}{r^3} ]
[ \ddot{y} = -\frac{G M y}{r^3} ]
where ( r = \sqrt{x^2 + y^2} ).
from scipy.integrate import odeint

def gravity(state, t, M):
    x, y, vx, vy = state
    r = np.sqrt(x**2 + y**2)
    ax = -G * M * x / r**3
    ay = -G * M * y / r**3
    return [vx, vy, ax, ay]

R_earth = 6.371e6  # m
h = 400e3  # m
r0 = R_earth + h
v_esc = escape_velocity(M_earth, r0) * 1000  # m/s

state0 = [r0, 0, 0, 0.9 * v_esc]  # elliptical
t = np.linspace(0, 20000, 1000)

sol = odeint(gravity, state0, t, args=(M_earth,))

plt.figure(figsize=(8, 8))
plt.plot(sol[:, 0], sol[:, 1], label="Trajectory")
circle = plt.Circle((0, 0), R_earth, color='blue', alpha=0.3)
plt.gca().add_artist(circle)
plt.axis("equal")
plt.xlabel("x (m)")
plt.ylabel("y (m)")
plt.title("Payload Trajectory")
plt.legend()
plt.show()
Discussion
Orbital Insertion: Low velocity yields stable orbits.
Reentry: Trajectories intersecting Earth.
Escape: High velocity for deep-space missions.