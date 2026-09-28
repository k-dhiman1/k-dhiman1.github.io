---
title: "MOS Common-Source (CS) Amplifier"
permalink: /wiki/mos-cs-amplifier/
toc: true
toc_label: "Contents"
---

# Building up to the Amplifier

A transistor can be thought of as a voltage-controlled current source (VCCS), where the voltage at one port (gate-source) controls the current through the device. Passing this current through a load resistor allows for amplification to take place, where the output voltage is (ideally) a scaled replica of the input. For small, incremental fluctuations of voltage/current quantities in the circuit, the transistor can be approximated as a linear VCCS, where the output (incremental current) is related to the input (incremental voltage) via a parameter called the transconductance of the device. This relation is expressed as

$$i_d = g_m v_{gs},$$

where $i_d$ is the incremental or small-signal drain current, $g_m$ is the transconductance established at the given transistor operating point, and $v_{gs}$ is the incremental gate-source voltage.

