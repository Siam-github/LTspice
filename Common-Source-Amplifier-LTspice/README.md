# Common-Source Amplifier Design & Analysis (LTspice)

![LTspice](https://img.shields.io/badge/Tool-LTspice-blue)
![Analog Design](https://img.shields.io/badge/Domain-Analog%20IC-red)
![Status](https://img.shields.io/badge/Status-Completed-success)
![License](https://img.shields.io/badge/License-MIT-green)

A simulation-driven comparative study of three **common-source (CS) amplifier** load configurations in LTspice, focusing on quantifying performance trade-offs in gain, output resistance, bandwidth, and voltage swing.

---

## Configurations Compared

| # | Load Type | Key Characteristic |
|---|-----------|-------------------|
| 1 | **PMOS Active Load** | Balanced gain, swing, and output resistance |
| 2 | **Diode-Connected Load** | Low Rout, high linearity, reduced gain |
| 3 | **Current Source Load** | Maximum gain via very high Rout |

---

## Core Design Equation

$$A_v = -g_m \cdot R_{out}$$

Where:
- $g_m$ — Transconductance of the NMOS driver
- $R_{out}$ — Effective output resistance of the load network

Gain is fundamentally a function of $R_{out}$. Load selection is therefore the primary design lever.

---

## Circuit Topologies

### 1. PMOS Active Load

```
      VDD
       |
    [PMOS]
       |
       +──── Vout
       |
    [NMOS]
       |
      GND
```

- Moderate output resistance ($R_{out} = r_{on} \| r_{op}$)
- Balanced gain and output swing
- Preferred for standard integrated analog designs

### 2. Diode-Connected Load

```
      VDD
       |
 [PMOS: Gate=Drain]
       |
       +──── Vout
       |
    [NMOS]
       |
      GND
```

- Low output resistance ($R_{out} \approx \frac{1}{g_{mp}}$)
- Reduced voltage gain, improved linearity
- Wider bandwidth due to lower pole time constant

### 3. Current Source Load

```
      VDD
       |
 [Ideal Current Source]
       |
       +──── Vout
       |
    [NMOS]
       |
      GND
```

- Very high output resistance ($R_{out} \approx r_{on}$)
- Maximum achievable voltage gain
- Limited voltage swing under low-supply constraints

---

## Simulation Setup

| Parameter | Value |
|-----------|-------|
| Supply Voltage (VDD) | 1.8 V |
| Technology | Generic CMOS |
| Analysis Types | DC sweep, AC response, Transient |
| MOSFET Models | BSIM3v3 (PTM 180 nm) |

Each configuration is simulated across three analysis types located in `simulations/dc/`, `simulations/ac/`, and `simulations/transient/`.

---

## Design Methodology

Biasing and sizing decisions follow a structured $g_m/I_D$ approach:

- NMOS kept in **saturation** across the operating range
- Target $g_m/I_D \approx 10\text{–}15\ \text{V}^{-1}$ for moderate inversion (balances gain and bandwidth)
- Load type directly controls $R_{out}$, which in turn sets gain and swing

Key design trade-offs:

- Higher $g_m$ → higher gain, but higher power consumption
- Lower $I_D$ → better efficiency, but reduced bandwidth
- Higher $R_{out}$ → higher gain, but narrower bandwidth (gain-bandwidth product is approximately conserved)

---

## Quantitative Results

| Configuration | Gain (dB) | Rout (kΩ) | Bandwidth (MHz) | Power (µW) |
|---------------|-----------|-----------|-----------------|------------|
| PMOS Load     | 18.2      | 45        | 12              | 120        |
| Diode Load    | 9.5       | 10        | 45              | 110        |
| Current Source Load | 32.7 | 120      | 5               | 130        |

---

## Engineering Insights

**1. Gain scales directly with output resistance.**
The current source load achieves ~3× higher $R_{out}$ compared to the PMOS load, translating directly to the dominant gain advantage.

**2. Bandwidth and gain trade inversely.**
The diode-connected load exhibits ~4× higher bandwidth due to its reduced output resistance lowering the output pole time constant ($\tau = R_{out} \cdot C_L$).

**3. PMOS load is the practical IC design choice.**
It offers the best compromise between gain, voltage swing, and compliance across process corners — making it the default choice in most integrated analog front-ends.

**4. Current source load is supply-constrained.**
Under 1.8 V and below, maintaining saturation for both the driver and the current source simultaneously limits the usable output swing, reducing its practical advantage.

**5. Gain efficiency favors current source.**
Current source load delivers the highest gain-per-µW, making it attractive in power-sensitive applications where swing constraints can be tolerated.

---

## Visual Results

> Simulation output plots are located in `results/` organized by topology.

| PMOS Load | Diode Load | Current Source Load |
|-----------|-----------|---------------------|
| `results/pmos_driver/dc_curve.png` | `results/diode_load/dc_curve.png` | `results/current_source_load/dc_curve.png` |
| `results/pmos_driver/gain_plot.png` | `results/diode_load/gain_plot.png` | `results/current_source_load/gain_plot.png` |
| `results/pmos_driver/waveform.png` | `results/diode_load/waveform.png` | `results/current_source_load/waveform.png` |

---

## Repository Structure

```
commonsource-amplifier-ltspice/
├── circuits/                  # LTspice schematics (.asc)
│   ├── pmos_driver/
│   ├── diode_load/
│   └── current_source_load/
├── netlists/                  # Extracted netlists (.cir)
├── simulations/               # Analysis setups (DC / AC / Transient)
│   ├── dc/
│   ├── ac/
│   └── transient/
├── models/                    # BSIM3v3 device models (.lib)
├── results/                   # Output plots per topology
├── analysis/                  # Hand calculations and comparisons (.md)
├── docs/                      # Theory and methodology
├── scripts/                   # Python plotting and data extraction
└── assets/                    # README visuals
```

---

## How to Run

1. Open any `.asc` file in LTspice (XVII or newer)
2. Confirm model paths in `models/` are correctly linked in the schematic
3. Run the desired analysis:
   - **DC sweep** — transfer curve and operating point
   - **AC analysis** — gain and phase vs. frequency
   - **Transient** — time-domain response to sinusoidal input
4. Export `.raw` data and use `scripts/data_extraction.py` to parse results
5. Use `scripts/plot_generation.py` to reproduce figures in `results/`

---

## Future Work

- [ ] Full $g_m/I_D$ methodology integration for systematic sizing
- [ ] Noise figure analysis (thermal + flicker noise per topology)
- [ ] Layout-aware parasitic extraction and post-layout simulation
- [ ] Corner analysis (FF, SS, SF, FS) for process robustness
- [ ] Supply sensitivity and PSRR characterization

---

## License

This project is licensed under the [MIT License](LICENSE).

---

## Author

**Md Masudun Nobi Siam**

This project is structured to reflect industry-grade analog design thinking — emphasizing not only simulation execution, but systematic insight generation and comparative performance analysis across load topologies.