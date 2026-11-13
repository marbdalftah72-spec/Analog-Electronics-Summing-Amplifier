# ⚡ Dual-Sign Summing Amplifier & Operational Amplifier Analog Circuit Design

[![Domain](https://img.shields.io/badge/Domain-Analog%20Circuits%20%7C%20Electronics-brightgreen.svg)](#)
[![Simulation](https://img.shields.io/badge/Simulation-Proteus%20%7C%20Multisim-blue.svg)](#)
[![IC](https://img.shields.io/badge/Op--Amp-LM741%20%7C%20TL081-red.svg)](#)
[![License](https://img.shields.io/badge/License-MIT-green.svg)](LICENSE)

Design, mathematical derivation, simulation, and hardware verification of an **Operational Amplifier (Op-Amp) Summing Amplifier Circuit supporting simultaneous positive and negative input voltage summation**. 

Authored by **Ammar Abdelfattah** for the **Electronics & Analog Circuits** course at **Faculty of Engineering – New Ismailia National University (NINU)**.

---

## 📌 Mathematical Circuit Analysis & Derivations

In standard analog computing and audio signal mixing, an inverting summing amplifier produces an output proportional to the inverted weighted sum of its inputs:
$$V_{\text{out}} = - R_f \sum_{i=1}^n \frac{V_i}{R_i}$$

To achieve **both positive and negative coefficients** simultaneously without requiring a separate external inverting stage, this project analyzes and implements a **Balanced Differential Summing Amplifier** topology utilizing both the inverting ($-$) and non-inverting ($+$) inputs of a single Op-Amp (LM741 / TL071):

```text
               R1
 V_pos1 o----/\/\/\----+
                       |
               R2      |
 V_pos2 o----/\/\/\----+--------(+)
                       |          |
                      [R_p]       |
                       |          |
                      GND         |
                                  |-----\
                                  |      )----o V_out
                                  |-----/
                       +--------(-)
               R3      |          |
 V_neg1 o----/\/\/\----+          |
                       |          |
               Rf      |          |
         +---/\/\/\----+          |
         |                        |
         +------------------------+
```

### Mathematical Transfer Function:
Applying Kirchhoff's Current Law (KCL) at the inverting node $V_-$ and non-inverting node $V_+$, coupled with the virtual short approximation ($V_+ = V_-$):

1. **Inverting Node KCL**:
   $$\frac{V_{\text{neg}} - V_-}{R_3} + \frac{V_{\text{out}} - V_-}{R_f} = 0$$
2. **Non-Inverting Node KCL**:
   $$\frac{V_{\text{pos}} - V_+}{R_1} = \frac{V_+}{R_p}$$
3. **Combined Output Transfer Function**:
   $$V_{\text{out}} = \left( 1 + \frac{R_f}{R_3} \right) \left( \frac{R_p}{R_1 + R_p} \right) V_{\text{pos}} - \left( \frac{R_f}{R_3} \right) V_{\text{neg}}$$

By tuning the resistor matching condition such that:
$$\left( 1 + \frac{R_f}{R_3} \right) \left( \frac{R_p}{R_1 + R_p} \right) = \frac{R_f}{R_3} = K$$

The circuit reduces to an exact subtraction and addition engine:
$$V_{\text{out}} = K (V_{\text{pos}} - V_{\text{neg}})$$

---

## 🔬 Experimental Validation & Multi-Signal Testing

- **Gain Accuracy**: Evaluated with precision $1\%$ metal-film resistors.
- **Common-Mode Rejection Ratio (CMRR)**: Measured across frequencies from $10\text{ Hz}$ to $50\text{ kHz}$.
- **Clipping Limits**: Analyzed under dual supply voltages $\pm 15\text{V DC}$, exhibiting linear operation up to $\pm 13.5\text{V}$.

---

## 📁 Repository Contents

- `schematics/circuit_diagram.pdf`: High-resolution circuit schematic.
- `simulation/summing_amp.ms14`: Multisim / Proteus simulation file.
- `documentation/analog_derivation_report.pdf`: Detailed analytical proof and oscilloscope trace captures.
- `README.md`: Technical overview.

---

## 👨‍💻 Author

- **Ammar Abdelfattah**
- Faculty of Engineering, **New Ismailia National University (NINU)**
