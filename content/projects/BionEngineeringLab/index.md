---
title: BioEngineering Laboratory
date: 2024-06-15

tags:
  - Biomechanics
  - Laboratoy experience
  - Bachelor project
image:
  filename: "Vestizione.jpg"
  fill_image: true
  focal_point: "Center"
---

---

## Overview

This laboratory course focused on exploring the **mechanical, biomechanical, and static properties** of biological systems.  
The project was divided into three main modules:

1. **Viscoelastic Materials**
2. **Gait Analysis**
3. **Statics and Anthropometry**

Each section combined experimental activities with theoretical modeling and data analysis to understand the physical principles behind biological motion and tissue behavior.
{{< download-pdf file="laboratorio_Bioingegneria.pdf" text="Take a look at the final report!" >}}

---

## Module I — Viscoelastic Materials

### Objective

The goal was to analyze the **mechanical behavior of biological tissues**, specifically **pig tendons**, through three mechanical tests:

- **Hysteresis test**
- **Stress relaxation test**
- **Tensile (failure) test**

### Experimental Setup

Tests were performed using an **Instron 3365 tensile machine**, capable of measuring both force and displacement.  
Each sample was fixed between clamps and subjected to controlled loading cycles at different speeds.

{{< figure src="close_up_instron.jpeg" alt="" caption="The Instron machine with the viscoelastic material in it. " >}}

---

## Module II — Gait Analysis

### Objective

To study human gait kinematics **with and without an exoskeleton**, comparing joint angles, stride parameters, and movement patterns.

### Methodology

- The experiment used the **EksoNR exoskeleton** by Ekso Bionics and **seven IMU sensors** (Xsens).
- Data were collected from the trunk, thighs, shanks, and feet, converted from **quaternions** to **rotation matrices** for joint angle computation.
- The analysis focused on **hip**, **knee**, and **ankle** motion during walking at different speeds.

{{< figure src="Vestizione.jpg" alt="" caption="IMU setup." >}}

### Key Findings

- Motion data confirmed the **periodic behavior** of the gait cycle (stance and swing phases).
- Using the exoskeleton affected stride length and timing but maintained overall gait symmetry.
- The analysis included RMSE evaluation between assisted and unassisted walking, showing consistent trends with biomechanical expectations.

---

## Module III — Statics and Anthropometry

### Objective

To evaluate **balance, posture, and force distribution** in static and quasi-static walking conditions, using anthropometric measurements.

### Approach

Participants were instrumented with reflective markers, and forces on each leg were measured using pressure platforms.  
Static equilibrium models were used to estimate the **center of mass (CoM)** and verify theoretical assumptions of human balance.

{{< figure src="marker_ale_1.jpg" alt="" caption="Optoeletronic setup." >}}

### Results

- The **CoM displacement** during quiet standing and slow walking matched theoretical predictions from the **inverted pendulum model**.
- Experimental force data confirmed proper **load sharing** between limbs and validated anthropometric tables used for modeling.

---

## Conclusions

This multidisciplinary project provided practical understanding of:

- The **viscoelastic behavior** of biological tissues;
- The **biomechanics of human gait**, both assisted and natural;
- The **static principles** governing human balance.

The experience strengthened both experimental and analytical skills, bridging the gap between **engineering mechanics** and **biomedical applications**.

---
