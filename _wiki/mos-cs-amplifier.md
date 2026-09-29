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

where $i_d$ is the incremental or small-signal drain current, $g_m$ is the transconductance established at the given transistor operating point, and $v_{gs}$ is the incremental gate-source voltage. Passing this current through a load resistor allows for amplification to take place by generating an output voltage that is a scaled version of the input.

A basic incremental circuit model for a MOS transistor based on Eq. \eqref{eq:vccs} is shown in Fig. 1 below. The effects of channel-length modulation (i.e., the dependence of the drain current on the drain-source voltage) can be accounted for by including a resistor $r_O$ between the drain and the source terminals.

{% include figure image_path="/assets/images/wiki/mos_ss.svg" caption="Figure 1: MOS transistor small-signal model: (left) ideal model, (right) including channel-length modulation." class="align-center" %}

From Eq. \eqref{eq:vccs}, it can be observed that an input voltage can be given to either the gate or the source terminal, and the output can be taken (across a resistor) from either the drain or the source terminal, as the drain current is equal to the source current. Applying an input to the drain or measuring an output voltage at the gate are of no meaning because the drain voltage only weakly influences the drain current (due to channel-length modulation), and the gate voltage is not influenced by the drain current (but the converse is true). 

This results in four possible input/output configurations. Working through the possibilities, we can come the conclusion that providing an input at the gate and extracting the output from the drain, as shown below in Fig. 2, gives us the incremental amplification behavior that we are looking for.

{% include figure image_path="/assets/images/wiki/mos_cs_ss_basic.svg" caption="Figure 2: MOS common-source amplifier basic small-signal model." class="align-center" %}

In this configuration, the source terminal is common to both the input and the output ports and can be incrementally grounded. The input is applied to the gate due to the large impedance seen looking in; this ensures that the transistor does not load the source, so the entire $v_\text{in}$ is passed to the gate. The output is taken across the drain and the common terminal because the output impedance when looking into this port is large (ideally infinite), making it so that the entire incremental current passes through the load resistor. These factors together maximize the incremental voltage gain of the circuit which is given by

\begin{equation} 
  \frac{v_\text{out}}{v_\text{in}} = \frac{-g_m v_\text{in} R_L}{v_\text{in}} = -g_m R_L. 
  \label{eq:cs-gain} 
\end{equation}

The effects of channel-length modulation can be included by replacing $R_L$ with $R_L || r_O$ in Eq. \eqref{eq:cs-gain}.




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
