---
title: "Master Thesis: Simulation as a Supervision Engine for Learning Soft Object Manipulation"
date: 2026-09-20

tags:
  - Master Thesis
  - Soft Robotics
  - Simulation
  - Model Predictive Control
  - Learning
---

## Supervision

My master thesis (October 2026 – April 2027, full-time) is carried out at the [**Soft Robotics Lab**](https://srl.ethz.ch/), ETH Zürich, under the supervision of:

- [**Prof. Robert Katzschmann**](https://srl.ethz.ch/)
- **Manuel Mekkattu**

---

## Project Overview

Learning-based manipulation of deformable objects is caught between simulation speed and physical accuracy: fast solvers train policies that do not transfer, while high-fidelity solvers are far too expensive for the sample budgets that reinforcement learning demands.

This thesis treats **simulation fidelity as a design variable of the learning pipeline** rather than a fixed property of the environment. It builds on **SORS**, the lab's GPU-accelerated FEM soft-body simulator with Lagrange-multiplier contact and IPC friction, and builds the numerical machinery that makes learning from an expensive simulator viable.

---

## Planned Work

1. **Batched learning environment**: wrap the coupled Franka and soft-object digital twin as a GPU environment where solver tier, mesh resolution, friction model and timestep are runtime parameters.
2. **High-fidelity simulation as a privileged expert**: solve the manipulation task offline with **trajectory optimization and MPC**, with full access to the FEM state.
3. **Policy distillation**: distill the expert into a fast closed-loop policy that only sees deployable observations, and identify by ablation which physical cues it actually needs.
4. **Adaptive-fidelity training** (extension): switch between a fast solver tier and the high-fidelity contact tier online, and characterize the fidelity-compute Pareto front.
5. **Sim-to-real deployment** on a Franka arm, reporting the sim-to-real gap for each fidelity setting.

---

## Expected Outcomes

- A reusable batched GPU learning environment with simulation fidelity as a controllable parameter.
- A privileged-expert-to-policy pipeline showing that high-fidelity simulation improves the learning workflow, and not only the environment.
- Quantitative sim-to-real results on a deformable-object manipulation benchmark (such as O-ring seating, rubber-band placement or cable routing into clips).

---
