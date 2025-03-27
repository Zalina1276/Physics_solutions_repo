# Problem 1
# Orbital Period and Orbital Radius

## Motivation
The relationship between the square of the orbital period and the cube of the orbital radius, known as **Kepler's Third Law**, is a fundamental principle in celestial mechanics. This law provides insights into planetary motions and gravitational interactions at various scales, from satellites orbiting Earth to exoplanetary systems in distant galaxies. Understanding this relationship allows us to determine planetary masses, distances, and orbital characteristics with high accuracy.

---

## Theoretical Derivation
Kepler's Third Law states that the square of the orbital period \(T\) is proportional to the cube of the semi-major axis (or radius \(r\) for circular orbits):

$$T^2 \propto r^3.$$

To derive this relationship from Newton's Laws and gravitational principles:

1. The gravitational force provides the necessary centripetal force for a body in circular orbit:

   $$F_g = \frac{G M m}{r^2}, \quad F_c = m \frac{v^2}{r}.$$

   Setting these equal to each other:

   $$\frac{G M m}{r^2} = m \frac{v^2}{r}.$$

2. The orbital velocity \( v \) is given by:

   $$v = \frac{2\pi r}{T}.$$

   Substituting into the force equation:

   $$\frac{G M}{r^2} = \frac{(2\pi r)^2}{T^2 r}.$$

3. Simplifying:

   $$T^2 = \frac{4\pi^2}{G M} r^3.$$

This confirms Kepler's Third Law, with the proportionality constant $\frac{4\pi^2}{G M}$.

## Astronomical Implications
This relationship is crucial in determining:

- The masses of celestial bodies by observing the orbital periods and radii of their satellites.

- The distances of exoplanets from their host stars.

- The orbital mechanics of artificial satellites.

**Examples:**

- The Moon’s orbit around Earth follows this law, allowing astronomers to estimate Earth’s mass.

- The planets in the Solar System follow this relationship, confirming Newtonian gravity.

## Computational Model

We implement a Python simulation to verify this relationship numerically.

### **Python Implementation: Kepler's Third Law Verification**

```python
import numpy as np
import matplotlib.pyplot as plt

# Constants
G = 6.67430e-11  # Gravitational constant (m^3 kg^-1 s^-2)
M = 1.989e30     # Mass of the Sun (kg)

# Define orbital radii (in meters) for simulation
radii = np.linspace(5e10, 1e12, 100)  # Range from 0.33 AU to ~6.7 AU

# Compute orbital periods using Kepler's Third Law
periods = np.sqrt((4 * np.pi**2 * radii**3) / (G * M))

# Plotting results
plt.figure(figsize=(8,6))
plt.plot(radii, periods**2, label='$T^2$ vs. $r^3$', color='blue')
plt.xlabel('Orbital Radius (m)')
plt.ylabel('Orbital Period Squared ($s^2$)')
plt.title('Kepler\'s Third Law Verification')
plt.legend()
plt.grid()
plt.show()
```

### **Additional Simulations**

#### **1. Comparison of Orbital Periods for Different Central Masses**
```python
# Varying central masses (e.g., Earth, Jupiter, Sun)
masses = [5.972e24, 1.898e27, 1.989e30]  # Earth, Jupiter, Sun
labels = ['Earth', 'Jupiter', 'Sun']
colors = ['red', 'green', 'blue']

plt.figure(figsize=(8,6))
for M, label, color in zip(masses, labels, colors):
    periods = np.sqrt((4 * np.pi**2 * radii**3) / (G * M))
    plt.plot(radii, periods**2, label=f'Central Mass: {label}', color=color)

plt.xlabel('Orbital Radius (m)')
plt.ylabel('Orbital Period Squared ($s^2$)')
plt.title('Orbital Period vs. Radius for Different Central Masses')
plt.legend()
plt.grid()
plt.show()
```

#### **2. Orbital Periods of Planets in the Solar System**
```python
# Data for planets (in meters and seconds)
planet_radii = [5.79e10, 1.08e11, 1.50e11, 2.28e11, 7.78e11, 1.43e12, 2.87e12, 4.50e12]
planet_periods = [7.6e6, 1.9e7, 3.2e7, 5.9e7, 3.7e8, 9.3e8, 2.7e9, 5.4e9]  # Approximate orbital periods
planet_names = ['Mercury', 'Venus', 'Earth', 'Mars', 'Jupiter', 'Saturn', 'Uranus', 'Neptune']

plt.figure(figsize=(8,6))
plt.scatter(planet_radii, np.array(planet_periods)**2, color='purple', label='Planets')
plt.xlabel('Orbital Radius (m)')
plt.ylabel('Orbital Period Squared ($s^2$)')
plt.title('Orbital Period vs. Radius for Solar System Planets')
for i, name in enumerate(planet_names):
    plt.annotate(name, (planet_radii[i], planet_periods[i]**2))
plt.legend()
plt.grid()
plt.show()
```

#### **3. Simulating a Satellite Orbit Around Earth**
```python
# Earth's mass
M_earth = 5.972e24  # kg

# Define orbital radii (e.g., low Earth orbit to geostationary orbit)
satellite_radii = np.linspace(7e6, 4.2e7, 100)  # From 700 km to 42,000 km altitude

# Compute orbital periods
satellite_periods = np.sqrt((4 * np.pi**2 * satellite_radii**3) / (G * M_earth))

plt.figure(figsize=(8,6))
plt.plot(satellite_radii, satellite_periods, label='Satellite Orbit', color='orange')
plt.xlabel('Orbital Radius (m)')
plt.ylabel('Orbital Period (s)')
plt.title('Satellite Orbital Period Around Earth')
plt.legend()
plt.grid()
plt.show()
```

### **Results & Discussion**

These additional plots illustrate:

1. How the central mass influences the orbital period.

2. The verification of Kepler’s Third Law using real planetary data.

3. The relationship between altitude and period for Earth-orbiting satellites.

## Extensions to Elliptical Orbits
While Kepler’s Third Law was originally formulated for elliptical orbits, the same principle holds when considering the **semi-major axis** $a$ instead of $r$. This allows astronomers to study binary star systems, exoplanets, and even entire galaxies.

### **Conclusion**
Kepler’s Third Law provides a fundamental link between gravity and planetary motion, offering critical insights into astrophysics and space exploration. Its computational verification further strengthens its role as a cornerstone of celestial mechanics.

All plots in: [Google Collab](https://colab.research.google.com/drive/1qLvtIVOvNFZVebJs_L2Bp4DgAH0eoSg_?usp=sharing)
