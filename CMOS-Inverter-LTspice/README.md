# 🔷 CMOS Inverter Design using LTspice

![LTspice](https://img.shields.io/badge/Tool-LTspice-blue)
![VLSI](https://img.shields.io/badge/Domain-VLSI-green)
![Status](https://img.shields.io/badge/Project-Completed-brightgreen)

---

## 📌 Overview

This project presents the design and analysis of a CMOS inverter using LTspice. The work includes DC, AC, and transient analysis along with propagation delay and power consumption evaluation.

---

## ⚙️ Tools & Technologies

* LTspice
* CMOS PTM Models
* Analog VLSI Design Concepts

---

## 🧠 Design Methodology

### gm/Id-Based Sizing

The transistor sizing is performed using the gm/Id methodology to achieve an optimal trade-off between speed and power.

* Target region: Moderate inversion (gm/Id ≈ 15)
* NMOS width: 1 µm
* PMOS width: 2 µm
* Reason: Mobility ratio compensation for symmetric switching

---

## 🔌 Circuit Description

* CMOS inverter using NMOS and PMOS
* Supply Voltage: 1.8V
* Load Capacitance: 10fF

---

## 📊 Simulations Performed

### ✅ DC Analysis

* Voltage Transfer Characteristics (VTC)
* Switching Threshold (VM)

### ✅ AC Analysis

* Gain
* Bandwidth

### ✅ Transient Analysis

* Switching behavior
* Propagation delay measurement

---

## ⏱️ Propagation Delay

[
t_p = \frac{t_{PLH} + t_{PHL}}{2}
]

Measured using LTspice `.measure` commands.

---

## ⚡ Power Consumption

[
P = V_{DD} \times I_{avg}
]

Includes both dynamic and static power components.

---

## 📈 Results

| Parameter         | Value |
| ----------------- | ----- |
| VDD               | 1.8V  |
| Propagation Delay | XX ps |
| Power Consumption | XX µW |
| Gain              | XX    |

---

## 🖼️ Figures

### CMOS Inverter Schematic

![schematic](figures/schematic.png)

### Transient Response

![waveform](results/transient_waveform.png)

---

## 📂 Project Structure

```
models/
circuits/
simulations/
results/
calculations/
figures/
```

---

## 🚀 Future Work

* Layout design (Magic / Sky130)
* Parasitic extraction
* Monte Carlo analysis

---

## 👤 Author

**Md. Masudun Nabi Siam**
EEE, GSTU
Aspiring Analog & Mixed-Signal VLSI Engineer

---
