\# Common Source Amplifier Configurations



\## Overview

There are multiple design configurations for a \*\*Common Source (CS) amplifier\*\*.

The primary design decisions involve:

\- Drain load selection

\- Biasing network design



\---



\## What is an Active Load?



In MOSFET amplifier circuits, instead of using a passive resistor, an \*\*active component\*\* (such as a MOSFET or a current mirror) is used to enhance amplifier performance.



This active element is referred to as an \*\*Active Load\*\*.



\---



\## Why Use an Active Load?



Active loads are widely used in \*\*integrated circuits (ICs)\*\* due to:



\- \*\*Area efficiency\*\*: Resistors consume large silicon area

\- \*\*Power efficiency\*\*: Lower voltage drop compared to resistors

\- \*\*Higher gain capability\*\*



\---



\## Gain Limitation in Passive Load CS Amplifier



For a basic CS amplifier: \\(A\_v ≈ -g\_m \* R\_D\\)



\### Limitations:



\#### 1. Increasing \\( R\_D \\)

\- Increases gain

\- But also increases voltage drop \\( (I\_D \\cdot R\_D) \\)

\- Reduces available drain voltage

\- May push MOSFET out of saturation



\#### 2. Increasing \\( I\_D \\)

\- Increases transconductance \\( g\_m \\)

\- Leads to higher power dissipation

\- Increases voltage drop across \\( R\_D \\)

\- Again risks leaving saturation region



\#### 3. Increasing Supply Voltage

\- Helps maintain saturation

\- Not feasible in modern IC design (low-voltage constraints)



\---



\## Solution: Active Load



Active loads eliminate these limitations by:

\- Providing \*\*high output resistance\*\*

\- Maintaining \*\*low voltage drop\*\*

\- Enabling \*\*high gain without large power penalties\*\*



\---



\## Passive vs Active Load Comparison



| Feature                | Passive Load (Resistor)     | Active Load (MOSFET)        |

|----------------------|-----------------------------|-----------------------------|

| Element Type         | Non-amplifying, dissipative | Has intrinsic gain (gₘ)     |

| Small-Signal Impedance | Fixed = \\( R\_D \\)          | Very high: \\( r\_o = 1 / (\\lambda I\_D) \\) |

| DC Voltage Drop      | Large \\( (I\_D \\cdot R\_D) \\) | Small \\( V\_{DS,sat} \\approx 100–200mV \\) |

| Gain Achievable      | Moderate (\~10–30)           | Very high (\~100–1000)       |

| Typical Use          | Discrete / simple circuits  | VLSI, Op-Amps, OTAs         |

| Power Efficiency     | Low                         | High                        |



\---



\## Key Insight



> Active loads are fundamental to modern analog IC design because they enable \\\*\\\*high gain, compact layout, and power-efficient operation\\\*\\\*.

