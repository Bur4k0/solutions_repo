# Gravity: Problem 1 - Orbital Period and Orbital Radius

## Motivation

The relationship between the square of the orbital period and the cube of the orbital radius, famously known as **Kepler's Third Law**, forms a cornerstone of celestial mechanics. This elegant and profound relationship enables us to decipher planetary motions and carries deep implications for understanding gravitational interactions across both local and cosmic scales. By exploring this law, we can bridge fundamental gravitational principles with tangible phenomena, such as satellite orbits and planetary systems.

## Task

- Derive the relationship between the square of the orbital period ($T^2$) and the cube of the orbital radius ($r^3$) for circular orbits.
- Discuss the astronomical implications of this relationship, including its utility in determining planetary masses and distances.
- Analyze real-world examples, such as the Moon's orbit around Earth or planetary orbits within the Solar System.
- Implement a computational model to simulate circular orbits and validate the derived relationship.

## Deliverables

- A Markdown document featuring a Python script or notebook for simulation implementation.
- A comprehensive explanation of the concepts involved.
- Graphical representations illustrating circular orbits and the $T^2$ vs $r^3$ relationship.
- A discussion on the extension of this relationship to elliptical orbits and other celestial bodies.

---

## Derivation of Kepler's Third Law for Circular Orbits

For an object of mass $m$ in a circular orbit around a central body of mass $M$ at radius $r$, the gravitational force supplies the centripetal force required for circular motion.

### Gravitational Force
$
F_g = \frac{G M m}{r^2}
$
where $G = 6.674 \times 10^{-11} \, \text{m}^3 \text{kg}^{-1} \text{s}^{-2}$ is the gravitational constant.

### Centripetal Force
$
F_c = \frac{m v^2}{r}
$
where $v$ is the orbital velocity.

### Equating Forces
Since $F_g = F_c$:
$
\frac{G M m}{r^2} = \frac{m v^2}{r}
$
Cancel $m$ (assuming $m \neq 0$):
$
\frac{G M}{r^2} = \frac{v^2}{r}
$
Multiply both sides by $r$:
$
\frac{G M}{r} = v^2
$

### Relating Velocity to Period
The velocity is the circumference divided by the period $T$:
$
v = \frac{2\pi r}{T}
$
Thus:
$
v^2 = \left( \frac{2\pi r}{T} \right)^2 = \frac{4\pi^2 r^2}{T^2}
$

### Final Derivation
Substitute $v^2$ into the equation:
$
\frac{G M}{r} = \frac{4\pi^2 r^2}{T^2}
$
Solve for $T^2$:
$
T^2 = \frac{4\pi^2 r^3}{G M}
$
This is Kepler's Third Law for circular orbits: $T^2 \propto r^3$, with the constant of proportionality $\frac{4\pi^2}{G M}$ depending on the central mass $M$.

---

## Astronomical Implications

Kepler's Third Law is a powerful tool in astronomy:

- **Mass Calculation**: Measure $T$ and $r$ to find $M$:
  $
  M = \frac{4\pi^2 r^3}{G T^2}
 $
  This is critical for determining the masses of planets and stars using their satellites or orbiting companions.

- **Distance Estimation**: If $M$ is known (e.g., the Sun’s mass), $r$ can be derived from $T$, aiding in mapping celestial distances.

- **Applications**: From satellite orbit design to understanding exoplanet systems and binary stars, this law connects gravitational theory to observable phenomena.

---

## Real-World Examples

### Moon's Orbit Around Earth
- Radius: $r = 3.844 \times 10^8 \, \text{m}$
- Period: $T = 27.32 \, \text{days} = 2.36 \times 10^6 \, \text{s}$
- Earth’s mass: $M \approx 5.972 \times 10^{24} \, \text{kg}$

Verify:
$T^2 = (2.36 \times 10^6)^2 = 5.57 \times 10^{12} \, \text{s}^2$

$r^3 = (3.844 \times 10^8)^3 = 5.68 \times 10^{25} \, \text{m}^3$

$\frac{T^2}{r^3} \approx 9.8 \times 10^{-14} \, \text{s}^2 \text{m}^{-3}$

$\frac{4\pi^2}{G M} \approx 9.9 \times 10^{-14} \, \text{s}^2 \text{m}^{-3}$

The match confirms the law, with slight deviations due to the Moon’s elliptical orbit.

### Earth’s Orbit Around the Sun
- Radius: $r = 1.496 \times 10^{11} \, \text{m}$ (1 AU)
- Period: $T = 3.156 \times 10^7 \, \text{s}$ (365.25 days)
- Sun’s mass: $M \approx 1.989 \times 10^{30} \, \text{kg}$

$T^2 \approx 9.96 \times 10^{14} \, \text{s}^2$

$r^3 \approx 3.347 \times 10^{33} \, \text{m}^3$

$\frac{T^2}{r^3} \approx 2.98 \times 10^{-19} \, \text{s}^2 \text{m}^{-3}$

$\frac{4\pi^2}{G M} \approx 2.98 \times 10^{-19} \, \text{s}^2 \text{m}^{-3}$
Another validation of the law’s consistency.

---

## Computational Model

[Simulation3](simulation3.html)

### Output
- **Orbit Plot**: Displays the Moon’s circular path around Earth.
- **$T^2$ vs $r^3$ Plot**: A log-log graph showing a straight line, confirming $T^2 \propto r^3$.
- **Console**: Prints the ratio $T^2 / r^3$ matching the constant $4\pi^2 / (G M)$.

---

## Extension to Elliptical Orbits

For elliptical orbits, Kepler’s Third Law becomes:
$
T^2 = \frac{4\pi^2}{G M} a^3
$
where $a$ is the semi-major axis. This generalizes the circular case ($r = a$) and applies to:
- Planetary orbits (e.g., Earth’s slight eccentricity).
- Comets with highly elliptical paths.
- Binary star systems, where $M$ is the total mass.

The derivation involves conservation laws, but the $T^2 \propto a^3$ form persists, making it universally applicable.

---

## Conclusion

Kepler’s Third Law elegantly links gravitational dynamics to orbital motion, validated by examples like the Moon and Earth-Sun system. Its computational verification reinforces its precision, while its extension to elliptical orbits broadens its scope, cementing its role in celestial mechanics.

---
