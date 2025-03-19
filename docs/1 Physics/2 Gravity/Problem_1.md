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

[Kepler’s Third Law Plot](kepler_third_law.html)
[Moon’s Circular Orbit](moon_orbit.html)