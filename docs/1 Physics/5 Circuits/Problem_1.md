# Problem 1

# Equivalent Resistance Using Graph Theory 


# Circuit Simplification: Visualizing Equivalent Resistance

##  Goal

To demonstrate how the **equivalent resistance** of a circuit evolves as we **remove one resistor at a time**, while adjusting values of remaining resistors to preserve or compare $R_{\text{eq}}$.

---

## Initial Circuit

Let’s consider a resistor network:

This means:
- $R_1$ is in series with the **parallel combination** of $R_2$ and $R_3$.

---

### Step 1: Calculate Initial $R_{\text{eq}}$

We start by calculating the parallel combination:

$$
R_{23} = \left( \frac{1}{R_2} + \frac{1}{R_3} \right)^{-1}
= \left( \frac{1}{20} + \frac{1}{30} \right)^{-1}
= \left( \frac{5}{60} \right)^{-1} = 12 \, \Omega
$$

Then the total equivalent resistance:

$$
R_{\text{eq}} = R_1 + R_{23} = 10 + 12 = 22 \, \Omega
$$

---

## Step 2: Remove $R_3$, Adjust $R_2$

We now **delete $R_3$** and **replace $R_2$ with 12Ω** to preserve $R_{\text{eq}}$.

$$A ── R₁ = 10Ω ── R₂ = 12Ω ── B$$


Now the circuit is just two resistors in series:

$$
R_{\text{eq}} = R_1 + R_2 = 10 + 12 = 22 \, \Omega
$$

**Same result, simpler structure**

---

## Step 3: Remove $R_2$, Adjust $R_3$

Let’s try the opposite: **remove $R_2$** and set $R_3 = 12Ω$:

$$
A ── R₁ = 10Ω ── R₃ = 12Ω ── B
$$

Again:

$$
R_{\text{eq}} = 10 + 12 = 22 \, \Omega
$$

**Same behavior**, different configuration.

---

## Insight

This process shows that:

Different resistor combinations can be **equivalent**, as long as we correctly adjust the values and structure.

This is exactly what **graph-based circuit analysis** helps us do — systematically simplify and compare circuits.

---

Python implementations are in [Collab](https://colab.research.google.com/drive/12GTBwiNby3IxKENQUjtxPdjeVxnk3_vg?usp=sharing)

  ![alt text](step1.png)

  ![alt text](step2.png) 

 ![alt text](step3.png)

 ![alt text](step4.png)

 ![alt text](final.png)