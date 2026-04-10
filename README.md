# Metabolic Traffic Jams in Bioreactors
### An Agent-Based Model of Self-Organized Criticality

**Course:** Complexity Science (Individual Project)  
**Student:** Stuti Upadhyay (2023CH10801)  
**Submitted:** April 10, 2026

---

## Overview

This project applies complexity science to model metabolic dynamics in an
industrial stirred-tank bioreactor using an agent-based model (ABM) implemented
in NetLogo 6.4.

Bacterial agents make local metabolic decisions based on their immediate oxygen
environment. When oxygen falls below a threshold, cells switch from aerobic to
anaerobic metabolism, producing acid that further depletes local oxygen and
triggers cascading failures — a **metabolic traffic jam**. The global behaviour
that emerges — spiral oxygen-depletion fronts, intermittent population crashes,
and non-monotonic efficiency responses — was never explicitly programmed.
It arises purely from local rules, consistent with **self-organized criticality (SOC)**.

---

## Repository Structure

```
├── simulation/
│   └── cll798_MetabolicTrafficJams.nlogo
│
├── data/
│   ├── anaerobic_conn0.1_cons0.3.csv
│   ├── anaerobic_conn0.3_cons0.3.csv
│   ├── anaerobic_conn0.6_cons0.3.csv
│   └── anaerobic_conn0.9_cons0.3.csv
│
├── analysis/
│   └── avalanche_analysis.py
│
├── figures/
│   ├── fig1.png
│   ├── fig2.png
│   ├── fig3a.png
│   ├── fig3b.png
│   ├── fig4.png
│   ├── fig5a.png
│   ├── fig5b.png
│   └── avalanche_analysis.png
│
└── report/
    ├── cll798_individualproject.pdf
    └── bioreactor_report.tex
```

---

## How to Run the Simulation

1. Download and install **NetLogo 6.4**
2. Open `simulation/cll798_MetabolicTrafficJams.nlogo`
3. Adjust sliders:
   - diffusion-rate
   - consumption-rate
   - reproduction-rate
4. Click **Setup** → **Go**

---

## How to Reproduce the Avalanche Analysis

```bash
pip install numpy pandas matplotlib
cd analysis/
python avalanche_analysis.py
```

---

## Key Findings

| Finding | Result |
|---|---|
| Connectivity (diffusion rate) | Monotonically increasing efficiency; but maximum avalanche size also increases — high connectivity is productive but volatile |
| Critical connectivity window | Avalanche frequency peaks at diffusion-rate 0.3–0.6, consistent with SOC |
| Noise (consumption rate) | Tentative non-monotonic efficiency response with local minimum at rate 0.3; requires replicate confirmation |
| Population pressure (reproduction rate) | Sharp phase transition between rates 2 and 5 — sub-critical sparse regime gives way to supercritical donut-forming cascade regime |

---

## Complexity Science Concepts

| Concept | Manifestation |
|---|---|
| Noise | Stochastic movement |
| Avalanche | Cascading switching |
| Connectivity | Diffusion coupling |

---

## Dependencies

- NetLogo 6.4  
- Python 3.8+  
- numpy, pandas, matplotlib  

---

## Acknowledgements

AI assistance (Claude) was used for framing, code review, and interpretation. All conclusions are the author's own.
