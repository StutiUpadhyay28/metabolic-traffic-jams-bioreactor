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
│   └── cll798_MetabolicTrafficJams.nlogo   # NetLogo model (main simulation file)
│
├── data/
│   ├── anaerobic_conn0.1_cons0.3.csv       # Time-series: diffusion-rate = 0.1
│   ├── anaerobic_conn0.3_cons0.3.csv       # Time-series: diffusion-rate = 0.3
│   ├── anaerobic_conn0.6_cons0.3.csv       # Time-series: diffusion-rate = 0.6
│   └── anaerobic_conn0.9_cons0.3.csv       # Time-series: diffusion-rate = 0.9
│
├── figures/
│   ├── fig1.png                            # Baseline simulation at tick ~65
│   ├── fig2.png                            # Population dynamics plot
│   ├── fig3a.png                           # Spatial pattern: diffusion = 0.3
│   ├── fig3b.png                           # Spatial pattern: diffusion = 0.9
│   ├── fig4.png                            # Spatial pattern: consumption = 0.1
│   ├── fig5a.png                           # Spatial pattern: reproduction = 5
│   ├── fig5b.png                           # Spatial pattern: reproduction = 2
│   ├── fig6.png                            # Experiment trend analysis
│   ├── Interface.png                       # Interface of the NetLogo Simulation
│   └── avalanche_analysis.png              # Generated avalanche frequency figure
│
└── report/
    ├── cll798_individualproject.pdf        # Final submitted report (PDF)
    └── bioreactor_report.tex              # LaTeX source file
```

---

## How to Run the Simulation

1. Download and install **NetLogo 6.4** from [ccl.northwestern.edu/netlogo](https://ccl.northwestern.edu/netlogo/)
2. Open `simulation/cll798_MetabolicTrafficJams.nlogo`
3. In the **Interface** tab, adjust the three sliders:
   - `diffusion-rate` — controls oxygen transport range (connectivity)
   - `consumption-rate` — controls how fast aerobic cells deplete oxygen (noise)
   - `reproduction-rate` — controls population growth rate (population pressure)
4. Click **Setup** to initialise the simulation
5. Click **Go** to run
6. To export time-series data for avalanche analysis, run to tick 500 then click **Export Data**

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

| Concept | Manifestation in this system |
|---|---|
| **Noise** | Stochastic Brownian cell movement (±10° random perturbation per tick) seeding cascade events |
| **Avalanche** | Cascading anaerobic metabolic switching propagating through spatially connected bacterial population |
| **Connectivity** | Spatial range of oxygen and acid diffusion; population density governing coupling strength between agents |

---

## Model Parameters

| Parameter | Default | Range | Role |
|---|---|---|---|
| `diffusion-rate` | 0.61 | 0.1 – 0.9 | Oxygen transport (connectivity) |
| `consumption-rate` | 0.30 | 0.1 – 0.7 | Oxygen depletion per aerobic cell per tick |
| `reproduction-rate` | 7.2 | 2 – 10 | Probability (%) of cell division per tick |

---

## Dependencies

| Tool | Version | Purpose |
|---|---|---|
| NetLogo | 6.4 | Agent-based simulation |
| Python | 3.8+ | Avalanche data analysis |
| numpy | any | Numerical computation |
| pandas | any | CSV data loading |
| matplotlib | any | Figure generation |

---

## Acknowledgements

AI assistance (Claude, Anthropic) was used for complexity science framing,
code review, experiment design guidance, result interpretation, and report
drafting. All simulation data were collected by the author through direct
NetLogo experimentation. All scientific interpretations and conclusions are
the author's own. A full list of AI prompts used is provided in Appendix A
of the project report.

---

## References

1. Bak, P., Tang, C., & Wiesenfeld, K. (1987). Self-organized criticality: An explanation of 1/f noise. *Physical Review Letters, 59*(4), 381–384.
2. Wilensky, U. (1999). NetLogo. Center for Connected Learning and Computer-Based Modeling, Northwestern University. http://ccl.northwestern.edu/netlogo/
3. Nienow, A. W. (2006). Hydrodynamics of stirred bioreactors. *Applied Mechanics Reviews, 51*(1), 3–32.
4. Enfors, S. O., et al. (2001). Physiological responses to mixing in large scale bioreactors. *Journal of Biotechnology, 85*(2), 175–185.
5. Bonabeau, E. (2002). Agent-based modeling: Methods and techniques for simulating human systems. *PNAS, 99*(suppl 3), 7280–7287.
6. Jensen, H. J. (1998). *Self-Organized Criticality*. Cambridge University Press.
