# Common Source Amplifier Configurations

This document provides a technical overview of Common Source (CS) amplifier configurations, focusing on the comparison between passive (resistor) loads and active loads (MOSFETs/Current Mirrors) in integrated circuit design.

## What is an Active Load?

In MOSFET amplifier circuits, an **Active Load** uses an active component (like another MOSFET or a current mirror) instead of a passive resistor to increase the amplifier's gain.

![Fig. 1 MOSFET Amplifier with Active Load](figures\Fig.1 MOSFET Amplifier with Active Load.png)

## Why Use an Active Load?

Active loads are primarily used in integrated circuits where size and power consumption are major constraints. Key benefits include:

- **Space Efficiency:** Fabricating resistors in ICs requires a lot of space. Active loads (MOSFETs) are much smaller.
- **Higher Voltage Gain:** Active loads significantly increase the amplifier's voltage gain without requiring large supply voltages.
- **Smaller Voltage Drop:** Unlike resistors, active loads have a small drain-to-source saturation voltage (≈100–200mV), keeping the MOSFET in saturation even with low supply voltages.

### Gain Limitations with Passive Loads

For a simple CS amplifier with a passive (resistive) load:

```math
	|Av| = gm * (RD || r0)
	If r0 >> RD , then |Av| ≈ gm * RD
```





To increase gain, you would typically increase `RD` or `gm`. However:

- **Increasing `RD`** increases the voltage drop across it, reducing the drain voltage. The MOSFET may leave saturation.
- **Increasing `ID`** (to increase `gm`) increases power dissipation and also increases voltage drop across `RD`.
- **Increasing supply voltage** is not practical in modern ICs where supply voltages are shrinking.

**Active loads eliminate these problems.**

## Comparison: Passive Load vs. Active Load

| Feature                  | Passive (Resistor)                     | Active (MOSFET)                               |
| ------------------------ | -------------------------------------- | --------------------------------------------- |
| **Element type**         | Non-amplifying, dissipative            | Has its own gm, can amplify                  |
| **Small-signal impedance** | Fixed = RD                            | Very high: r0 = 1 / (λ * ID)                   |
| **DC voltage drop**      | Large (ID × RD)                        | Small (VDS,sat ≈ 100–200mV)                   |
| **Gain achievable**      | Moderate (~10–30)                      | Very high (~100–1000)                         |
| **Used in**              | Discrete, RF, simple stages            | All VLSI/IC op-amps, OTAs                    |
| **Power efficiency**     | Low                                    | High                                          |

## Summary

- **Passive loads** are simple and suitable for discrete or RF designs but suffer from gain limitations and large voltage drops.
- **Active loads** (using MOSFETs or current mirrors) are essential for modern VLSI and analog IC design. They provide:
  - High small-signal impedance
  - Low DC voltage drop
  - Very high achievable gain
  - Better power efficiency

## License

This README is based on the provided educational material for reference and learning purposes.