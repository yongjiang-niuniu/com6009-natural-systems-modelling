# Models and reproducibility

These notes describe the [submitted COM6009 report](../reports/COM6009_Assignment_Yongjiang.pdf). All numerical results below are historical results stated in that report. No simulation was rerun while preparing this archive.

## Available evidence

The recovered deliverable is a three-page PDF with six figures. Inspection of every page, the PDF's link annotations and embedded-file collection found no source-code appendix, external code link or embedded file. The observed Blackboard attempt contains this single PDF attachment.

The report records methods and selected parameters, but does not supply the original programs, generated numerical arrays, random seeds or an environment specification. The notes below can guide a future reconstruction. Such a reconstruction would be a new implementation until the original source is recovered and compared.

## 1. Forced Duffing oscillator

Report section 1, pages 1–2, figures 1–3.

The second-order equation is

```text
x'' = γ cos(ωt) − δx' − αx − βx³
```

With `x₁ = x` and `x₂ = x'`, the first-order system is

```text
dx₁/dt = x₂
dx₂/dt = γ cos(ωt) − δx₂ − αx₁ − βx₁³
```

| Parameter | Value for the main oscillator study |
| --- | --- |
| Forcing amplitude γ | 0.29 |
| Damping δ | 0.3 |
| Linear coefficient α | −1 |
| Cubic coefficient β | 1 |
| Forcing frequency ω | 1.2 |
| Integrator | Fourth-order Runge–Kutta (RK4) |
| Selected time step | 0.01 |
| Fine reference time step | 0.001 |

The explicit forcing time makes the stated system non-autonomous. Figure 1 presents trajectories for different initial conditions and the phase portrait `(x, v)`.

Figure 2 compares time steps against the reference solution. The report gives the following RMSE values:

| Time step | Reported RMSE |
| --- | --- |
| 0.2 | 1.28 × 10⁻¹ |
| 0.01 | 1.08 × 10⁻⁶ |
| 0.005 | 7.05 × 10⁻⁸ |

For the sensitivity investigation in figure 3, γ is changed to 0.5. The two initial states are `(0.100000, 0)` and `(0.100001, 0)`. The report records a maximum separation of approximately 2.15 and a stroboscopic Poincaré section sampled once per forcing period `T = 2π/ω`. It interprets these observations as evidence for chaotic behaviour. The report does not supply a computed Lyapunov exponent, and this archive does not independently establish chaos.

**Needed for exact reproduction:** the original integrator and plotting code, all per-figure initial states and simulation settings in machine-readable form, the precise RMSE sampling/alignment procedure, and the transient-discard and sampling choices for the Poincaré section. Reading coordinates from the plotted figures would not recover the original numerical arrays.

## 2. Agent-based prey–predator model

Report section 2, pages 1–2, figures 4–5.

The report describes a lecture eco-lab implementation in which an environment holds grass and rabbit and fox agents inherit from a common agent class. Local movement, eating, breeding and death rules produce stochastic population dynamics. The comparison with an ODE model emphasizes spatial locality, discrete individuals and extinction.

Figure 4 is a representative run. Its grass curve is divided by 20 for display on the same axis; this is a plotting scale, not a stated change to the ecological rules.

For figure 5, fox speed α takes four values. There are eight independent simulations per value, each lasting 600 iterations. The report studies rabbit extinction, final rabbit count, and maximum and minimum rabbit counts, with variability shown in the figure.

| Fox speed α | Reported observed rabbit-extinction proportion |
| --- | --- |
| 2 | 0 |
| 3 | 0 |
| 4 | 0.375 |
| 5 | 0.875 |

These proportions come from eight runs per condition. They describe this small experiment and should not be read as precisely established extinction probabilities for the underlying model.

**Needed for exact reproduction:** the original eco-lab version and student changes, environment dimensions and boundaries, initial populations and grass state, update order, full movement/eating/breeding/death rules, food and age settings, random-number generator and seeds, the precise extinction rule, and the per-run results used for the figure. No complete dependency or runtime specification was recovered.

## 3. Lotka–Volterra equations with predator harvesting

Report section 3, pages 2–3, figure 6.

The report uses prey abundance `x` and predator abundance `y`:

```text
dx/dt = x(α − βy)
dy/dt = y(δx − γ) − h
```

| Parameter | Value |
| --- | --- |
| α | 1.0 |
| β | 0.1 |
| γ | 1.5 |
| δ | 0.075 |
| Harvesting values h shown in figure 6 | 0, 0.1, 0.2, 0.4, 0.8 |

For `h = 0`, the non-zero coexistence equilibrium is `(x*, y*) = (20, 10)`. A positive `h` subtracts a constant amount from predator growth. The report records predator abundance crossing below zero at approximately `t = 34.15` for `h = 0.4` and `t = 21.74` for `h = 0.8`.

Negative abundance makes this mathematical solution biologically invalid. The report proposes possible model changes, such as treating zero as extinction or making harvesting vanish when predators are absent. It does not document an implementation of those changes.

**Needed for exact reproduction:** original source and numerical outputs, initial conditions and settings for each plotted trajectory, the solver and tolerances or step size, and the procedure used to identify boundary-crossing times. RK4 is explicitly named for the Duffing study; the report does not clearly specify a solver for this harvesting study.

## Figure map

| Figure | PDF page | Content |
| --- | --- | --- |
| 1 | 1 | Duffing time series and phase portraits at γ = 0.29 |
| 2 | 1 | Duffing step-size comparison and RMSE |
| 3 | 2 | Initial-condition sensitivity and Poincaré section at γ = 0.5 |
| 4 | 2 | Representative grass/rabbit/fox population simulation |
| 5 | 2 | Fox-speed sensitivity across repeated agent-based simulations |
| 6 | 3 | Harvested Lotka–Volterra trajectories and phase portraits |

## Preservation checks

The archived PDF is byte-identical to the original downloaded from the submitted Blackboard attempt. The [submission record](../reports/submission_record.json) contains its SHA-256 and size. All three pages were rendered and inspected; the text, figures and bibliography are present. The repository records no marks or teacher feedback.

There is no code-level test suite to run for this report archive. A complete reproduction claim would require recovering or explicitly rebuilding the simulations, recording their environment and full configurations, and comparing the resulting figures and numbers with the submitted report.
