# Problem 2

# Escape Velocities and Cosmic Velocities  

## Introduction  

The ability to overcome a celestial body's gravitational influence is crucial for space exploration. Three significant velocity thresholds are:  

- **First Cosmic Velocity** ($v_1$): The velocity required to maintain a stable circular orbit around a celestial body.
- **Second Cosmic Velocity (Escape Velocity)** ($v_2$): The velocity required to completely escape the celestial body's gravitational field.
- **Third Cosmic Velocity** ($v_3$): The velocity required to escape the gravitational influence of the central star (e.g., the Sun).  

These velocities are fundamental in space mission planning, from launching satellites to interstellar travel.

---

## Mathematical Derivation  

### **First Cosmic Velocity ($v_1$) - Orbital Velocity**  

For a satellite in a circular orbit at radius $r$ from the center of a celestial body of mass $M$, the gravitational force provides the required centripetal force:  

$$ \frac{G M m}{r^2} = \frac{m v_1^2}{r} $$

Solving for $v_1$:  

$$ v_1 = \sqrt{\frac{G M}{r}} $$

### **Second Cosmic Velocity ($v_2$) - Escape Velocity**  

Escape velocity is derived from energy conservation. A body starting at $r$ with velocity $v_2$ should reach infinity with zero kinetic energy:  

$$ \frac{1}{2} m v_2^2 - \frac{G M m}{r} = 0 $$

Solving for $v_2$:  

$$ v_2 = \sqrt{\frac{2 G M}{r}} $$

### **Third Cosmic Velocity ($v_3$) - Solar System Escape Velocity**  

To escape the Sun’s gravitational pull from a planet, we use:  

$$ v_3 = \sqrt{v_2^2 + v_{\text{orb}}^2} $$

where $v_{\text{orb}}$ is the planet’s orbital velocity around the Sun:  

$$ v_{\text{orb}} = \sqrt{\frac{G M_{s}}{R}} $$

where $M_{s}$ is the Sun’s mass and $R$ is the planet’s distance from the Sun.

---

## Calculations for Earth, Mars, and Jupiter 

Using standard values:  
- Gravitational constant: $G = 6.674 \times 10^{-11} \, \text{m}^3 \text{kg}^{-1} \text{s}^{-2}$  
- Earth: $M_E = 5.972 \times 10^{24}$ kg, $R_E = 6371 \times 10^3$ m  
- Mars: $M_M = 6.417 \times 10^{23}$ kg, $R_M = 3389 \times 10^3$ m  
- Jupiter: $M_J = 1.898 \times 10^{27}$ kg, $R_J = 69911 \times 10^3$ m  

We compute:

$$ v_{1E} = \sqrt{\frac{G M_E}{R_E}} $$

$$ v_{2E} = \sqrt{2} v_{1E} $$

$$ v_{3E} = \sqrt{v_{2E}^2 + v_{\text{orbE}}^2} $$

Similar calculations follow for Mars and Jupiter.

### **Conditions Analysis**

1. **Dependence on Mass and Radius**: Higher mass increases gravitational pull, requiring higher velocities. Larger radius reduce the required velocity due to weaker surface gravity.
2. **Energy Considerations**: Escape velocity is derived by equating kinetic and gravitational potential energy.
3. **Planetary Comparisons**: Different planets have different escape velocities depending on their mass and radius.

---

## Python Calculation & Visualization

![alt text](image-5.png)

---

## Importance in Space Exploration  

**1.Satellite Deployment:**  

   - First cosmic velocity determines stable orbits.  
   - Used for communications, weather, and research satellites.  

**2.Interplanetary Missions:**  

   - Second cosmic velocity allows escape to other planets.  
   - Used for Mars rovers and deep-space probes.  

**3.Interstellar Travel:**  

   - Third cosmic velocity enables missions beyond the solar system.  
   - Future missions (e.g., Breakthrough Starshot) aim to reach this velocity.  

---

## Conclusion

The concept of cosmic velocities is fundamental to space travel, defining the energy requirements for various missions. Understanding these velocities helps optimize spacecraft design and mission planning, leading to efficient exploration of the cosmos.

All plot codes in: [Google Collab](https://colab.research.google.com/drive/1qLvtIVOvNFZVebJs_L2Bp4DgAH0eoSg_?usp=sharing)
