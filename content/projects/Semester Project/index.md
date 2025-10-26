---
title: Nonlinear Model Predictive Control for precise fast agile flight in confined spaces
date: 2025-09-15

tags:
  - Semester Project
  - Optimization based control
  - Quadrorotor
---

## Supervision

This project is conducted under the supervision of:

- [**Professor Davide Scaramuzza**](https://rpg.ifi.uzh.ch/people_scaramuzza.html)
- [**Dr. Rudolf Rieter**](https://scholar.google.com/citations?user=5VdYugYAAAAJ&hl=en)
- [**Leonard Bauersfeld**](https://lbfd.github.io/)

at the [**Robotics and Perception Group (RPG)**](https://rpg.ifi.uzh.ch/index.html), University of Zürich.

---

## Project Overview

This semester project investigates the application of **multi-phase numerical optimal control** for achieving **high-performance**, **agile flight** of a **flexible quadrotor** in confined environments.

While high-fidelity models exist for many robotic platforms, their computational complexity often prevents their use in real-time control. The goal of this project is to **develop and identify dynamic models of a flexible quadrotor** that achieve a practical trade-off between **accuracy** and **computational efficiency**.

---

## Methodology

### 1. Hybrid Control Strategy

The proposed approach combines:

- **Model Predictive Control (MPC)** with **precise numerical integration** over a short initial horizon, and
- A **simplified, lower-fidelity model** for longer-term prediction.

This hybrid setup allows maintaining **long prediction horizons**, essential for agile maneuvers such as:

- Flying through narrow gaps, and
- Navigating tight indoor environments.

{{< figure src="Adobe Express - morphy.gif" alt="Morphy drone" caption="Deformation of Morphy's arms due to thrust." >}}

---

### 2. Platform: The Morphy Drone

The experiments are conducted using the [**Morphy drone**](https://www.researchgate.net/publication/385736833_Morphy_A_Compliant_and_Morphologically_Aware_Flying_Robot), a **compliant and morphologically aware flying robot** whose arms can deform under thrust.  
This flexibility introduces new control challenges and opportunities for exploiting morphology in flight dynamics.

---

### 3. Model Development and Validation

I am currently building, simulating, and validating a **high-fidelity dynamic model** of the Morphy platform.  
Once the model is ready, I will perform **system identification** by collecting real-world flight data to accurately determine the physical parameters of the quadrotor.

---

### 4. Control Design

After model identification:

- I will design and tune a **Nonlinear Model Predictive Controller (NMPC)** within the [**ACADOS**](https://docs.acados.org/) framework.
- The controller will be evaluated in simulation for performance, stability, and robustness.

---

### 5. Real-Time Deployment

The final stage involves integrating the **full high-fidelity model** with a **simpler model** (e.g., point-mass or rigid-body approximation) to enable **real-time NMPC deployment** onboard the drone.  
This integration aims to combine the accuracy of detailed models with the responsiveness required for real-time flight control.

---

## Expected Outcomes

- A validated high-fidelity model of a flexible quadrotor.
- An efficient NMPC capable of agile flight through confined environments.
- Insights into the balance between model complexity and real-time feasibility in numerical optimal control.

---
