# Multi-Stage Attack Graph Simulation Via Markov Chains
> Closed-Form Dwell Time and Absorption Probabilities for SOC Containment versus Catastrophic Breach

Author: Patrick Lefler

Published: 2026-08-27

Published Link: 

## Project Introduction
> A closed-form absorbing Markov chain models the cyber kill chain in pure R, calculating adversary dwell time and containment-versus-catastrophe odds for board reporting.

## Overview
The project maps the enterprise kill chain as an absorbing Markov chain: six transient states, from initial phishing delivery through domain compromise, feed into three permanent outcomes — SOC containment, data exfiltration, or enterprise ransomware. Closed-form inversion of the transition matrix's transient block produces the Fundamental Matrix, from which expected adversary dwell time and exact terminal-outcome probabilities fall out algebraically, with no Monte Carlo simulation required. A baseline (unmitigated) parameterization is run alongside a hardened posture (Zero Trust segmentation, automated EDR) to isolate the containment lift each control regime buys at every stage. The intended outcome is a governance scorecard that ties incident-response SLAs and security capital allocation to a specific, auditable number rather than a subjective risk rating.

## Tech Stack
* **Language:** R
* **Framework:** [Quarto](https://quarto.org/)
* **Primary Libraries:** tidyverse (matrix algebra and data manipulation), ggplot2 + patchwork (multi-panel diagnostic plots), gt (governance scorecard), scales, sessioninfo
* **Deployment/Output:** Self-contained HTML report (`embed-resources: true`)

## Repository Structure
```
multi-stage-attack-graph-simulation/
├── data/               # Baseline and hardened transition matrix parameterizations
├── scripts/            # Fundamental Matrix solver, dwell-time and absorption-probability functions
├── models/             # Saved transition matrices and solved fundamental matrices (.rds)
├── output/              # Rendered HTML report
├── _brand.yml
├── _quarto.yml
└── index.qmd
```

## Key Findings
> Transition probabilities are calibrated to industry benchmarks, not internal SIEM telemetry — treat results as directional pending empirical validation against production data.

1. Baseline mean dwell time collapses from 14.2 hours at initial reconnaissance to 4.2 hours at payload staging, and catastrophic loss overtakes SOC containment as the more likely outcome once an attacker reaches S3: Privilege Escalation (52.9% vs. 47.1%).
2. A hardened control regime lifts SOC containment from 72.5% to 97.3% for perimeter-stage breaches and compresses catastrophic loss from 27.5% to 2.7%, with the largest net containment gain (+40.5 percentage points) landing at S4: Lateral Movement.
3. The Fundamental Matrix framework replaces simulation with closed-form matrix inversion, producing deterministic, auditable dwell-time and absorption-probability estimates that support three governance directives tying MTTD/MTTR SLAs and capital allocation to specific kill-chain stages.

## License
This project is licensed under the MIT License. See the LICENSE file for details.

## Contact
Patrick Lefler [https://www.linkedin.com/in/patricklefler/] | [patrick-lefler.github.io] | [https://substack.com/@pflefler]
