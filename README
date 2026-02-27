# AAE5303 Assignment 2: ORB-SLAM3 with HKisland GNSS Dataset

## 1. Assignment Overview (作业概述)
This assignment focuses on running ORB-SLAM3 monocular SLAM on the HKisland_GNSS03 dataset, generating trajectory results, and evaluating SLAM performance.  
（本次作业核心为在 HKisland_GNSS03 数据集上运行 ORB-SLAM3 单目SLAM，生成轨迹结果并评估SLAM性能。）

## 2. Environment Setup (环境配置)
- **Runtime Environment**: Docker (ORB-SLAM3 + ROS Noetic container)
- **Core Dependencies**: OpenCV 4.5.5, Eigen3 3.4.0, Pangolin 0.6, ROS Noetic
- **Hardware**: [需填充 - 填写运行硬件，如 "Intel i7-12700H + 16GB RAM" 或 "Docker Desktop on Windows 11"]

## 3. Dataset Information (数据集信息)
- **Dataset Name**: HKisland_GNSS03.bag
- **Source**: HKU MaRS Lab Dataset ([https://mars.hku.hk/dataset.html](https://mars.hku.hk/dataset.html))
- **Dataset Type**: ROS bag (monocular camera + GNSS data)
- **Duration**: [需填充 - 填写bag文件时长，如 "390 seconds"，可通过 `rosbag info` 查看]
- **Key Topics**: `/left_camera/image/compressed` (monocular image), `/gnss/fix` (GNSS pose)

## 4. Running Steps (运行步骤)
### 4.1 Start ROS Core
```bash
roscore &
