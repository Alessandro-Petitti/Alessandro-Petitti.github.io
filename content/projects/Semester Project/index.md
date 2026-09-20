---
title: Agile Flight of Flexible Drones in Confined Spaces with Multi-Phase MPC
date: 2026-01-16

tags:
  - Semester Project
  - Optimization based control
  - Quadrotor
  - Model Predictive Control
---

## Supervision

This project was carried out under the supervision of:

- [**Professor Davide Scaramuzza**](https://rpg.ifi.uzh.ch/people_scaramuzza.html)
- [**Dr. Rudolf Reiter**](https://scholar.google.com/citations?user=5VdYugYAAAAJ&hl=en)
- [**Leonard Bauersfeld**](https://lbfd.github.io/)
- **Ismail Geles**

at the [**Robotics and Perception Group (RPG)**](https://rpg.ifi.uzh.ch/index.html), University of Zürich (September 2025 – January 2026).

---

## Project Overview

The project is motivated by **Autoassess**, a Horizon Europe project that aims to replace part of the manual inspection of ship interiors with autonomous aerial robots. Ballast tanks and cargo holds are confined, cluttered, GNSS-denied, and dangerous for human surveyors, so the drones must be **fast, safe, and collision tolerant**.

This semester project develops a **multi-phase Model Predictive Contouring Control (MPCC++)** framework for agile flight of a **flexible-joint quadrotor** ([**Morphy**](https://www.researchgate.net/publication/385736833_Morphy_A_Compliant_and_Morphologically_Aware_Flying_Robot), whose arms deform under thrust). High-fidelity models capture the compliance, but they are too expensive to optimize over a long horizon in real time.

---

## Approach

The key idea is that model fidelity does not need to be uniform over the prediction horizon:

1. **Near horizon**: a high-fidelity flexible-joint model, written as a differential-algebraic equation (DAE) and integrated implicitly, stabilizes the fast internal dynamics.
2. **Mid horizon**: a rigid-body quadrotor surrogate.
3. **Far horizon**: a point-mass surrogate for cheap, long look-ahead.

All phases share a single **progress variable** and the same **track-aligned tunnel constraints**, and are coupled through deterministic **transition maps**. The resulting problem is a single nonlinear program, solved in real-time-iteration mode with the [**acados**](https://docs.acados.org/) multi-phase OCP interface.

{{< figure src="Adobe Express - morphy.gif" alt="Morphy drone" caption="Deformation of Morphy's arms due to thrust." >}}

---

## Results

- **Tracking MPC in simulation** (figure-8 track): the multi-phase formulation cut the computation time per step from **71.9 ms** (high-fidelity only) to **21.3 ms**, with a comparable tracking error (0.19 m vs 0.23 m RMSE).
- **MPCC++ in simulation** (racing circuit): the three-phase controller reduced the step time from **120 ± 60 ms to 17 ± 0.2 ms** and improved the lap time from **3.8 ± 0.1 s to 3.4 ± 0.2 s**, compared to a single-phase controller.
- **Real flight**: due to technical delays, the controller could not be deployed on Morphy itself. It was instead validated on a rigid quadrotor (Kolibri) with motion capture, flying through gates while respecting the tunnel constraints.

---

## Outcome and next steps

The work led to a preprint, [**Multi-Phase Model Predictive Quadrotor Contouring Control**](/publications/preprint/), co-authored with the supervisors above.

Open directions include reducing the high-frequency body-rate oscillations, adaptive tuning of the progress reward and tunnel weights, porting the full pipeline to Morphy, and an energy-optimal formulation.

---
