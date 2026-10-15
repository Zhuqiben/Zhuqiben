<div align="center">

# 你好，我是 soo 👋

### 机器人感知算法工程师 · Robot Perception Engineer

计算机视觉 · ROS 1 / ROS 2 · 嵌入式部署 · 仿真到真机落地

[个人博客](https://zhuqiben.github.io/blog/) · [精选项目](#精选项目--selected-projects) · [联系方式](#联系方式--contact)

</div>

---

## 关于我 · About me

我是一名机器人感知算法开发者，专注于机器人感知、计算机视觉、深度学习、嵌入式部署，以及从仿真到真机的完整落地。<br>
I am a robot perception developer focused on robot perception, computer vision, deep learning, edge deployment, and simulation-to-real applications.

- 🔭 聚焦方向：机器人感知 · 计算机视觉 · 边缘端部署
- 🎯 求职方向：机器人感知 / 计算机视觉算法 / 嵌入式视觉部署
- 🧩 工程闭环：覆盖「数据准备 → 训练 → 轻量化 → 真机联调」全流程
- 📝 记录习惯：通过开源项目与博客沉淀实践与学习

<br>

- 🔭 Focus: robot perception · computer vision · edge deployment
- 🎯 Target roles: robot perception / computer vision algorithms / embedded vision deployment
- 🧩 Engineering loop: data preparation → training → optimization → on-device integration
- 📝 Habit: documenting practical work through open-source projects and blog posts

## 教育背景 · Education

**东莞理工学院 · 机电工程（本科）**　2021.09 – 2025.06<br>
**Dongguan University of Technology · Mechanical and Electrical Engineering (B.Eng.)**　2021.09 – 2025.06

- 核心课程：计算机视觉、人工智能、机器学习、数据结构、数字图像处理
- 自修方向：机器人控制基础、ROS 开发、大模型 + 机器人决策
- 语言能力：大学英语四级（CET-4）

<br>

- Core courses: Computer Vision, Artificial Intelligence, Machine Learning, Data Structures, Digital Image Processing
- Self-study: robot control fundamentals, ROS development, LLM + robot decision making
- Language: CET-4

## 专业技能 · Skills

| 方向 · Area | 内容 · Details |
| --- | --- |
| 机器人框架 · Robotics | ROS 1 / ROS 2（DDS、Action、Lifecycle Node）、Topic / Service 通信、功能包工程化 |
| 仿真与 Sim2Real · Simulation | Webots、Gazebo；关注仿真与真机在传感器噪声、通信延迟上的差异，具备迁移意识 |
| 计算机视觉 · Computer Vision | 目标检测（YOLO / Faster R-CNN）、人脸识别与跟踪（LBPH + 卡尔曼滤波）、视线追踪 |
| 嵌入式部署 · Edge Deployment | Jetson Nano、树莓派、Linux；模型轻量化与 ONNX 推理加速 |
| 编程与框架 · Programming | Python、PyTorch、C++（基础）、MATLAB |
| 工具链 · Toolchain | OpenCV、MAVLink、Tkinter、Git、GitHub Pages |

## 精选项目 · Selected projects

基于 ROS 2 的车道线跟随功能包：[lane_driving](https://github.com/Zhuqiben/lane_driving) · Python / ROS 2 / OpenCV<br>
ROS 2 lane-following package: [lane_driving](https://github.com/Zhuqiben/lane_driving) · Python / ROS 2 / OpenCV

驾驶员监控系统：视线估计（MPIIGaze / MPIIFaceGaze）+ YOLO 目标检测（face / phone）+ 疲劳分心分析（EAR / MAR），含 Tkinter 桌面界面与完整训练教程：[Gaze-DMS](https://github.com/Zhuqiben/Gaze-DMS) · Python / PyTorch / ONNX / Tkinter<br>
Driver monitoring prototype: gaze estimation (MPIIGaze / MPIIFaceGaze) + YOLO object detection (face / phone) + fatigue and distraction analysis (EAR / MAR), with a Tkinter desktop UI and a full training guide: [Gaze-DMS](https://github.com/Zhuqiben/Gaze-DMS) · Python / PyTorch / ONNX / Tkinter

MPIIGaze 与 MPIIFaceGaze 的非官方 PyTorch 实现，可延伸至驾驶员监控与人机交互（注视跟随）场景：[pytorch_mpiigaze](https://github.com/Zhuqiben/pytorch_mpiigaze) · Python / PyTorch<br>
Unofficial PyTorch implementation of MPIIGaze and MPIIFaceGaze, applicable to driver monitoring and human-robot interaction (gaze following): [pytorch_mpiigaze](https://github.com/Zhuqiben/pytorch_mpiigaze) · Python / PyTorch

中英文双语博客与作品集站点：原生 HTML/CSS/JavaScript 构建，通过 GitHub Pages 发布，内容与页面分离管理：[blog](https://github.com/Zhuqiben/blog) · HTML / CSS / JavaScript<br>
Bilingual blog and portfolio site built with vanilla HTML/CSS/JavaScript and published on GitHub Pages, with content separated from presentation: [blog](https://github.com/Zhuqiben/blog) · HTML / CSS / JavaScript

## 竞赛与实践 · Competitions & practice

机器人仿真视觉项目：使用 YOLO 在 Webots 中实现动态目标检测与跟踪，推理速度达到 20 FPS 以上 · YOLO / ROS / Webots<br>
Robot simulation vision project: real-time object detection and tracking with YOLO in Webots, reaching over 20 FPS · YOLO / ROS / Webots

无人机人脸识别跟踪系统（论文发表）：使用 LBPH 与卡尔曼滤波构建树莓派/Pixhawk 感知与控制闭环 · OpenCV / MAVLink<br>
Drone face recognition and tracking system (published paper): a Raspberry Pi/Pixhawk perception and control loop using LBPH and Kalman filtering · OpenCV / MAVLink

大模型 + 机器人决策 / Sim2Real 专项：调用 GPT-4V 解析自然语言指令完成 LLM → /cmd_vel 的仿真对接，并在 Webots / Gazebo 中对比仿真与真机的摩擦力、延迟差异 · LLM / Gazebo<br>
LLM-driven robot decision making / Sim2Real study: parsing natural-language commands with GPT-4V into LLM → /cmd_vel simulation control, and comparing friction and latency differences between Webots / Gazebo and real robots · LLM / Gazebo

## 竞赛荣誉 · Honors

- 2023 国际自主智能机器人大赛 · 人形机器人现实世界标准赛 · **一等奖**<br>
  2023 International Autonomous Intelligent Robot Competition · Humanoid Robot Real-World Standard Track · **First Prize**
- 2022 国际自主智能机器人大赛 · 机器人仿真赛 · **三等奖**<br>
  2022 International Autonomous Intelligent Robot Competition · Robot Simulation Track · **Third Prize**
- Kaggle 竞赛铜牌 · UM - Game-Playing Strength of MCTS Variants（[查看认证](https://www.kaggle.com/certification/competitions/qibensu/um-game-playing-strength-of-mcts-variants)）<br>
  Kaggle Competition Bronze Medal · UM - Game-Playing Strength of MCTS Variants（[certification](https://www.kaggle.com/certification/competitions/qibensu/um-game-playing-strength-of-mcts-variants)）

## 联系方式 · Contact

- 📧 邮箱 / Email：[zhuqibensu@proton.me](mailto:zhuqibensu@proton.me)
- 🐙 GitHub：[@Zhuqiben](https://github.com/Zhuqiben)
- 📝 博客 / Blog：[zhuqiben.github.io/blog](https://zhuqiben.github.io/blog/)
- 📊 Kaggle：[qibensu](https://www.kaggle.com/qibensu)

## 技术栈 · Tech Stack

![Python](https://img.shields.io/badge/Python-3776AB?style=flat-square&logo=python&logoColor=white)
![PyTorch](https://img.shields.io/badge/PyTorch-EE4C2C?style=flat-square&logo=pytorch&logoColor=white)
![ROS 2](https://img.shields.io/badge/ROS_2-22314E?style=flat-square&logo=ros&logoColor=white)
![OpenCV](https://img.shields.io/badge/OpenCV-5C3EE8?style=flat-square&logo=opencv&logoColor=white)
![ONNX](https://img.shields.io/badge/ONNX-005CED?style=flat-square&logo=onnx&logoColor=white)
![C++](https://img.shields.io/badge/C++-00599C?style=flat-square&logo=cplusplus&logoColor=white)
![MATLAB](https://img.shields.io/badge/MATLAB-0076A8?style=flat-square&logo=mathworks&logoColor=white)
![Linux](https://img.shields.io/badge/Linux-FCC624?style=flat-square&logo=linux&logoColor=black)
![Git](https://img.shields.io/badge/Git-F05032?style=flat-square&logo=git&logoColor=white)
