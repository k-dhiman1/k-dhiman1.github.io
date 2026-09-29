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

<div style="text-align: center; margin: 25px 0;">
  <img src="/assets/images/wiki/mos_ss.svg" alt="MOS ss model" style="max-height: auto; width: auto; display: block; margin: 0 auto;" />
  <p style="font-style: italic; font-size: 0.9em; color: #555; margin-top: 10px;">
    Figure 1: MOS transistor small-signal model: ideal model (left), including channel-length modulation (right).
  </p>
</div>

From Eq. \eqref{eq:vccs}, it can be observed that an input voltage can be given to either the gate or the source terminal, and the output can be taken (across a resistor) from either the drain or the source terminal, as the drain current is equal to the source current. Applying an input to the drain or measuring an output voltage at the gate is of no meaning because the drain voltage only weakly influences the drain current (due to channel-length modulation), and the gate voltage is not influenced by the drain current (but the converse is true). 

This results in four possible input/output configurations. Working through the possibilities, we can come the conclusion that providing an input at the gate and extracting the output from the drain, as shown below in Fig. 2, gives us the incremental amplification behavior that we are looking for.

<div style="text-align: center; margin: 25px 0;">
  <img src="/assets/images/wiki/mos_cs_ss_basic.svg" alt="MOS cs amp ss ckt" style="max-height: 300px; width: auto; display: block; margin: 0 auto;" />
  <p style="font-style: italic; font-size: 0.9em; color: #555; margin-top: 10px;">
    Figure 2: MOS common-source amplifier basic small-signal model.
  </p>
</div>

In this configuration, the source terminal is common to both the input and the output ports and can be incrementally grounded. The input is applied to the gate due to the large impedance seen looking in; this ensures that the transistor does not load the source, so the entire $v_\text{in}$ is passed to the gate. The output is measured across the drain and the common terminal because the output impedance when looking into this port is large (ideally infinite), making it so that the entire incremental current passes through the load resistor. These factors together maximize the incremental voltage gain of the circuit which is given by

\begin{equation} 
  \frac{v_\text{out}}{v_\text{in}} = \frac{-g_m v_\text{in} R_L}{v_\text{in}} = -g_m R_L. 
  \label{eq:cs-gain} 
\end{equation}

The effects of channel-length modulation can be included by replacing $R_L$ with $R_L \vert\vert r_O$ in Eq. \eqref{eq:cs-gain}. Additionally, if $R_\text{in}$ and $R_\text{out}$ are finite, then the voltage gain can be expressed as

\begin{equation} 
  \frac{v_\text{out}}{v_\text{in}} = \frac{v_{gs}}{v_\text{in}} \cdot \frac{i_d}{v_{gs}} \cdot \frac{v_\text{out}}{i_d} = \frac{R_\text{in}}{R_g + R_\text{in}} \cdot g_m \cdot \left[- \left(R_L \vert\vert R_\text{out}\right)\right].
  \label{eq:cs-overall-gain} 
\end{equation}

## Biasing

The amplifier topology discussed above requires the n-MOS transistor to biased in the saturation region to realize the desired small-signal amplification and performance. It is generally preferable to bias a transistor using a current rather than voltage in order to minimize variations in the transconductance of the device; one such biasing scheme is shown in Fig. 3 below.

<div style="text-align: center; margin: 25px 0;">
  <img src="/assets/images/wiki/mos_cs_dc_bias.svg" alt="n-MOS biasing scheme" style="max-height: 450px; width: auto; display: block; margin: 0 auto;" />
  <p style="font-style: italic; font-size: 0.9em; color: #555; margin-top: 10px;">
    Figure 3: n-MOS current biasing scheme with implicit negative feedback.
  </p>
</div>

This biasing scheme employs implicit negative feedback to maintain a constant drain current $I_D = I_\text{ref}$. To observe how, imagine that there is an infinitesimal capacitance connected from the source to ground (it is reasonable to assume that the node has some small parasitic capacitance associated with it). If a current $I_D$ is entering the source and $I_\text{ref}$ is leaving it, then $I_D - I_\text{ref}$ must pass through the infinitesimal capacitor (KCL). If the transistor's drain current is greater than $I_\text{ref}$, then the capacitor current is positive and it begins to charge, thus increasing $V_S$; if $V_S$ increases while $V_G$ is held constant, then the drain current $I_D$ will decrease. Conversely, if the drain current is less than $I_\text{ref}$, then the capacitor current is negative and it begins to discharge to provide the current required to satisfy KCL, thus decreasing $V_S$; if $V_S$ decreases while $V_G$ is held constant, then the drain current $I_D$ will increase. This process continues until $I_D = I_\text{ref}$.

The next step is to connect the input voltage to the gate and the load resistor to the drain. This is done through the use of coupling/bypass capacitors, which ensure that the transistor $M_1$'s operating point is not disturbed by the addition of these components. Furthermore, the source terminal needs to be incrementally grounded via a coupling capacitor, as it is the common terminal for the amplifier. The final circuit is shown in Fig. 4 below.

<div style="text-align: center; margin: 25px 0;">
  <img src="/assets/images/wiki/mos_cs_dc_bias_full.svg" alt="n-MOS cs amp full" style="max-height: 450px; width: auto; display: block; margin: 0 auto;" />
  <p style="font-style: italic; font-size: 0.9em; color: #555; margin-top: 10px;">
    Figure 4: Full n-MOS common-source amplifier circuit.
  </p>
</div>

The small-signal voltage gain of this circuit is given by Eq. \eqref{eq:cs-overall-gain}, where $R_\text{in} = R_A \vert \vert R_B$ is the input resistance looking in from the source ($R_g$ not included) and $R_\text{out} = R_D \vert \vert r_O$ is the output resistance looking into the drain of $M_1$ from the load ($R_L$ not included). That is,

$$
  \frac{v_\text{out}}{v_\text{in}} = -\frac{R_A \vert \vert R_B}{R_g + R_A \vert \vert R_B} g_m \left(R_L \vert\vert R_D \vert\vert r_O\right).
$$

To maximize the voltage gain, we would like to have $R_A \vert \vert R_B \gg R_g$ and $R_D \vert \vert r_O \gg R_L$.

## Source Degeneration

When building discrete circuits, it is preferable to minimize the use of active components to reduce circuit cost. Thus, we would like to bias the transistor using a passive component instead of a current source (Fig. 3). From the substitution theorem, we know that any circuit element can be replaced with another provided that the voltage across and the current through the branch containing the element remain unchanged. In other words, we can replace the current source $I_\text{ref}$ in Fig. 3 with a source resistor $R_S$ provided that the source voltage $V_S$ and the drain current $I_D$ remain the same. This addition of a resistor in series with the source is also known as source degeneration.

From Fig. 3, it can be observed that $I_D = I_\text{ref}$, $V_G = R_B V_{DD}/(R_A + R_B) \triangleq V_{G0}$, and $V_S = V_{G0} - V_{GS0} \triangleq V_{S0}$, where

$$ V_{GS0} = V_{TH} + \sqrt{ \frac{2 I_\text{ref}}{\mu_n C_{ox} (W/L)} } \quad (M_1 \text{ in saturation; } r_O \to \infty). $$

Thus, the resistor $R_S$ will have to be chosen such that

$$
  R_S = \frac{V_{S0}}{I_\text{ref}} = \frac{1}{I_\text{ref}} \left[ \frac{R_B}{R_A + R_B} V_{DD} - V_{TH} - \sqrt{\frac{2 I_\text{ref}}{\mu_n C_{ox} (W/L)}} \right].
$$

The substitution is highlighted in Fig. 5 below.

<div style="text-align: center; margin: 25px 0;">
  <img src="/assets/images/wiki/mos_cs_degen_bias.svg" alt="n-MOS degen bias" style="max-height: 350px; width: auto; display: block; margin: 0 auto;" />
  <p style="font-style: italic; font-size: 0.9em; color: #555; margin-top: 10px;">
    Figure 5: n-MOS biasing scheme with source resistor instead of current source.
  </p>
</div>

Since we have substituted the current source with a resistor and not eliminated it entirely, we still expect there to be some negative feedback that stabilizes the circuit. This is indeed true and can be observed as follows: when $I_D$ increases ($I_D > I_\text{ref}$), $V_{S} = I_D R_S$ increases, causing $I_D$ to decrease (because $V_{G} = V_{G0}$ is held constant). Similarly, if $I_D$ decreases ($I_D < I_\text{ref}$), then $V_{S}$ decreases, causing $I_D$ to increase. Therefore, the presence of the source resistor $R_S$ causes the transistor to resist fluctuations in its bias current, though not as strongly as current-source biasing.

Another way to look at the negative feedback due to $R_S$ is to consider an incremental change $v_g$ in the gate voltage. This $v_g$ will result in a change $i_d$ in the drain current. From the above discussion, we know that the source voltage will change in response to $i_d$ (Ohm's law); i.e., the incremental source voltage $v_s$ is non-zero. We also know from Eq. \eqref{eq:vccs} that the change in drain current due to an incremental $v_{gs}$ is $i_d = g_m v_{gs}$. The incremental source voltage is then given by

\begin{equation} 
  v_s = i_d R_S = g_m v_{gs} R_S = g_m (v_g - v_s) R_S \implies v_s = \frac{g_m R_S}{1 + g_m R_S}v_g.
  \label{eq:vcvs-gain}
\end{equation}

Note that the factor $g_m R_S/(1 + g_m R_S) < 1$ in the above equation, so while the source voltage changes in a way as to resist the change in the gate voltage (which is the cause for the drain current changing), it cannot fully offset it. Compare this to the case of current-source biasing by setting $R_S \to \infty$ in Eq. \eqref{eq:vcvs-gain}. This yields $v_s = v_g$, meaning that the change in the source voltage is equal to the change in the gate voltage, thus maintaining $v_{GS}$ constant, and therefore $i_D$ remains constant.

To analyze the performance of the source-degenerated common-source amplifier, consider the incremental circuit shown in Fig. 6 below. Note that $M_1$ represents the ideal small-signal MOS transistor model (Fig. 1, left). The effect of channel-length modulation is included by explicitly placing $r_O$ in parallel with $M_1$. 

<div style="text-align: center; margin: 25px 0;">
  <img src="/assets/images/wiki/mos_cs_degen_ss.svg" alt="MOS degen ss" style="max-height: 450px; width: auto; display: block; margin: 0 auto;" />
  <p style="font-style: italic; font-size: 0.9em; color: #555; margin-top: 10px;">
    Figure 6: Basic incremental circuit for common-source amplifier with source degeneration.
  </p>
</div>

Applying KCL at the source and substituting $v_g = v_\text{in}$ and $v_\text{out} = -v_s R_L/R_S$ gives

$$ g_m v_{gs} + \frac{v_\text{out} - v_s}{r_O} = \frac{v_s}{R_s} \implies g_m (v_\text{in} - v_s) - v_s \frac{R_L/R_S + 1}{r_O} = \frac{v_s}{R_s}.$$

Solving gives

$$\frac{v_s}{v_\text{in}} = \frac{g_m}{1/R_S + g_m + R_L/(r_O R_S) + 1/r_O} = \frac{g_m r_O R_S}{r_O + R_S + g_m r_O R_S + R_L}.$$

Finally, $$\frac{v_\text{out}}{v_\text{in}} = \frac{v_s}{v_\text{in}} \cdot \frac{v_\text{out}}{v_s} = \frac{-g_m r_O R_L}{r_O + R_S + g_m r_O R_S + R_L}.

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
