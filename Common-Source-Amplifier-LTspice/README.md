# \# Common-Source Amplifier Design \& Analysis (LTspice)

# 

# !\[LTspice](https://img.shields.io/badge/Tool-LTspice-blue)

# !\[Analog Design](https://img.shields.io/badge/Domain-Analog%20IC-red)

# !\[Status](https://img.shields.io/badge/Status-Completed-success)

# !\[License](https://img.shields.io/badge/License-MIT-green)

# 

# A simulation-driven comparative study of three \*\*common-source (CS) amplifier\*\* load configurations in LTspice, focusing on quantifying performance trade-offs in gain, output resistance, bandwidth, and voltage swing.

# 

# \---

# 

# \## Configurations Compared

# 

# | # | Load Type | Key Characteristic |

# |---|-----------|-------------------|

# | 1 | \*\*PMOS Active Load\*\* | Balanced gain, swing, and output resistance |

# | 2 | \*\*Diode-Connected Load\*\* | Low Rout, high linearity, reduced gain |

# | 3 | \*\*Current Source Load\*\* | Maximum gain via very high Rout |

# 

# \---

# 

# \## Core Design Equation

# 

# $$A\_v = -g\_m \\cdot R\_{out}$$

# 

# Where:

# \- $g\_m$ — Transconductance of the NMOS driver

# \- $R\_{out}$ — Effective output resistance of the load network

# 

# Gain is fundamentally a function of $R\_{out}$. Load selection is therefore the primary design lever.

# 

# \---

# 

# \## Circuit Topologies

# 

# \### 1. PMOS Active Load

# 

# ```

# &#x20;     VDD

# &#x20;      |

# &#x20;   \[PMOS]

# &#x20;      |

# &#x20;      +──── Vout

# &#x20;      |

# &#x20;   \[NMOS]

# &#x20;      |

# &#x20;     GND

# ```

# 

# \- Moderate output resistance ($R\_{out} = r\_{on} \\| r\_{op}$)

# \- Balanced gain and output swing

# \- Preferred for standard integrated analog designs

# 

# \### 2. Diode-Connected Load

# 

# ```

# &#x20;     VDD

# &#x20;      |

# &#x20;\[PMOS: Gate=Drain]

# &#x20;      |

# &#x20;      +──── Vout

# &#x20;      |

# &#x20;   \[NMOS]

# &#x20;      |

# &#x20;     GND

# ```

# 

# \- Low output resistance ($R\_{out} \\approx \\frac{1}{g\_{mp}}$)

# \- Reduced voltage gain, improved linearity

# \- Wider bandwidth due to lower pole time constant

# 

# \### 3. Current Source Load

# 

# ```

# &#x20;     VDD

# &#x20;      |

# &#x20;\[Ideal Current Source]

# &#x20;      |

# &#x20;      +──── Vout

# &#x20;      |

# &#x20;   \[NMOS]

# &#x20;      |

# &#x20;     GND

# ```

# 

# \- Very high output resistance ($R\_{out} \\approx r\_{on}$)

# \- Maximum achievable voltage gain

# \- Limited voltage swing under low-supply constraints

# 

# \---

# 

# \## Simulation Setup

# 

# | Parameter | Value |

# |-----------|-------|

# | Supply Voltage (VDD) | 1.8 V |

# | Technology | Generic CMOS |

# | Analysis Types | DC sweep, AC response, Transient |

# | MOSFET Models | BSIM3v3 (PTM 180 nm) |

# 

# Each configuration is simulated across three analysis types located in `simulations/dc/`, `simulations/ac/`, and `simulations/transient/`.

# 

# \---

# 

# \## Design Methodology

# 

# Biasing and sizing decisions follow a structured $g\_m/I\_D$ approach:

# 

# \- NMOS kept in \*\*saturation\*\* across the operating range

# \- Target $g\_m/I\_D \\approx 10\\text{–}15\\ \\text{V}^{-1}$ for moderate inversion (balances gain and bandwidth)

# \- Load type directly controls $R\_{out}$, which in turn sets gain and swing

# 

# Key design trade-offs:

# 

# \- Higher $g\_m$ → higher gain, but higher power consumption

# \- Lower $I\_D$ → better efficiency, but reduced bandwidth

# \- Higher $R\_{out}$ → higher gain, but narrower bandwidth (gain-bandwidth product is approximately conserved)

# 

# \---

# 

# \## Quantitative Results

# 

# | Configuration | Gain (dB) | Rout (kΩ) | Bandwidth (MHz) | Power (µW) |

# |---------------|-----------|-----------|-----------------|------------|

# | PMOS Load     | 18.2      | 45        | 12              | 120        |

# | Diode Load    | 9.5       | 10        | 45              | 110        |

# | Current Source Load | 32.7 | 120      | 5               | 130        |

# 

# \---

# 

# \## Engineering Insights

# 

# \*\*1. Gain scales directly with output resistance.\*\*

# The current source load achieves \~3× higher $R\_{out}$ compared to the PMOS load, translating directly to the dominant gain advantage.

# 

# \*\*2. Bandwidth and gain trade inversely.\*\*

# The diode-connected load exhibits \~4× higher bandwidth due to its reduced output resistance lowering the output pole time constant ($\\tau = R\_{out} \\cdot C\_L$).

# 

# \*\*3. PMOS load is the practical IC design choice.\*\*

# It offers the best compromise between gain, voltage swing, and compliance across process corners — making it the default choice in most integrated analog front-ends.

# 

# \*\*4. Current source load is supply-constrained.\*\*

# Under 1.8 V and below, maintaining saturation for both the driver and the current source simultaneously limits the usable output swing, reducing its practical advantage.

# 

# \*\*5. Gain efficiency favors current source.\*\*

# Current source load delivers the highest gain-per-µW, making it attractive in power-sensitive applications where swing constraints can be tolerated.

# 

# \---

# 

# \## Visual Results

# 

# > Simulation output plots are located in `results/` organized by topology.

# 

# | PMOS Load | Diode Load | Current Source Load |

# |-----------|-----------|---------------------|

# | `results/pmos\_driver/dc\_curve.png` | `results/diode\_load/dc\_curve.png` | `results/current\_source\_load/dc\_curve.png` |

# | `results/pmos\_driver/gain\_plot.png` | `results/diode\_load/gain\_plot.png` | `results/current\_source\_load/gain\_plot.png` |

# | `results/pmos\_driver/waveform.png` | `results/diode\_load/waveform.png` | `results/current\_source\_load/waveform.png` |

# 

# \---

# 

# \## Repository Structure

# 

# ```

# commonsource-amplifier-ltspice/

# ├── circuits/                  # LTspice schematics (.asc)

# │   ├── pmos\_driver/

# │   ├── diode\_load/

# │   └── current\_source\_load/

# ├── netlists/                  # Extracted netlists (.cir)

# ├── simulations/               # Analysis setups (DC / AC / Transient)

# │   ├── dc/

# │   ├── ac/

# │   └── transient/

# ├── models/                    # BSIM3v3 device models (.lib)

# ├── results/                   # Output plots per topology

# ├── analysis/                  # Hand calculations and comparisons (.md)

# ├── docs/                      # Theory and methodology

# ├── scripts/                   # Python plotting and data extraction

# └── assets/                    # README visuals

# ```

# 

# \---

# 

# \## How to Run

# 

# 1\. Open any `.asc` file in LTspice (XVII or newer)

# 2\. Confirm model paths in `models/` are correctly linked in the schematic

# 3\. Run the desired analysis:

# &#x20;  - \*\*DC sweep\*\* — transfer curve and operating point

# &#x20;  - \*\*AC analysis\*\* — gain and phase vs. frequency

# &#x20;  - \*\*Transient\*\* — time-domain response to sinusoidal input

# 4\. Export `.raw` data and use `scripts/data\_extraction.py` to parse results

# 5\. Use `scripts/plot\_generation.py` to reproduce figures in `results/`

# 

# \---

# 

# \## Future Work

# 

# \- \[ ] Full $g\_m/I\_D$ methodology integration for systematic sizing

# \- \[ ] Noise figure analysis (thermal + flicker noise per topology)

# \- \[ ] Layout-aware parasitic extraction and post-layout simulation

# \- \[ ] Corner analysis (FF, SS, SF, FS) for process robustness

# \- \[ ] Supply sensitivity and PSRR characterization

# 

# \---

# 

# \## License

# 

# This project is licensed under the \[MIT License](LICENSE).

# 

# \---

# 

# \## Author

# 

# \*\*Md Masudun Nobi Siam\*\*

# 

# This project is structured to reflect industry-grade analog design thinking — emphasizing not only simulation execution, but systematic insight generation and comparative performance analysis across load topologies.

