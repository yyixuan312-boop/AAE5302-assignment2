# AAE5303 Assignment 2: ORB-SLAM3 with HKisland GNSS Dataset

## 1. Assignment Overview 
This assignment focuses on running ORB-SLAM3 monocular SLAM on the HKisland_GNSS03 dataset, generating trajectory results, and evaluating SLAM performance.  

## 2. Environment Setup 
- **Runtime Environment**: Docker (ORB-SLAM3 + ROS Noetic container)
- **Core Dependencies**: OpenCV 4.5.5, Eigen3 3.4.0, Pangolin 0.6, ROS Noetic
- **Hardware**: Docker Desktop on Windows 11

## 3. Dataset Information 
- **Dataset Name**: HKisland_GNSS03.bag
- **Source**: HKU MaRS Lab Dataset ([https://mars.hku.hk/dataset.html](https://mars.hku.hk/dataset.html))
- **Dataset Type**: ROS bag (monocular camera + GNSS data)
- **Duration**: [需填充 - 填写bag文件时长，如 "390 seconds"，可通过 `rosbag info` 查看]
- **Key Topics**: `/left_camera/image/compressed` (monocular image), `/gnss/fix` (GNSS pose)

## 4. Running Steps 
### 4.1 Start ROS Core
```bash
roscore &
### 4.2 Play ROS Bag 
```bash
# --pause: Pause at start (press Space to play); Remap topic to match ORB-SLAM3 subscription
rosbag play --pause ./data/HKisland_GNSS03.bag /left_camera/image/compressed:=/camera/image_raw/compressed
