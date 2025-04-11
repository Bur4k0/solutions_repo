
---

# **Measuring Earth's Gravitational Acceleration with a Pendulum**

## **Materials Used**
- String length: 1.0 m  

- Weight: [e.g., metal keychain]  

- Stopwatch resolution: ±0.01 s  

- Ruler resolution: ±0.005 m  

---

## **Procedure Summary**
- Pendulum length $L$: Measured from suspension point to center of mass of the bob  
- Time for 10 full oscillations recorded 10 times  

- Period $T$ calculated as $\frac{t_{10}}{10}$  

- Acceleration due to gravity $g$ found using the formula:  

  $g = \frac{4\pi^2 L}{T^2}$

---

## **1. Tabulated Data**

```markdown
| Trial | Time for 10 Oscillations $t_{10}$ (s) | Period $T = \frac{t_{10}}{10}$ (s) |
|-------|-------------------------------------------|----------------------------------------|
| 1     |                                           |                                        |
| 2     |                                           |                                        |
| 3     |                                           |                                        |
| 4     |                                           |                                        |
| 5     |                                           |                                        |
| 6     |                                           |                                        |
| 7     |                                           |                                        |
| 8     |                                           |                                        |
| 9     |                                           |                                        |
| 10    |                                           |                                        |
```

Add your measured values in the second column, compute the period for each in the third column.

---

## **2. Calculations**

### **Mean Period $\bar{T}$:**

$\bar{T} = \frac{1}{10} \sum_{i=1}^{10} T_i$

### **Standard Deviation $\sigma$:**

$\sigma = \sqrt{\frac{1}{n-1} \sum_{i=1}^{n} (T_i - \bar{T})^2}$

### **Uncertainty in Mean Time $\Delta T$:**

$\Delta T = \frac{\sigma}{\sqrt{n}}$

---

## **3. Calculation of $g$:**

$g = \frac{4\pi^2 L}{\bar{T}^2}$

---

## **4. Uncertainty in $g$:**

Use propagation of uncertainties:

$\left(\frac{\Delta g}{g}\right)^2 = \left(\frac{\Delta L}{L}\right)^2 + \left(2 \cdot \frac{\Delta T}{\bar{T}}\right)^2$

Then:

$\Delta g = g \cdot \sqrt{ \left(\frac{\Delta L}{L}\right)^2 + \left(2 \cdot \frac{\Delta T}{\bar{T}}\right)^2 }$

---

## **5. Final Results:**

```markdown
- Measured Pendulum Length $L$: ___ m ± ___ m

- Mean Period $\bar{T}$: ___ s ± ___ s

- Gravitational Acceleration $g$: ___ m/s² ± ___ m/s²

- Standard Value of $g$: 9.80665 m/s²

- Percent Error: ___%
```

---

[Simulation](deneme_2.html)

[Simulation-2](deneme.html)

## **6. Discussion**

### **Comparison with Standard Value:**
Compare your value of $g$ with 9.81 m/s². If there's a significant deviation, consider the following sources of error.

### **Sources of Uncertainty:**

1. **Measurement of Length $L$:**
   - Uncertainty due to the resolution of the ruler.

   - Misalignment of the ruler or measuring from incorrect reference points.

2. **Timing Variability:**
   - Human reaction time when using a stopwatch (can be ±0.2s cumulatively over 10 oscillations).

   - Multiple trials reduce this uncertainty.

3. **Amplitude Assumption:**
   - Pendulum motion should be small-angle (<15°) to satisfy the simple harmonic motion approximation.

   - Larger angles introduce systematic error in $T$.

4. **Other Experimental Limitations:**
   - Air resistance and friction at the pivot.

   - Non-rigid string or slight changes in the swing plane.

---
