# AAE5303 Assignment 2: Cursor adaptation and practice for the orbSLAM3  demo to show the performance 

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
```
### 4.2 Start ROS Core
```bash
rosbag play --pause ./data/HKisland_GNSS03.bag /left_camera/image/compressed:=/camera/image_raw/compressed
```
### 4.3 Launch ORB-SLAM3 Monocular Node
```bash
rosrun ORB_SLAM3 MonoCompressed Vocabulary/ORBvoc.txt Examples/Monocular/HKisland_Mono.yaml > run_log.txt 2>&1
```
### 4.4 Execute SLAM Process
1.Press Space in the bag playback terminal to start data streaming.  
2.Check the Pangolin visualization window for normal trajectory display.  
3.Wait for bag playback completion (trajectory file auto-generated).

## 5. Results
### 5.1 File Submission List (文件补充清单)
| 文件路径 | 必须/可选 | 补充说明 |
|----------|-----------|----------|
| `groung——truth——HKisland03.txt` | 必须 | ORB-SLAM3完整运行日志（无ERROR/FATAL级报错），需上传到仓库根目录 |
| `KeyFrameTrajectory_HKisland03.txt` | 必须 | ORB-SLAM3生成的关键帧轨迹文件，需上传到仓库根目录（重命名为该名称） |
| `imgs/slam_visualization.png` | 必须 | Pangolin可视化窗口截图（需包含SLAM轨迹+特征点+终端运行状态），需上传到仓库`imgs`文件夹 |
| `results/evaluation_result.txt` | 可选 | ATE/RPE轨迹评估结果（作业要求评估则补充），需上传到仓库`results`文件夹 |
| `run_assignment2.sh` | 可选 | 一键运行脚本（包含roscore、播放bag、启动SLAM的命令），需上传到仓库根目录 |

---

### 5.2 Visualization Screenshot
![SLAM Visualization Screenshot](imgs/slam_visualization.png)
*【需补充：填写截图说明，例如 "Pangolin窗口展示HKisland场景下ORB-SLAM3的运行轨迹和特征点分布"】*

---

### 5.3 Evaluation Metrics (if applicable)
| Metric | Value | Note |
|--------|-------|------|
| Absolute Trajectory Error (ATE) - RMSE | 【需补充：填写ATE RMSE数值，例如 "0.85m"（无评估则删除此行）】 | 【需补充：填写评估说明，例如 "基于evo_ape tum计算，--t_max_diff 0.1s"（无评估则删除此行）】 |
| RPE Translation Drift (平移漂移率) | 【需补充：填写数值，例如 "0.012 m/m"（无评估则删除此行）】 | 【需补充：填写说明，例如 "基于10m窗口evo_rpe计算，RPE_trans_mean/10"（无评估则删除此行）】 |
| RPE Rotation Drift (旋转漂移率) | 【需补充：填写数值，例如 "1.5 °/100m"（无评估则删除此行）】 | 【需补充：填写说明，例如 "基于10m窗口evo_rpe计算，(RPE_rot_mean/10)*100"（无评估则删除此行）】 |
| Completeness (完整性) | 【需补充：填写百分比，例如 "92.5%"（无评估则删除此行）】 | 【需补充：填写说明，例如 "matched_poses/gt_poses*100，匹配姿态数/真值姿态数"（无评估则删除此行）】 |
