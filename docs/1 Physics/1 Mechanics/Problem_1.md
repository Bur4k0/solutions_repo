# Problem 1
# Projectile Motion Analysis and Simulation

## 1. Theoretical Foundation

Projectile motion is a classic example of motion under constant acceleration, where the only force acting is gravity (assuming no air resistance for now). We derive the equations from first principles using Newton’s second law.

### Governing Equations

In a 2D Cartesian coordinate system:

- **Horizontal motion:** No forces act, so acceleration $a_x = 0$ and velocity remains constant:
  $v_x = v_0 \cos\theta$
  $x(t) = v_0 \cos\theta \cdot t$

- **Vertical motion:** Gravity acts downward with acceleration $a_y = -g$:
  $v_y = v_0 \sin\theta - g t$
  $y(t) = v_0 \sin\theta \cdot t - \frac{1}{2} g t^2$

These parametric equations describe a parabolic trajectory.

### Family of Solutions

The trajectory depends on initial conditions:
- Higher $v_0$ results in a larger range and peak height.
- Changing $\theta$ alters the steepness and symmetry.
- Varying $g$ (e.g., on the Moon, $g \approx 1.6 \text{ m/s}^2$) changes the scale.

---

## 2. Analysis of the Range

The range $R$ is the horizontal distance when $y = 0$ (assuming equal launch and landing height).

### Time of Flight
Setting $y(t) = 0$ and solving for $t$:
$t = \frac{2 v_0 \sin\theta}{g}$

### Range Equation
Substituting into $x(t)$:
$R = \frac{v_0^2 \sin 2\theta}{g}$

### Dependence on Parameters
- **Maximum Range:** Achieved at $\theta = 45^\circ$, with $R_{\max} = \frac{v_0^2}{g}$.
- **Initial Velocity:** Range scales with $v_0^2$, so doubling $v_0$ quadruples $R$.
- **Gravity:** Lower $g$ results in a longer range.

---

## 3. Practical Applications

This model applies to:
- **Sports:** Basketball shots, soccer kicks, javelin throws.
- **Engineering:** Artillery trajectories, water fountains.
- **Astrophysics:** Lunar landings, planetary surface exploration.

### Extensions:
- **Uneven Terrain:** Adjusts time of flight using $y(t) = -h$.
- **Air Resistance:** Introduces drag, requiring numerical solutions.

---

## 4. Implementation

We develop a Python simulation to visualize projectile motion.

### Python Code for Simulation

```python
import numpy as np
import matplotlib.pyplot as plt

def projectile_motion(v0, theta, g=9.81, dt=0.01):
    theta_rad = np.radians(theta)
    vx, vy = v0 * np.cos(theta_rad), v0 * np.sin(theta_rad)
    x, y, t = [0], [0], 0
    while y[-1] >= 0:
        t += dt
        x.append(vx * t)
        y.append(vy * t - 0.5 * g * t**2)
    return x, y

v0 = 20  # Initial velocity
angles = [30, 45, 60]
plt.figure()
for angle in angles:
    x, y = projectile_motion(v0, angle)
    plt.plot(x, y, label=f"{angle} degrees")
plt.xlabel("Horizontal Distance (m)")
plt.ylabel("Vertical Distance (m)")
plt.legend()
plt.title("Projectile Motion for Different Angles")
plt.show()
```

### Graphical Representation

The simulation plots projectile motion for different angles, illustrating how range varies with initial conditions.

### Limitations and Realistic Extensions

- **Idealized Assumptions:** No air resistance, flat terrain.
- **Realistic Factors:** Wind, drag force, varying gravity.
- **Numerical Methods:** Required for solving equations with air resistance.

---

This document provides a theoretical foundation, computational implementation, and practical insights into projectile motion.

