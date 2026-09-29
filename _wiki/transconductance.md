---
title: "Transconductance"
classes: wide
toc: true
toc_label: "Contents"
---

## MOS Transconductance

For an n-MOS transistor operating in the saturation region, its drain current is modelled by the equation

$$I_D = \frac{1}{2} \mu_n C_{ox} \frac{W}{L} (V_{GS} - V_{TH})^2 (1 + \lambda V_{DS}),$$

where $\mu_n,$ $C_{ox},$ $\frac{W}{L},$ $\lambda,$ and the threshold voltage $V_{TH}$ are device parameters.

The transfer conductance, or transconductance, is a transfer parameter (i.e., a parameter relating quantities at two different ports) that quantifies the *change* in drain current due to a change in the gate-source voltage. It measures how strongly the transistor reacts to an incremental gate-source voltage. In other words, it is the ratio of the incremental drain current to the incremental gate-source voltage and is given by

$$g_m = \frac{\partial I_D}{\partial V_{GS}} = \mu_n C_{ox} \frac{W}{L} (V_{GS} - V_{TH}) (1 + \lambda V_{DS}).$$

For hand calculations, we can assume that the channel-length modulation coefficient $\lambda$ is very small, resulting in the following expressions for the transconductance:

\begin{equation}
  {g_m = \mu_n C_{ox} \frac{W}{L} (V_{GS} - V_{TH}) \quad = \quad \sqrt{2 \mu_n C_{ox} \frac{W}{L} I_D} \quad = \quad \frac{2 I_D}{V_{GS} - V_{TH}}.}
  \label{eq:mos-gm}
\end{equation}
