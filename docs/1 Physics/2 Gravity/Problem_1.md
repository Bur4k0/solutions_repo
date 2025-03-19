# Gravity - Celestial Mechanics and Space Exploration

## Problem 1: Orbital Period and Orbital Radius
### Motivation
The relationship between the square of the orbital period and the cube of the orbital radius, known as **Kepler's Third Law**, is fundamental in celestial mechanics. It allows the determination of planetary motions and connects gravity to real-world phenomena such as satellite orbits and planetary systems.

### Theory and Derivation
According to Newton's Law of Gravitation, the gravitational force acting on an object of mass \( m \) orbiting a massive body of mass \( M \) is given by:

$
F = \frac{GMm}{r^2}
$

For circular orbits, this force provides the centripetal force:

$
F = \frac{mv^2}{r}
$

By equating the two forces:

$
\frac{GMm}{r^2} = \frac{mv^2}{r}
$

Simplify and solve for the orbital speed \( v \):

$
v = \sqrt{\frac{GM}{r}}
$

Now, using the relationship between speed, radius, and period:

$
v = \frac{2 \pi r}{T}
$

$
\frac{2 \pi r}{T} = \sqrt{\frac{GM}{r}}
$

Squaring both sides and rearranging:

$
T^2 = \frac{4 \pi^2}{GM} r^3
$

This is **Kepler's Third Law**, where the square of the orbital period is proportional to the cube of the orbital radius.

### Implementation
```python
import numpy as np
import matplotlib.pyplot as plt

# Constants
G = 6.67430e-11  # Gravitational constant (m^3 kg^-1 s^-2)
M = 5.972e24      # Mass of the Earth (kg)

# Function to calculate orbital period
def orbital_period(r):
    return 2 * np.pi * np.sqrt(r**3 / (G * M))

# Generate orbital radii from 1e7 to 4e7 meters
radii = np.linspace(1e7, 4e7, 100)
periods = orbital_period(radii)

# Plotting
plt.figure(figsize=(10, 6))
plt.plot(radii, periods)
plt.title('Orbital Period vs. Orbital Radius')
plt.xlabel('Orbital Radius (m)')
plt.ylabel('Orbital Period (s)')
plt.grid(True)
plt.show()
```

### Simulation
This simulation plots the relationship between **Orbital Period** and **Orbital Radius**. It confirms the relationship defined by Kepler's Third Law. To further enhance this simulation, we can compare the theoretical and simulated values for different planetary bodies in the Solar System.

### Discussion
This relationship is instrumental in calculating planetary masses and distances. We'll further explore real-world examples such as the Moon's orbit around Earth and planetary orbits within the Solar System.

---

## Problem 2: Escape Velocities and Cosmic Velocities
### Simulation
```python
# Function to calculate velocities

def velocities(R):
    v_orb = np.sqrt(G * M / R)
    v_esc = np.sqrt(2 * G * M / R)
    return v_orb, v_esc

# Generate radii
radii = np.linspace(1e6, 2e7, 100)
v_orb_list, v_esc_list = [], []

for r in radii:
    v_orb, v_esc = velocities(r)
    v_orb_list.append(v_orb)
    v_esc_list.append(v_esc)

# Plotting
plt.figure(figsize=(10, 6))
plt.plot(radii, v_orb_list, label='Orbital Velocity')
plt.plot(radii, v_esc_list, label='Escape Velocity')
plt.title('Velocities vs. Radius')
plt.xlabel('Radius (m)')
plt.ylabel('Velocity (m/s)')
plt.legend()
plt.grid(True)
plt.show()
```

### Discussion
This simulation shows the relationship between **Orbital Velocity** and **Escape Velocity** for various radii. The difference between the two curves reflects how much speed is needed to overcome gravitational pull and achieve escape.

---

## Problem 3: Trajectories of a Freely Released Payload Near Earth
### Simulation
```python
from scipy.integrate import solve_ivp

# Constants
R_earth = 6.3781e6  # Radius of Earth (m)

# Differential equations for motion

def motion(t, y):
    x, y, vx, vy = y
    r = np.sqrt(x**2 + y**2)
    ax = -G * M * x / r**3
    ay = -G * M * y / r**3
    return [vx, vy, ax, ay]

# Initial conditions
x0, y0 = R_earth + 500000, 0  # Position (m)
vx0, vy0 = 0, 7500  # Initial velocity (m/s)

# Solving the differential equations
solution = solve_ivp(motion, [0, 6000], [x0, y0, vx0, vy0], max_step=1)
x, y = solution.y[0], solution.y[1]

# Plotting
plt.figure(figsize=(8, 8))
plt.plot(x, y)
plt.xlabel('x (m)')
plt.ylabel('y (m)')
plt.title('Trajectory of a Freely Released Payload')
plt.grid(True)
plt.axis('equal')
plt.show()
```

### Discussion
The simulation above demonstrates the trajectory of a freely released payload, considering Earth's gravitational pull. Different initial conditions can be used to analyze **parabolic, hyperbolic, and elliptical** trajectories.

---

The simulations for all three problems are now added. Would you like me to continue by improving the explanations and making the simulations more interactive and realistic? 
