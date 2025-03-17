# Problem 2

<span style="font-size: 1.2em; font-weight: bold;">Analyzing the Motion of a Simple Pendulum</span>

#### Motivation:

The forced damped pendulum is a captivating example of a physical system with intricate behavior resulting from the interplay of damping, restoring forces, and external driving forces. By introducing both damping and external periodic forcing, the system demonstrates a transition from simple harmonic motion to a rich spectrum of dynamics, including resonance, chaos, and quasiperiodic behavior. These phenomena serve as a foundation for understanding complex real-world systems, such as driven oscillators, climate systems, and mechanical structures under periodic stress.

Adding forcing introduces new parameters, such as the amplitude and frequency of the external force, which significantly affect the pendulum's behavior. By systematically varying these parameters, a diverse class of solutions can be observed, including synchronized oscillations, chaotic motion, and resonance phenomena. These behaviors not only highlight fundamental physics principles but also provide insights into engineering applications such as energy harvesting, vibration isolation, and mechanical resonance.

#### Task:

- Derive the equation of motion for a simple pendulum.
- Investigate the period of oscillation as a function of amplitude.
- Examine the effects of damping and external driving forces.
#### Deliverables:
- Equations governing pendulum motion.
- Plots showing period versus amplitude.
- Analysis of damping and resonance phenomena.
#### Hints and Resources:
- Apply small-angle approximations for linear analysis.
- Use numerical methods for non-linear and damped cases.

## Solution

### 1. Deriving the Equation of Motion

A simple pendulum consists of a **mass** $m$ attached to a string of length $L$, singing under gravity. The forces acting on the mass are:

- Tension in the string (which does not contribute to angular motion)
- The gravitational force $mg$

Using Newton's Second Law for rotational motion: 

$$
\sum \tau = I\alpha
$$

where:
- $\tau$ = $-mgLsin\theta$ is the torque due to gravity
- $I=mL^2$ is the moment of inertia 
- $\alpha=\frac{d^2\theta}{dt^2}$ is the angular acceleration

Thus, the equation of motion is:

$$mL^2\frac{d^2\theta}{dt^2}=-mgLsin\theta$$ 

Dividing by $mL^2$:

$$\frac{d^2\theta}{dt^2}+\frac{g}{L}sin\theta=0$$ 

#### Small-Angle Approximation ($sin\theta \approx \theta$)

For small oscillations $(\theta<<1)$, we approximate $sin\theta \approx \theta$, giving:

$$\frac{d^2\theta}{dt^2}+\frac{g}{L}\theta=0$$

This is a simple harmonic oscillator equation with the solution:

$$\theta(t)=\theta_0 cos(\sqrt{\frac{g}{L}}t +\phi)$$

where $\omega_0 = \sqrt{\frac{g}{L}}$ is the **natural frequency**, and the period is: 

$$T=2\pi\sqrt{\frac{L}{g}}$$ 

### 2. Period as a Function of Amplitude 

For larger angles, the small-angle approximation is invalid. The exact period is:

$$T=4\sqrt{\frac{L}{g}} \int^{\pi/2}_0 \frac{d\phi}{\sqrt{1-k^2sin^2\phi}}$$

wwhere $k=sin(\theta_0/2)$. This requires elliptic integrals. 

#### Nummerical Simulation of Nonlinear Period

We can compute the period numerrically for larger amplitudes. 

```python

import numpy as np
import matplotlib.pyplot as plt
from scipy.integrate import quad

# Define constants
L = 1.0  # Length of pendulum in meters
g = 9.81  # Gravity in m/s^2

# Function for integral
def integral(phi, k):
    return 1 / np.sqrt(1 - k**2 * np.sin(phi)**2)

# Compute period for different amplitudes
theta_0_values = np.linspace(0, np.pi/2, 50)  # Amplitudes from 0 to 90 degrees
T_values = []

for theta_0 in theta_0_values:
    k = np.sin(theta_0 / 2)
    T_exact = 4 * np.sqrt(L / g) * quad(integral, 0, np.pi/2, args=(k,))[0]
    T_values.append(T_exact)

# Plot results
plt.plot(theta_0_values * 180 / np.pi, T_values, label="Nonlinear Period")
plt.axhline(2*np.pi*np.sqrt(L/g), color='r', linestyle='--', label="Small-angle Approximation")
plt.xlabel("Initial Amplitude (degrees)")
plt.ylabel("Period (s)")
plt.title("Pendulum Period vs. Initial Amplitude")
plt.legend()
plt.grid()
plt.show()

```

**Observations**
- For small amplitudes, the period remains constant. 
- For larger amplitudes, the period increases due to nonlinearity. 

### 3. Effects of Damping and Driving Forces

In real-world cases, air resistance and friction introduce **damping**, while periodic forces can drive the pendulum. 

#### Damped Pendulum 

Adding a damping term $b$, the equation becomes: 

$$\frac{d^2\theta}{dt^2}+\frac{b}{m} \frac{d\theta}{dt}+\frac{g}{L} \sin\theta = 0$$

For small damping, the solution is:

$$\theta(t)=\theta_0e^{-\gamma T}cos(\omega_d t)$$

where $\gamma=\frac{b}{2m}$ and $\omega_d = \sqrt{\frac{g}{L} - \gamma^2}$

#### Driven Pendulum (Forced Oscillations)

With an external force $F_0cos(\omega t)$, the equation is:

$$\frac{d^2\theta}{dt^2}+\frac{b}{m} \frac{d\theta}{dt}+\frac{g}{L} \sin\theta = \frac{F_0}{mL}cos(\omega t)$$
 
This system exhibits **resonance** when the driving frequency matches the natural frequency $\omega_0$

#### Nummerical Simulation of Damped and Driven Pendulum 

A numerical solution is needed for solving nonlinear, damped, and driven cases. Using **Runge-Kutta** integration:

```python
from scipy.integrate import solve_ivp

# Parameters
b = 0.1  # Damping coefficient
F0 = 0.2  # Driving force
omega_drive = 2.0  # Driving frequency

# Define the system of ODEs
def pendulum_eqs(t, y):
    theta, omega = y
    dtheta_dt = omega
    domega_dt = - (g/L) * np.sin(theta) - b * omega + F0 * np.cos(omega_drive * t)
    return [dtheta_dt, domega_dt]

# Solve for time evolution
t_span = (0, 20)  # Time interval
y0 = [np.pi/4, 0]  # Initial conditions (45 degrees, zero velocity)
t_eval = np.linspace(0, 20, 1000)  # Time points

sol = solve_ivp(pendulum_eqs, t_span, y0, t_eval=t_eval)

# Plot results
plt.plot(sol.t, sol.y[0], label="Damped & Driven Motion")
plt.xlabel("Time (s)")
plt.ylabel("Angle (radians)")
plt.title("Damped & Driven Pendulum Motion")
plt.legend()
plt.grid()
plt.show()

```

| Case | Equation | Observation |
|------|----------|-------------|
|Simple Pendulum (Small Angles)|$T=2\pi \sqrt{L/g}$|Period is constant|
|Nonlinear Case (Large Angles)|$T=4\sqrt{L/g}\int^{\pi/2}_0 \frac{d\phi}{\sqrt{1-k^2 sin^2\phi}}$|Period increases with amplitude|
|Damped Pendulum|$\theta=\theta_0e^{-\gamma t}cos(\omega_dt)$|Oscillations decay over time|
|Driven Pendulum|$\frac{d^2\theta}{dt^2}+\frac{b}{m}\frac{d\theta}{dt}+\frac{g}{L}sin\theta=\frac{F_0}{mL}cos(\omega t)$|Resonance occurs when $\omega \approx \omega_0$|

### Final Thoughts

- The simple pendulum follows a harmonic motions for **small angles**
- For **large amplitudes**, the period **increases** non-linearly
- **Damping** leads to decay. while **driving forces** introduces resonance
- **Numerical methods** help  solve the **nonlinear and forced cases** 