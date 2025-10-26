---
title: MUGS-SLAM, a Multi-Camera Gaussian Splatting for Robust 3D SLAM
date: 2025-05-01
links:
  - type: GitHub repo
    url: https://github.com/fgarciacardenas/multi-3dgs?tab=readme-ov-file
  - type: pdf
    url: 3D_vision_project_FINAL.pdf
    label: "Report PDF"
tags:
  - Computer Vision
  - 3D vision
  - Gaussian Splatting
---

## Overview

As result of our semester course _3D vision_, me and my team ([Elia Raimondi](https://www.linkedin.com/in/elia-raimondi/), [Luca Monegaglia](https://www.linkedin.com/in/luca-monegaglia/) and [Facundo Garcia](https://www.linkedin.com/in/facundogc/)) developed **MUGS-SLAM**, a novel multi-camera SLAM framework that leverages **3D Gaussian Splatting (3DGS)** to achieve both **photorealistic reconstruction** and **robust camera tracking**.  
Unlike traditional feature-based SLAM methods, MUGS-SLAM unifies multiple fisheye or pinhole cameras into a **single Gaussian-based map**, ensuring seamless alignment, higher accuracy, and more complete reconstructions — even in low-texture or low-light environments.
{{< download-pdf file="3D_vision_project_FINAL.pdf" text="Take a look at the final report!" >}}

## Methodology

### Multi-Camera SLAM with 3DGS

At the core of our system lies a unified 3D Gaussian representation that replaces discrete point clouds with continuous Gaussian primitives.  
Each Gaussian carries not only position and uncertainty information but also color and opacity, enabling smooth, high-quality renderings.

The system jointly optimizes camera poses and Gaussian parameters through **Bundle Adjustment**, while maintaining global consistency across cameras.  
Thanks to GPU-accelerated kernels, both fisheye and pinhole models are processed in real time.

---

### Depth Consistency: Histogram-Based Alignment

One of the key challenges in multi-camera SLAM is that **depth estimates from different cameras often have inconsistent scales**.  
This can happen because monocular depth priors depend heavily on lighting, texture, and camera calibration — leading to distortions and mismatched geometry when the maps are fused.

To solve this, we introduced a **histogram matching technique** that enforces a common depth scale across all views.  
Given a camera’s depth distribution \( D*i \) and a reference distribution \( D*{\text{ref}} \), we remap the depths as:

\[
D'_i(x) = F^{-1}_{\text{ref}}(F_i(D_i(x)))
\]

where \( F*i \) and \( F*{\text{ref}} \) are the cumulative distribution functions (CDFs).  
In simpler terms, this process ensures that all cameras share the same “depth histogram”, aligning their internal scales and improving the fusion quality.

This alignment offers three benefits:

1. **Scale Consistency** — all cameras contribute coherent geometry.
2. **Robust Fusion** — depth maps combine seamlessly without discontinuities.
3. **High-Resolution Detail** — fine structures are preserved even after alignment.

The result is a single, globally consistent Gaussian map that avoids cross-view seams and produces smooth, photorealistic reconstructions.

---

## Experiments and Results

We tested MUGS-SLAM on both **synthetic environments** generated with Habitat-Sim and **real-world data** from the **Hilti-Oxford dataset**.  
The system demonstrated superior **trajectory accuracy** and **reconstruction fidelity** compared to existing SLAM frameworks like HI-SLAM2 and BAMF-SLAM.

**Tracking Accuracy (APE RMSE):**

| Dataset | HI-SLAM2 | BAMF  | MUGS-SLAM |
| :------ | :------: | :---: | :-------: |
| room09  |  2.655   | 0.475 | **0.370** |
| room14  |  0.320   | 0.221 | **0.077** |
| exp04   |  0.847   | 0.177 | **0.126** |

**Reconstruction Quality:**

| Metric  | HI-SLAM2 | MUGS-SLAM |
| :------ | :------: | :-------: |
| PSNR ↑  |   28.7   | **30.9**  |
| SSIM ↑  |  0.867   | **0.886** |
| LPIPS ↓ |  0.357   | **0.272** |

The qualitative reconstructions show that MUGS-SLAM preserves finer geometric and textural details, producing cleaner edges and more accurate 3D surfaces, especially in complex or grayscale scenes.

---

## Contributions and Takeaways

- **Unified Multi-Camera 3DGS SLAM:** consistent mapping across multiple lenses.
- **Histogram-Based Depth Alignment:** scale-normalized priors for better fusion.
- **GPU-Accelerated Optimization:** real-time tracking and reconstruction.
- **Synthetic Dataset Pipeline:** Habitat-Sim setup for benchmarking multi-camera SLAM.

---

## Conclusion

{{< figure src="group_pic.jpg" alt="Me and my fantastic team!" caption="Me and my team at the paper presentation :) " >}}

MUGS-SLAM demonstrates how **3D Gaussian Splatting can unify mapping and localization** in a multi-camera system.  
By introducing histogram-based depth alignment and leveraging GPU efficiency, we achieved **accurate**, **realistic**, and **scalable** 3D reconstructions that bridge the gap between geometry and photorealism.
