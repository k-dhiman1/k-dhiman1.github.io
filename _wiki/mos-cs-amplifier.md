---
title: "MOS Common-Source Amplifier"
classes: wide
toc: true
toc_label: "Contents"
---

## Building up to the Amplifier

In the saturation region, the MOS transistor can be thought of as a voltage-controlled current source (VCCS), where the voltage at one port (gate-source) controls the current through the device. For small, incremental fluctuations in the transistor gate-source voltage, the device can be approximated as a *linear* VCCS, where the output current is related to the input voltage via a parameter known as the transconductance of the device. This relation is expressed as

\begin{equation} 
  i_d = g_m v_{gs}, 
  \label{eq:vccs} 
\end{equation}

where $i_d$ is the incremental or small-signal drain current, $g_m$ is the transconductance established at the given transistor operating point, and $v_{gs}$ is the incremental gate-source voltage. Passing this current through a load resistor $R_L$ allows for amplification to take place, provided that $\vert {g_m R_L}\vert > 1$, by generating an output voltage that is a scaled version of the input.

A basic incremental circuit model for a MOS transistor based on Eq. \eqref{eq:vccs} is shown below. The effects of channel-length modulation (i.e., the dependence of the drain current on the drain-source voltage) can be accounted for by including a resistor $r_O$ between the drain and the source terminals.

![MOS transistor small-signal equivalent circuit](/assets/images/wiki/mos_ss.svg){: .align-center}

<!-- 

### Transconductance

For an n-MOS transistor operating in the saturation region, its drain current is modelled by the equation

$$I_D = \frac{1}{2} \mu_n C_{ox} \frac{W}{L} (V_{GS} - V_{TH})^2 (1 + \lambda V_{DS}),$$

where $\mu_n,$ $C_{ox},$ $\frac{W}{L},$ $\lambda,$ and the threshold voltage $V_{TH}$ are device parameters.

The transfer conductance, or transconductance, is a transfer parameter (i.e., a parameter relating quantities at two different ports) that quantifies the *change* in drain current due to a change in the gate-source voltage. In other words, it is the ratio of the incremental drain current to the incremental gate-source voltage and is given by

$$g_m = \frac{\partial I_D}{\partial V_{GS}} = \mu_n C_{ox} \frac{W}{L} (V_{GS} - V_{TH}) (1 + \lambda V_{DS}).$$

For hand calculations, we can assume that the channel-length modulation coefficient $\lambda$ is very small, resulting in the following expressions for the transconductance:

$$\boxed{g_m = \mu_n C_{ox} \frac{W}{L} (V_{GS} - V_{TH}) \quad = \quad \sqrt{2 \mu_n C_{ox} \frac{W}{L} I_D} \quad = \quad \frac{2 I_D}{V_{GS} - V_{TH}}.}$$

-->
