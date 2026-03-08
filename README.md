# AAE5303 Assignment: Visual Odometry with ORB-SLAM3
This repository contains the implementation and analysis of monocular visual odometry using the ORB-SLAM3 framework on the HKisland_GNSS03 UAV aerial imagery dataset.

---

## Key Results
| Metric          | Value           | Description                                  |
|-----------------|-----------------|----------------------------------------------|
| ATE RMSE        | 1.373 m         | Global accuracy after Sim(3) alignment       |
| RPE Trans Drift | 4.02 m/m        | Translation drift rate (delta=10 m)          |
| RPE Rot Drift   | 147.83 deg/100m | Rotation drift rate (delta=10 m)            |
| Completeness    | 4.81%           | Matched poses / total ground-truth poses     |

---

## Introduction
ORB-SLAM3 is a state-of-the-art visual SLAM system capable of monocular, stereo, and visual-inertial odometry.

This assignment focuses on Monocular VO mode, which:
- Uses only camera images for pose estimation
- Cannot observe absolute scale (scale ambiguity)
- Relies on feature matching (ORB features) for tracking

---

## Methodology
### Evaluation Metrics
1. **ATE (Absolute Trajectory Error)**: Measures global trajectory accuracy after Sim(3) alignment
2. **RPE Translation Drift**: Local translation consistency (error per meter traveled)
3. **RPE Rotation Drift**: Local rotation consistency (error per 100 meters)
4. **Completeness**: Percentage of ground-truth poses successfully matched

---

## Dataset Description
### HKisland_GNSS03 Dataset
| Property         | Value                          |
|------------------|--------------------------------|
| Dataset Name     | HKisland_GNSS03                |
| Source           | MARS-LVIG / UAVScenes          |
| Duration         | ~361 seconds (~6.0 minutes)    |
| Image Resolution | 2448 × 2048 pixels             |
| Frame Rate       | ~10 Hz                         |
| Ground-truth Type| RTK GPS (centimeter-level accuracy) |
| Ground-truth Rate| 5 Hz                           |
| Ground-truth Poses | 1955                          |

### Ground Truth
RTK GPS provides centimeter-level positioning accuracy at 5 Hz, with a total of 1955 poses for quantitative evaluation.

---

## Implementation Details
### System Configuration
| Component   | Specification                          |
|-------------|----------------------------------------|
| Framework   | ORB-SLAM3 (C++)                        |
| Mode        | Monocular Visual Odometry              |
| Vocabulary  | ORBvoc.txt                             |
| OS          | Ubuntu 22.04 via WSL2                  |

### Camera Calibration
Camera.fx: 1444.43
Camera.fy: 1444.34
Camera.cx: 1179.58
CameraC.cy: 1844.98
Camera.k1: -0.0560
Camera.k2: 0.0000
