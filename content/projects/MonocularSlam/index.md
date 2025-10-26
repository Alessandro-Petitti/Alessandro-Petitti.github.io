---
title: VROOM, a Visual Robotic Odometry, Only Monocular
date: 2025-01-13
links:
  - type: GitHub repo
    url: https://github.com/fgarciacardenas/vamr-project
  - type: pdf
    url: VAMR_project_report.pdf
    label: "Download PDF"

tags:
  - Computer Vision
  - Visual Odometry
  - Vision Algorithms for Mobile Robotics
---

## Overview

As part of the class _Vision Algorithms for Mobile Robotics_, me and my team ([Francesco Banelli](https://www.linkedin.com/in/francesco-banelli/), [Facundo Garcia](https://www.linkedin.com/in/facundogc/) and [Rayan Slocum ](https://www.linkedin.com/in/ryanslocum/)), developed **VROOM**, a **monocular visual odometry (VO)** pipeline that allows a mobile robot to estimate its ego-motion and build a sparse 3D map using only a single RGB camera.
{{< download-pdf file="VAMR_project_report.pdf" text="Take a look at the final report!" >}}

## Methodology

The pipeline starts by processing the first few frames to estimate the **initial camera pose** and reconstruct the first set of 3D landmarks.  
We detect salient features using the **Harris Corner detector**, then track them across frames using **KLT optical flow**.  
By computing the **Essential Matrix** between the first and third frames, we establish the initial baseline and triangulate the first 3D points — providing a reference for subsequent motion estimation.

### 2. Keypoint Tracking

Once initialized, the system continuously tracks visual features across frames using **Kanade–Lucas–Tomasi (KLT)** optical flow.  
This method estimates pixel displacements between frames and filters out outliers automatically, maintaining a stable set of reliable feature correspondences.

### 3. Pose Estimation

At every iteration, 2D–3D correspondences are established between the currently tracked keypoints and the existing 3D landmarks.  
We solve the **Perspective-n-Point (PnP)** problem with **RANSAC** to estimate the camera’s rotation and translation, ensuring robustness to mismatches and occlusions.

### 4. Keypoint Management

Over time, some keypoints are lost due to occlusions or motion.  
To maintain sufficient coverage, we continuously introduce **candidate points** detected with Harris corners in new regions.  
If a candidate feature shows sufficient parallax relative to its first observation, it is **triangulated** and promoted to a tracked landmark.  
This dynamic update strategy keeps the map active and the tracking stable throughout the sequence.

---

## Handling Real-World Challenges

During development, several practical issues emerged:

- **Low feature count in challenging frames:** strong contrast transitions (e.g., outdoor-to-indoor) caused feature detectors to fail. We addressed this by adapting Harris detector thresholds dynamically per frame.
- **Uneven keypoint distribution:** features tended to cluster in salient regions. By adjusting detection parameters and enforcing spatial diversity, we improved coverage and reduced drift.
- **Dataset variability:** the KITTI, Parking, and Málaga datasets required different parameter sets. We managed them using a **parameter dictionary**, allowing flexible tuning per dataset.

---

## Depth Scale Limitation

Since VROOM is purely **monocular**, absolute scale cannot be recovered directly.  
We observed that scale drift is a major source of trajectory error.  
By initializing the system with the true scale factor (from ground truth), the estimated trajectories aligned almost perfectly.  
The system’s accuracy could be further improved by fusing inertial measurements or stereo depth information.

In mathematical terms, monocular systems can only estimate motion **up to scale**:
\[
T' = s \, T
\]
where \( s \) is an unknown scalar factor.  
Without additional cues, this leads to long-term drift in metric scale.

---

## Experimental Results

We tested VROOM on three datasets:

| Dataset     | Description                     | Performance Summary                                                                               |
| :---------- | :------------------------------ | :------------------------------------------------------------------------------------------------ |
| **KITTI**   | Outdoor urban driving           | Accurate local motion; minor drift after ~600 frames due to loss of texture and shadowed regions. |
| **Parking** | Indoor–outdoor transition       | Stable tracking after adaptive parameter tuning; drift mainly due to initial scale error.         |
| **Málaga**  | Urban scenario, no ground truth | Maintained local consistency; parameters transferred well from KITTI.                             |

Across all datasets, the pipeline achieved **locally consistent trajectories** and demonstrated good robustness to viewpoint changes.

---

## Lessons Learned

- **Feature diversity** is essential for maintaining robustness. Using multiple detection thresholds increased resilience to lighting and motion changes.
- **Adaptive parameter tuning** was critical — a fixed configuration cannot generalize across all datasets.
- The system, while lightweight, shows **competitive local performance** comparable to other monocular-only VO approaches.

---

## Conclusion

**VROOM** successfully demonstrates the feasibility of estimating robot motion and reconstructing 3D structure using a single monocular camera.  
Although inherently limited by the lack of absolute scale and loop closure, the system achieves strong **local accuracy** and **stable tracking** across varied environments.

Future extensions could include:

- Scale correction through stereo or IMU fusion.
- Loop closure and global optimization for long-term drift correction.
- Integration with visual-inertial odometry frameworks for real-time applications.

---

## Repository

Code and documentation are available at:  
👉 [https://github.com/fgarciacardenas/vamr-project](https://github.com/fgarciacardenas/vamr-project)

Video demonstrations:

- [KITTI](https://youtu.be/TVpDT9qPGPo)
- [Parking](https://youtu.be/AIJnRkeZyp8)
- [Málaga](https://youtu.be/IEy_toepZIE)
