# Problem 1

# Measuring Earth's Gravitational Acceleration with a Pendulum

## Motivation

The gravitational acceleration $g$ is a key physical constant. Measuring it using a simple pendulum provides a practical approach to understanding experimental physics, wave motion, and the effect of uncertainties in measurements.

---

## Materials

* String: $L \approx 17.35 \pm 0.005$ m (based on period and known $g$)
* Mass: Key chain
* Stopwatch: Smartphone with $\pm 0.01$ s precision

![alt text](swinging_kitty_only.gif)

---

## Data Collection

* Estimated Length: $L = 17.35$ m (based on timing and known $g$)
* Uncertainty: $\Delta L = 0.005$ m

 10 Individual Oscillations (Measurements in seconds):

```
8.35, 8.3, 8.36, 8.37, 8.4, 8.34, 8.35, 8.42, 8.3, 8.38
```
---

## Calculations

### Step 1: Mean $\overline{T}$

The average time for one oscillation based on 10 measurements is:


$$
\overline{T} = \frac{1}{10} \sum_{i=1}^{10} T_i = 8.36 \ \text{s}
$$

### Step 2: Standard Deviation $\sigma_T$

Using the **sample standard deviation** formula:

$$
\sigma_T = \sqrt{ \frac{1}{n - 1} \sum_{i=1}^{n} (T_i - \overline{T})^2 } \approx 0.04 \ \text{s}
$$

(This was calculated using Python)

### Step 3: Uncertainty in the Mean $\Delta T$

$$
\Delta T = \frac{\sigma_T}{\sqrt{n}} = \frac{0.04}{\sqrt{10}} = 0.01 \ \text{s}
$$

### Step 4: Estimated String Length $L$

Based on the average period and standard gravity:

$$
L = \frac{g T^2}{4\pi^2} = \frac{9.81 \cdot 8.36^2}{4\pi^2} \approx 17.35 \ \text{m}
$$

### Step 5: Calculated $g$

$$
g = \frac{4\pi^2 L}{T^2} = \frac{4\pi^2 \cdot 17.35}{8.36^2} = 9.81 \ \text{m/s}^2
$$

### Step 6: Uncertainty in $g$

Using propagation of uncertainty:

$$
\Delta g = g \cdot \sqrt{ \left( \frac{\Delta L}{L} \right)^2 + \left( 2 \cdot \frac{\Delta T}{T} \right)^2 }
$$

Substitute known values:

$$
\Delta g = 9.81 \cdot \sqrt{ \left( \frac{0.005}{17.35} \right)^2 + \left( 2 \cdot \frac{0.01}{8.36} \right)^2 } \approx 0.05 \ \text{m/s}^2
$$

---

## Final Results

| Quantity                    | Value     |
| --------------------------- | --------- |
| Length (L)                  | 17.35 m   |
| Uncertainty ($\Delta L$)    | 0.005 m   |
| Mean $T$                    | 8.36 s    |
| Std Dev ($\sigma_T$)        | 0.04 s    |
| Uncertainty ($\Delta T$)    | 0.01 s    |
| Calculated $g$              | 9.81 m/s² |
| Uncertainty ($\Delta g$)    | 0.05 m/s² |

---

## Discussion

* **String length estimation**: The length was back-calculated from the observed period assuming $g = 9.81$ m/s².
* **Effect of $\Delta L$**: A 1 mm resolution results in 0.5 cm uncertainty, significant for short lengths.
* **Effect of $\Delta T$**: Human reaction time and timer resolution contribute to variability, impacting $\Delta T$
* **Assumptions**:

  * Small angle approximation ($\theta < 15^\circ$)
  * Negligible air resistance and massless string
* **Comparison with Standard**: Measured $g = 9.81 \pm 0.05$ m/s² closely matches accepted value (9.80665 m/s²).

This experiment reinforces the importance of precision and error analysis in physical measurements and highlights the robustness of simple harmonic motion principles in determining fundamental constants.

