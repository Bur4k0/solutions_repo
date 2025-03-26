# Problem 1

---

### Step 1: Select a Regular Polygon
Let's choose a simple regular polygon to work with. A **square** is a good starting point because it has 4 vertices, which makes the calculations manageable while still allowing us to observe interesting interference patterns.

- A square has 4 vertices.
- Place the square in the coordinate plane with its center at the origin $(0, 0)$.
- Let the side length of the square be $2a$ (so the distance from the center to a vertex is $a\sqrt{2}$).
- The vertices of the square are at:
  - $(a, a)$
  - $(a, -a)$
  - $(-a, -a)$
  - $(-a, a)$

For simplicity, let's set $a = 1$, so the vertices are at:
- $(1, 1)$
- $(1, -1)$
- $(-1, -1)$
- $(-1, 1)$

---

### Step 2: Position the Sources
We place point wave sources at the vertices of the square, so we have 4 sources located at the coordinates above. Each source emits a circular wave described by the single disturbance equation:

$\eta(x, y, t) = \frac{A}{\sqrt{r}} \cos(kr - \omega t + \phi)$

Where:
- $\eta(x, y, t)$: Displacement of the water surface at point $(x, y)$ and time $t$.
- $A$: Amplitude of the wave.
- $k = \frac{2\pi}{\lambda}$: Wave number ($\lambda$ is the wavelength).
- $\omega = 2\pi f$: Angular frequency ($f$ is the frequency).
- $r = \sqrt{(x - x_0)^2 + (y - y_0)^2}$: Distance from the source at $(x_0, y_0)$ to the point $(x, y)$.
- $\phi$: Initial phase.

**Assumptions (from considerations):**
- All sources emit waves with the same amplitude $A$, wavelength $\lambda$, and frequency $f$.
- The waves are coherent, maintaining a constant phase difference. Let's assume $\phi = 0$ for simplicity (all sources are in phase).

Let's set some values for the parameters:
- $A = 1$ (arbitrary amplitude for simplicity).
- $\lambda = 1$ (so $k = \frac{2\pi}{\lambda} = 2\pi$).
- $f = 1$ (so $\omega = 2\pi f = 2\pi$).
- $\phi = 0$.

---

### Step 3: Wave Equations
For each source, we write the wave equation based on its position. The distance $r_i$ from each source to a point $(x, y)$ is:

- Source 1 at $(1, 1)$: $r_1 = \sqrt{(x - 1)^2 + (y - 1)^2}$
- Source 2 at $(1, -1)$: $r_2 = \sqrt{(x - 1)^2 + (y + 1)^2}$
- Source 3 at $(-1, -1)$: $r_3 = \sqrt{(x + 1)^2 + (y + 1)^2}$
- Source 4 at $(-1, 1)$: $r_4 = \sqrt{(x + 1)^2 + (y - 1)^2}$

The wave equation for each source is:

$\eta_i(x, y, t) = \frac{A}{\sqrt{r_i}} \cos(kr_i - \omega t + \phi)$

Substituting the values ($A = 1$, $k = 2\pi$, $\omega = 2\pi$, $\phi = 0$):

$\eta_i(x, y, t) = \frac{1}{\sqrt{r_i}} \cos(2\pi r_i - 2\pi t)$

So, for each source:
- $\eta_1(x, y, t) = \frac{1}{\sqrt{r_1}} \cos(2\pi r_1 - 2\pi t)$
- $\eta_2(x, y, t) = \frac{1}{\sqrt{r_2}} \cos(2\pi r_2 - 2\pi t)$
- $\eta_3(x, y, t) = \frac{1}{\sqrt{r_3}} \cos(2\pi r_3 - 2\pi t)$
- $\eta_4(x, y, t) = \frac{1}{\sqrt{r_4}} \cos(2\pi r_4 - 2\pi t)$

---

### Step 4: Superposition of Waves
The total displacement at point $(x, y)$ at time $t$ is the sum of the displacements from all sources (since $N = 4$):

$\eta_{\text{sum}}(x, y, t) = \sum_{i=1}^{4} \eta_i(x, y, t)$

$\eta_{\text{sum}}(x, y, t) = \sum_{i=1}^{4} \frac{1}{\sqrt{r_i}} \cos(2\pi r_i - 2\pi t)$

To analyze the interference pattern, we can simplify by looking at a specific time, say $t = 0$:

$\eta_{\text{sum}}(x, y, 0) = \sum_{i=1}^{4} \frac{1}{\sqrt{r_i}} \cos(2\pi r_i)$

---

### Step 5: Analyze Interference Patterns
Now we need to examine $\eta_{\text{sum}}(x, y, 0)$ as a function of position $(x, y)$.

- **Constructive Interference**: Occurs when the waves are in phase, i.e., the phase difference $2\pi (r_i - r_j)$ is a multiple of $2\pi$. This happens when the path difference $r_i - r_j$ is an integer multiple of the wavelength $\lambda = 1$.
- **Destructive Interference**: Occurs when the waves are out of phase, i.e., the phase difference is an odd multiple of $\pi$, so the path difference $r_i - r_j$ is an odd multiple of $\frac{\lambda}{2} = 0.5$.

Let's evaluate the pattern at a few key points:

1. **At the origin $(0, 0)$**:
   - $r_1 = \sqrt{(0-1)^2 + (0-1)^2} = \sqrt{2}$
   - $r_2 = \sqrt{(0-1)^2 + (0+1)^2} = \sqrt{2}$
   - $r_3 = \sqrt{(0+1)^2 + (0+1)^2} = \sqrt{2}$
   - $r_4 = \sqrt{(0+1)^2 + (0-1)^2} = \sqrt{2}$

   All distances are equal ($r_1 = r_2 = r_3 = r_4 = \sqrt{2}$), so the waves are in phase:

   $\eta_{\text{sum}}(0, 0, 0) = 4 \cdot \frac{1}{\sqrt{\sqrt{2}}} \cos(2\pi \sqrt{2}) \approx 4 \cdot \frac{1}{1.414} \cdot \cos(2\pi \cdot 1.414)$

   $\cos(2\pi \cdot 1.414) \approx \cos(2.828\pi) = \cos(0.828\pi) \approx -0.5$

   $\eta_{\text{sum}}(0, 0, 0) \approx 4 \cdot 0.707 \cdot (-0.5) \approx -1.414$

   The amplitude is non-zero, indicating constructive interference, though the negative value is due to the phase.

2. **Along the x-axis, e.g., $(x, 0)$**:
   - $r_1 = \sqrt{(x-1)^2 + (0-1)^2} = \sqrt{(x-1)^2 + 1}$
   - $r_2 = \sqrt{(x-1)^2 + (0+1)^2} = \sqrt{(x-1)^2 + 1}$
   - $r_3 = \sqrt{(x+1)^2 + (0+1)^2} = \sqrt{(x+1)^2 + 1}$
   - $r_4 = \sqrt{(x+1)^2 + (0-1)^2} = \sqrt{(x+1)^2 + 1}$

   Notice that $r_1 = r_2$ and $r_3 = r_4$, so we can pair the contributions:

   $\eta_{\text{sum}}(x, 0, 0) = 2 \cdot \frac{1}{\sqrt{\sqrt{(x-1)^2 + 1}}} \cos(2\pi \sqrt{(x-1)^2 + 1}) + 2 \cdot \frac{1}{\sqrt{\sqrt{(x+1)^2 + 1}}} \cos(2\pi \sqrt{(x+1)^2 + 1})$

   This expression shows symmetry along the x-axis, and we can compute it for various $x$ to find regions of constructive and destructive interference.

---

### Step 6: Visualization
To visualize the interference pattern, we would typically plot $\eta_{\text{sum}}(x, y, 0)$ over a grid of $(x, y)$ values. Since the problem suggests using tools like Python with Matplotlib, the pattern would show:
- **Symmetry**: Due to the square's symmetry, the interference pattern will be symmetric about the x and y axes.
- **Constructive regions**: Where the amplitude is large (bright spots in a plot).
- **Destructive regions**: Where the amplitude is near zero (dark spots).

The pattern will resemble a grid-like structure with peaks and troughs, reflecting the interference of four coherent sources.

---

[Interference Pattern Simulation](Interference_Pattern_simulation.html)

2. **Explanation**: The interference pattern for a square shows a grid-like structure with constructive interference at the center and along symmetric lines, and destructive interference where the path differences lead to phase cancellation.

3. **Graphical Representation**: The plot would show a 2D heatmap with red and blue regions indicating constructive and destructive interference, respectively.

---

