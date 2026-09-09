# Natural Systems Modelling

Three studies of nonlinear and ecological dynamics: numerical sensitivity in a forced Duffing oscillator, local interactions in a stochastic prey–predator model, and the limits of constant predator harvesting in Lotka–Volterra equations.

The [submitted report](reports/COM6009_Assignment_Yongjiang.pdf), **Modelling and Simulation of Nonlinear and Ecological Natural Systems**, presents the methods and six figures in three pages. It was completed as Yongjiang's individual COM6009 assignment at the University of Sheffield.

> **中文概述：** 本项目通过 Duffing 振子、草地—兔子—狐狸模型和带捕捞项的 Lotka–Volterra 方程，研究数值误差、随机生态互动及模型适用边界。仓库保留正式提交的三页报告与方法说明；原始仿真代码、数据和随机种子尚未恢复，因此其中的数值结果属于报告中的历史结果。

## Project at a glance

| Item | Details |
| --- | --- |
| Project type | Individual modelling and simulation report |
| Course | COM6009, cross-listed with COM3001, University of Sheffield |
| Methods | Ordinary differential equations, RK4 step-size comparison, stochastic agent-based modelling, phase portraits and Poincaré sampling |
| Available artifacts | Original three-page PDF, six figures, submission record and model notes |
| Status | Official report preserved; original executable simulations and numerical outputs unavailable |

## Research questions and methods

| Study | Question | Approach described in the report |
| --- | --- | --- |
| Forced Duffing oscillator | How do numerical step size and nearby initial states affect simulated dynamics? | Convert the second-order equation into a first-order system; integrate with RK4; compare errors, phase portraits and a stroboscopic Poincaré section. |
| Grass, rabbits and foxes | How do local interactions and fox speed affect population dynamics and extinction? | Use the lecture eco-lab structure with movement, eating, breeding and death; compare eight runs of 600 iterations at each fox speed. |
| Harvested Lotka–Volterra model | When does constant harvesting produce biologically invalid solutions? | Compare trajectories at five harvesting levels and examine when predator abundance crosses below zero. |

The [model notes](docs/MODELS_AND_REPRODUCIBILITY.md) record the equations, available parameters, numerical settings and information still needed for exact reproduction. RK4 is explicitly documented for the Duffing study; the harvesting study's solver is not clearly specified.

## Reading the report

Open the [original PDF](reports/COM6009_Assignment_Yongjiang.pdf) and follow this sequence:

| Figures | PDF pages | What to examine |
| --- | --- | --- |
| 1–2 | 1 | Duffing trajectories and the accuracy/cost choice behind the selected step size |
| 3 | 2 | Initial-condition sensitivity and the Poincaré section under stronger forcing |
| 4–5 | 2 | A representative ecological run and variation across fox-speed experiments |
| 6 | 3 | Harvested population trajectories and the boundary of biological validity |

There is no installation step for the available deliverable. The original programs, generated arrays and environment specification have not been recovered.

## Results and verification

The report records the following observations:

- **Duffing accuracy:** with a reference time step of 0.001, the reported RMSE is `1.28 × 10⁻¹` at step 0.2 and `1.08 × 10⁻⁶` at step 0.01. The study selects 0.01 for its simulations.
- **Stochastic extinction:** fox speeds 2, 3, 4 and 5 yield observed rabbit-extinction proportions of 0, 0, 0.375 and 0.875, respectively, from eight runs per condition.
- **Model boundary:** for harvesting rates 0.4 and 0.8, predator abundance crosses below zero at approximately times 34.15 and 21.74. These are invalid biological populations, motivating changes to the harvesting or extinction rules.

These are historical values from the submitted report, not regenerated measurements. Archival checks verified the PDF's original bytes and inspected all three pages, figures and references. This documentation refresh verifies navigation and file preservation; it does not add experimental evidence.

## Repository guide

| File | Purpose |
| --- | --- |
| [Submitted report](reports/COM6009_Assignment_Yongjiang.pdf) | Read the complete original assignment |
| [Models and reproducibility](docs/MODELS_AND_REPRODUCIBILITY.md) | Inspect equations, settings, figure references and reproduction gaps |
| [Submission record](reports/submission_record.json) | Check the Blackboard attempt, submission time, original file size and SHA-256 |

## Limitations

The small agent-based sample describes the observed runs, not a precisely established extinction probability. The report interprets Duffing sensitivity and Poincaré structure as evidence for chaos but does not compute a Lyapunov exponent. Suggested harvesting fixes are discussed rather than demonstrated by a recovered implementation.

Exact reproduction requires the original simulations, configurations, seeds and numerical outputs. The report contains no source appendix, embedded file or external code link. A future reconstruction would be new work until it could be compared with the original implementation.

## Attribution and provenance

The report names its author as **Yongjiang**; this repository is maintained by **Yongjiang Liu**. Blackboard records **Individual Assignment, Attempt 1**, submitted **6 May 2026 at 23:43 (UTC+8)**.

The agent-based model is described as using the module's lecture eco-lab structure. The PDF retains its bibliography and attribution; course teaching materials are not presented here as original student code. The [submission record](reports/submission_record.json) and [preservation notes](docs/MODELS_AND_REPRODUCIBILITY.md#preservation-checks) document the unchanged report. Later archive and documentation commits do not recreate its original development history.
