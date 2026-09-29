---
title: "Basic MOS Controlled Sources"
classes: wide
toc: true
toc_label: "Contents"
---

There are four kinds of controlled sources, namely the voltage-controlled current source (VCCS), voltage-controlled voltage source (VCVS), current-controlled current source (CCCS), and current-controlled voltage source (CCVS). The circuit including a controlled source is shown in Fig. 1 below, where the MOS controlled source is modelled as a two-port network, with a common terminal between the input and output ports for simplicity. The best we can do with a single MOS transistor is to create an incremental controlled source with a maximum gain of 1 (for a VCVS or a CCCS).

<div style="text-align: center; margin: 25px 0;">
  <img src="/assets/images/wiki/ctrl_src_block_diag.svg" alt="MOS ctrl src block" style="max-height: auto; width: auto; display: block; margin: 0 auto;" />
  <p style="font-style: italic; font-size: 0.9em; color: #555; margin-top: 10px;">
    Figure 1: MOS controlled source with voltage input (left) and current input (right).
  </p>
</div>

## Input and Output Impedances 

Table 1 below shows the ideal input and output resistances desired from a controlled source. If a source is voltage-controlled, then it is measuring or sensing a voltage at its input, so you want all of $v_\text{in}$ to appear at the input terminals of the controlled source. Therefore, it's best to have $R_\text{in} \to \infty$ to avoid loading the voltage source and dropping some fraction of $v_\text{in}$ across $R_g$. However, if a source is current-controlled, then it is sensing a current at its input, so you want all of $i_\text{in}$ to pass through the input terminals of the controlled source. Therefore, it's best to have $R_\text{in} \to 0$, which essentially shorts the internal resistance $R_g$ of the source, ensuring that none of $i_\text{in}$ passes through it.

<div markdown="1" style="text-align: center; margin: 25px 0;">

  <div markdown="1" style="display: inline-block; text-align: left;">

| Controlled Source | Ideal $R_{in}$ | Ideal $R_{out}$ |
| :--- | :--- | :--- |
| VCCS | $\infty$ | $\infty$ |
| VCVS | $\infty$ | $0$ |
| CCCS | $0$ | $\infty$ |
| CCVS | $0$ | $0$ |

  </div>

  <p style="font-style: italic; font-size: 0.9em; color: #555; margin-bottom: 8px;">
    Table 1: Ideal impedances for 2-port controlled sources.
  </p>

</div>
