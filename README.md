# PhysGuard

> Physics-based firewall that detects physically implausible cyberattacks on EV charging systems.

**Team:** Quadcore | **Event:** SUSTAINATHON 26 (VIT x CNET) | **Domain:** Sustainable AI & Cybersecurity | **Problem Statement:** AI-01, The Physically Plausible Cyberattack Problem

## Problem

Connected EVs and chargers depend on digital communication. An attacker can send a sensor value or command that looks valid to a conventional security check (correct format, in range, authenticated) but is physically inconsistent with the real state of the system. Traditional checks ask "is this data digitally valid?" They do not ask "is this data physically possible?"

## Our approach

1. **Digital twin:** a physics model of an EV battery and charger (equivalent circuit plus a thermal model) that predicts the expected voltage, current and temperature.
2. **Attack simulator:** injects false data, including stealthy attacks that stay inside normal ranges.
3. **Residual detector:** compares measured values with the twin's predictions and raises an alarm when the gap is persistently suspicious (CUSUM and/or a Kalman filter).
4. **Localization:** uses which signals disagree with the physics to identify the likely compromised sensor.
5. **Efficiency:** measures compute time (and estimated energy) per check, so the solution fits edge devices.
6. **Dashboard:** a live demo where a simple threshold check stays green while PhysGuard flags the attack.

## Status

- [ ] Digital twin
- [ ] Attack simulator
- [ ] Detector
- [ ] Localization
- [ ] Dashboard
- [ ] Metrics versus a threshold baseline
- [ ] Documentation and presentation

Results (detection rate, false alarms, detection delay, compute cost) will be added here once measured.

## Repository structure

```
physguard-by-quadcore/
|-- model/        # digital twin: battery, charger, thermal model
|-- attacks/      # attack simulator (false data injection, stealthy attacks)
|-- detector/     # residual detector, localization, metrics
|-- dashboard/    # Streamlit or Plotly demo app
|-- data/         # datasets (see Third-party resources; do not commit large files)
|-- docs/         # documentation, slides, diagrams
|-- requirements.txt
`-- README.md
```

## Setup

```bash
git clone <repo-url>
cd physguard-by-quadcore
python -m venv venv
# Windows: venv\Scripts\activate
# macOS/Linux: source venv/bin/activate
pip install -r requirements.txt
```

Planned `requirements.txt`: numpy, scipy, pandas, matplotlib, scikit-learn, streamlit

## Team

| Member | Role |
|---|---|
| Smaran Pokala | TBD |
| Sai Sathwik Panduri | TBD |
| Gauri | TBD |
| Rosie | TBD |

Suggested roles: Modeller, Detector lead, Dashboard and demo, Docs and pitch.

## Third-party resources

All external datasets, libraries and code must be listed here (event rule 9 and the submission checklist).

| Resource | Type | Use | Link |
|---|---|---|---|
| NumPy, SciPy, pandas, Matplotlib, scikit-learn, Streamlit | Libraries | Modelling, analysis, dashboard | Official docs |
| NASA Li-ion Battery Aging Datasets (Ames Prognostics Center of Excellence) | Dataset | Battery behaviour and model validation | Add link |

## Originality statement

The idea, design and implementation in this repository were created by the team during the event. Third-party datasets and libraries are acknowledged above.

## License

To be decided after the event.
