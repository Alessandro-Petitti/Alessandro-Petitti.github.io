---
title: "Multi-Phase Model Predictive Quadrotor Contouring Control"
authors:
  - admin
  - Rudolf Reiter
  - Leonard Bauersfeld
  - Ismail Geles
  - Davide Scaramuzza

date: "2026-01-16T00:00:00Z"

# Publication type.
publication_types: ["article"]

# Publication name and optional abbreviated publication name.
publication: "Preprint"
publication_short: "Preprint"

abstract: "Agile flight with soft robotic structures such as morphologically adaptive quadrotors promises improved safety and resilience, but it poses challenges for real-time optimization: high-fidelity flexible-joint dynamics are required for stable and safe navigation, yet they are computationally too expensive to optimize over long horizons. Existing learning-based approaches often sacrifice either performance or generalization, whereas model-based model predictive contouring control (MPCC) offers strong interpretability and constraint integration when differentiable dynamics are available. We propose a multi-phase MPCC that schedules models of decreasing fidelity within a single optimal control problem. A high-fidelity flexible-joint model in differential algebraic equation (DAE) form is used near the current state, followed by rigid-body and point-mass surrogates to extend look-ahead. We derive the nonlinear program formulation, including phase-coupling transition maps and progress-consistent scheduling. In high-fidelity simulations, the proposed three-phase controller reduces average MPC step time from 120 ± 60 ms to 17.0 ± 0.2 ms and improves lap time from 3.8 ± 0.1 s to 3.4 ± 0.2 s. Real-world experiments on a rigid quadrotor demonstrate favorable trade-offs between computation time and lap time compared to a single-phase MPCC."

summary: "A multi-phase MPCC that schedules models of decreasing fidelity (flexible-joint, rigid-body, point-mass) within a single optimal control problem, enabling long-horizon agile flight of flexible-joint quadrotors in real time."

tags:
  - Model Predictive Control
  - Aerial Robotics
  - Optimal Control

featured: true

# Featured image
image:
  caption: ""
  focal_point: ""
  preview_only: false

projects: []
slides: ""
---

This work is the outcome of my semester project at the [Robotics and Perception Group](https://rpg.ifi.uzh.ch/), University of Zürich. See the [project page](/projects/semester-project/) for more details.

**Keywords:** Aerial Systems, Mechanics and Control, Optimization and Optimal Control.
