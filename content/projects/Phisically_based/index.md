---
title: Morphy-ImpactSim, Physically-Based Collisions for a Compliant Multicopter
date: 2025-10-30
links:
  - type: pdf
    url: PBS_proposal.pdf
    label: "Project Proposal PDF"
tags:
  - Simulator build
  - Physics Simulation
  - Multibody Dynamics
  - Aerial Robots
---

## Overview

As part of a simulation-oriented project, me and my teammates (**Gennaro Guidone**, **Luca Monegaglia**) are designing **Morphy-ImpactSim**, a small but complete framework to **simulate the impact of a compliant drone (Morphy) against rigid surfaces**.

The goal is to move past the “perfectly rigid quadrotor” assumption and model a vehicle whose **arms can actually flex and absorb energy** through elastic joints. This makes it possible to study **safety**, **damage mitigation**, and **morphological adaptation** of small aerial robots without needing to crash a real platform every time.

{{< download-pdf file="PBS_proposal.pdf" text="Read the original proposal" >}}

---

## System Model

### A multibody Morphy

We represent the drone as:

- **1 central rigid body** (the main fuselage);
- **4 arm–motor–prop assemblies**, each treated as a **separate rigid body**;
- **4 compliant joints** between body and arms, modeled as **rotational spring–dampers**.

This lets the simulator reproduce typical post-impact behaviors:

- some arms deflect more than others,
- part of the impact energy is dissipated in the joints,
- the main body can rotate or slightly lift again.

We intentionally keep the model **control-free and aerodynamics-free**: the focus of the project is **impact physics**, not flight.

---

## Collision Handling

A key part of the project is **comparing two contact strategies** on the very same scenario:

1. **Impulse-based contact**

   - Predict unconstrained motion
   - Detect collisions w.r.t. a plane or object
   - Apply an instantaneous velocity correction
   - Fast and simple → good as a baseline
   - Easy to visualize and debug

2. **Smooth / IPC-style contact**
   - Contact is formulated as an energy / barrier term
   - Solved with implicit integration
   - More stable for multiple or deep contacts
   - Easier to extend to moving objects or richer scenes

Showing both methods makes the project look **engineering-oriented** (baseline) and **research-friendly** (variational / IPC).

---

## Scenarios

- **Base scenario:** drone in free fall → impact on a rigid horizontal plane → rebound + arm oscillations.
- **Extended scenario:** drone hits a **second object** (e.g. a box), transfers momentum, and the second object starts moving.
- **What-if tests:** change joint stiffness and damping to see how much energy is absorbed vs. bounced back.

This progression (plane → plane + compliance → moving obstacle) is exactly what we want to show on the website: **same model, richer contacts.**

---

## Deliverables

- ✅ **Multibody Morphy model** (central body + 4 compliant arms)
- ✅ **Geometry/URDF-style description** to visualize kinematics
- ✅ **Plane contact module** with impulse response
- ✅ **Second contact method (IPC-like) for comparison**
- ➕ **Optional moving-object collision** to test momentum transfer

---

## Why it Matters

- **Safer aerial robots**: compliant structures survive impacts better.
- **Design feedback**: we can tune spring/damper values in simulation before building hardware.
- **Reusable pipeline**: the very same simulator can later be connected to a controller or to a learning agent.
- **Bridges graphics and robotics**: we reuse standard articulated rigid-body ideas, but for a drone.

---

## Conclusion

**Morphy-ImpactSim** is a compact, clear project that shows how to:

1. model a **non-rigid / compliant** aerial platform,
2. run **physically meaningful impacts**,
3. and **compare two contact formulations** on identical data.

It’s a good example of “simulation-first” robotics: start from the physics, then add control.
