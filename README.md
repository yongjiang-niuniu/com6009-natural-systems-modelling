# Natural Systems Modelling — COM6009

An archive of Yongjiang's individual assignment, **Modelling and Simulation of Nonlinear and Ecological Natural Systems**, submitted for COM6009 at the University of Sheffield. The report compares numerical differential-equation models with a stochastic agent-based ecological model.

**Start with the [submitted report](reports/COM6009_Assignment_Yongjiang.pdf).** The official Blackboard submission contains one three-page PDF. This repository preserves that original file and documents its contents; the original simulation programs and data have not been recovered.

## Investigations

| Model | Work described in the report | Figures |
| --- | --- | --- |
| Forced Duffing oscillator | Convert a second-order equation into a first-order system; integrate with RK4; compare step sizes, phase portraits, initial-condition sensitivity and a Poincaré section. | 1–3 |
| Agent-based prey–predator model | Model local interactions among grass, rabbits and foxes; vary fox speed across repeated stochastic simulations. | 4–5 |
| Lotka–Volterra model with predator harvesting | Compare coexistence dynamics with increasing constant harvesting and identify when numerical populations leave the biologically meaningful region. | 6 |

The report records a Duffing step-size study using a reference step of 0.001 and selects 0.01 for its simulations. In the agent-based study, eight runs of 600 iterations per fox speed give observed rabbit-extinction proportions of 0, 0, 0.375 and 0.875 at speeds 2, 3, 4 and 5. The harvesting study discusses the model's failure to represent biology after predator abundance becomes negative.

These are results reported in the submitted PDF. They have not been regenerated during archiving. The small stochastic experiment and missing executable artifacts limit independent verification; the [model and reproducibility notes](docs/MODELS_AND_REPRODUCIBILITY.md) record the available parameters and missing information.

## Archive contents

- [Official report](reports/COM6009_Assignment_Yongjiang.pdf): unchanged three-page submission, including all six figures and references.
- [Submission record](reports/submission_record.json): observed Blackboard attempt, submission time, file size and SHA-256 checksum.
- [Model and reproducibility notes](docs/MODELS_AND_REPRODUCIBILITY.md): equations, recorded numerical settings, a figure map and conditions needed to reproduce the work.

## Submission and attribution

The Blackboard assessment is **Individual Assignment**, attempt 1, submitted **6 May 2026 at 23:43 (UTC+8)**. The course is COM6009, cross-listed with COM3001. The report names its author as **Yongjiang**; this archive is maintained by **Yongjiang Liu**.

The agent-based implementation is described in the report as using the module's lecture eco-lab structure. The report's bibliography and attribution remain in the PDF. Course teaching materials are not included in this project archive.

The PDF's SHA-256 is:

```text
85a99558bfe9e290e0bae2bab2f6715ac706649fbe485ed51a82f412dc636fb7
```

No installation or execution command is supplied because this archive currently contains no executable simulation source. Its commits document preservation and explanation of the recovered deliverable at the time of archiving; they do not reconstruct the original development history.
