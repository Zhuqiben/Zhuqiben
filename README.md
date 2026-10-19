<div align="center">

# 你好，我是 soo 👋

### 机器人软件工程师 · 感知算法 · Robot Software Engineer (Perception)

计算机视觉 · ROS 1 / ROS 2 · EKF-SLAM 与 Nav2 · 嵌入式部署 · 仿真到真机

[个人博客](https://zhuqiben.github.io/blog/) · [精选项目](#精选项目--selected-projects) · [工作与实验室经历](#工作与实验室经历--experience) · [邮箱](mailto:zhuqibensu@proton.me)

</div>

---

## 关于我 · About me

我是一名机器人感知开发者，专注于机器人感知、计算机视觉、深度学习、嵌入式部署，以及从仿真到真机的完整落地。
习惯用可复现的测量数据替代主观描述。<br>
I am a robot perception developer focused on robot perception, computer vision, deep learning, edge deployment, and simulation-to-real applications.
I prefer reproducible measurements over subjective descriptions.

- 聚焦方向：机器人感知 · 计算机视觉 · 边缘端部署
- 工程闭环：数据准备 → 训练 → 轻量化 → 真机联调
- 验证习惯：随机种子可复现、指标落盘、CI 守门
- 沉淀方式：开源仓库 + 双语博客

<br>

- Focus: robot perception · computer vision · edge deployment
- Loop: data preparation → training → optimization → on-device integration
- Validation: seeded and reproducible, metrics written to disk, CI as a gate
- Habit: open-source repositories plus a bilingual blog

## 精选项目 · Selected projects

**ROS 2 EKF-SLAM 地标导航仿真系统：[BEACON](https://github.com/Zhuqiben/beacon)** · ROS 2 Humble / Gazebo Classic / Nav2 / Python<br>
TurtleBot 3 在 Gazebo 场地中识别彩色地标，用纯 numpy 的 EKF-SLAM 滤波器建图，再由 Nav2 导航到指定颜色处，并在两个游走方块之间重新规划；9 个功能包覆盖感知、建图、导航与性能监控。

- **实测数据**：8 次固定种子任务（5 个世界种子 × 4 种目标色）全部成功，单程 15.3–36.3 s、路径 1.6–3.1 m；定位误差 RMS 2.5–7.8 cm（均值 4.6 cm），航向 RMS 均值 1.0°，地标估计误差均值 8.1 cm
- **连续任务**：一次启动、一张地图内连跑四种颜色 —— 障碍静止时 16.8 m / 204 s、RMS 6.0 cm；两个方块以 0.6 m/s 游走时 17.1 m / 212 s、RMS 6.5 cm，4/4 到达且零碰撞
- **延迟分解**：检测 ≈49 ms（约 20 Hz）、EKF-SLAM 4.6 ms、位姿桥 4.3 ms（p50），瓶颈明确落在检测端
- **验证体系**：94 个纯逻辑层 pytest 用例（EKF / 坐标变换 / 碰撞计数 / 颜色判定）+ flake8 / shellcheck / colcon build CI；随机场景由 `world_seed` 决定，结果可复现

🏁 [四色连续任务动图](https://github.com/Zhuqiben/beacon/blob/main/docs/media/gifs/gif_mission_dynamic.gif) · 📊 [测量数据与图表](https://github.com/Zhuqiben/beacon/tree/main/docs/media)

**ROS 2 EKF-SLAM landmark navigation in simulation：[BEACON](https://github.com/Zhuqiben/beacon)** · ROS 2 Humble / Gazebo Classic / Nav2 / Python<br>
A TurtleBot 3 detects coloured landmarks in a Gazebo arena, maps them with a pure-numpy EKF-SLAM filter, then drives to a requested colour with Nav2, re-planning between two roaming cubes; nine packages span perception, mapping, navigation and performance monitoring.

- **Measured**: 8 seeded missions (5 world seeds × 4 goal colours), 8/8 success, 15.3–36.3 s and 1.6–3.1 m per leg; localisation RMS 2.5–7.8 cm (mean 4.6 cm), mean heading RMS 1.0°, landmark map error 8.1 cm
- **Back-to-back**: four goals in one launch and one map — 16.8 m in 204 s at 6.0 cm RMS with static obstacles, 17.1 m in 212 s at 6.5 cm RMS with both cubes roaming at 0.6 m/s, 4/4 reached and no contact
- **Latency breakdown**: detector ≈49 ms (≈20 Hz), EKF-SLAM 4.6 ms, pose bridge 4.3 ms at p50 — the detector is the bottleneck
- **Validation**: 94 logic-layer pytest cases (EKF, frame transforms, collision tally, colour decision) plus a flake8 / shellcheck / colcon build CI; arenas are generated from `world_seed`, so results are reproducible

**驾驶员监控系统：[Gaze-DMS](https://github.com/Zhuqiben/Gaze-DMS)** · Python / PyTorch / ONNX / YOLO / Tkinter<br>
融合视线、头部姿态与行为信号判定驾驶员状态的桌面原型，仓库自带权重与相机标定，摄像头与离线视频均可运行。

- **感知链路**：RetinaFace（ONNX）人脸检测 + 68 点特征点与头部姿态、YOLO（`face` / `phone`）行为检测、MPIIGaze / MPIIFaceGaze 视线估计
- **状态判定**：EAR / MAR 疲劳指标、头部偏转分心判据与手机使用检测多路融合，输出统一状态提示
- **工程化**：PyTorch 训练 → ONNX 导出（`convert_to_onnx.py`）→ 端侧推理；`TRAINING.md` 记录数据集准备、四个模型的训练与评估全流程
- **开源合规**：自有代码 GPL-3.0，`THIRD_PARTY_NOTICES.md` 逐项列出上游（YOLOR GPL-3.0、OpenSeeFace BSD-2、Pytorch_Retinaface MIT、hysts/pytorch_mpiigaze MIT），受限模型改为脚本下载而非随仓库分发

**Driver monitoring prototype：[Gaze-DMS](https://github.com/Zhuqiben/Gaze-DMS)** · Python / PyTorch / ONNX / YOLO / Tkinter<br>
A desktop prototype that fuses gaze, head pose and behavioural cues into a driver-state verdict, shipping with its own weights and camera calibration and running from either a live camera or an offline video.

- **Perception**: RetinaFace (ONNX) face detection with 68 landmarks and head pose, YOLO behaviour detection (`face` / `phone`), MPIIGaze / MPIIFaceGaze gaze estimation
- **State logic**: EAR / MAR fatigue measures, head-yaw distraction cues and phone-use detection fused into a single state prompt
- **Engineering**: PyTorch training → ONNX export (`convert_to_onnx.py`) → on-device inference, with `TRAINING.md` covering dataset preparation, all four model trainings and evaluation
- **Licensing**: own code under GPL-3.0, upstream provenance itemised per component in `THIRD_PARTY_NOTICES.md`, restricted models fetched by script instead of redistributed

**基于 ROS 2 的车道线跟随功能包：[lane_driving](https://github.com/Zhuqiben/lane_driving)** · ROS 2 / Python / OpenCV / PID<br>
订阅相机图像检测车道线，经 PID 计算转向量后向 `/controller/cmd_vel` 下发速度指令，形成感知—控制闭环。

- **节点设计**：相机话题与启动状态参数化（默认 `depth_cam/rgb0/image_raw`），调试图像发布到私有话题 `~/image_result`
- **安全退出**：提供 `/lane_driving_node/exit`（`std_srvs/Trigger`）服务，退出时补发零速度指令，避免失控
- **部署适配**：`need_compile` 开关在「包索引查找」与「源码路径解析」两种模式间切换，便于仿真与真机切换调试

**ROS 2 lane-following package：[lane_driving](https://github.com/Zhuqiben/lane_driving)** · ROS 2 / Python / OpenCV / PID<br>
Detects lane lines from camera images, computes steering with PID and publishes velocity commands to `/controller/cmd_vel`, closing the perception-control loop.

- **Node design**: camera topic and start state are parameters (default `depth_cam/rgb0/image_raw`); debug frames go to the private topic `~/image_result`
- **Safe shutdown**: a `/lane_driving_node/exit` (`std_srvs/Trigger`) service publishes a zero-velocity command on exit
- **Deployment**: a `need_compile` switch selects between package-index lookup and source-tree paths, so the same node runs in simulation and on the real robot

**赛道视觉识别 · 国际自主智能机器人大赛实物赛：[qiben](https://github.com/Zhuqiben/qiben)** · Python / Keras / TensorFlow / OpenCV<br>
2023 年国际自主智能机器人大赛实物赛的机器人代码，用卷积分类网络识别赛道地面图案，反推机器人所处关卡并触发对应任务程序。

- **感知方案**：自采赛道地面图数据集（`corner` / `end` / `grass` / `mine` / `pit` / `red_brick` 六类），Keras + TensorFlow 训练分类模型并导出 `h5` 权重
- **决策链路**：地面图案识别 → 定位机器人所在关卡 → 执行对应关卡程序（过桥、开门、绕坑、采草莓等）
- **架构取舍**：客户端负责采集、终端负责推理并回传结果，规避树莓派端算力不足
- **现场适配**：按赛场光照与地面材质分场景整理脚本，便于赛后复盘与二次适配

**Track-pattern recognition, physical track of the International Autonomous Intelligent Robot Competition：[qiben](https://github.com/Zhuqiben/qiben)** · Python / Keras / TensorFlow / OpenCV<br>
The robot code for the 2023 physical competition, using a convolutional classifier to recognise track ground patterns, infer which level the robot is on and trigger the matching task program.

- **Perception**: a self-collected track dataset of six ground classes (`corner` / `end` / `grass` / `mine` / `pit` / `red_brick`), trained with Keras + TensorFlow and exported as an `h5` model
- **Decision chain**: ground pattern → current level → level-specific routine (bridge, door, pit, strawberry picking)
- **Architecture**: the client collects frames while a terminal host runs inference and returns the result, working around the Raspberry Pi's limited compute
- **Field readiness**: scripts are grouped by venue lighting and floor material for post-competition review and re-use

## 工作与实验室经历 · Experience

**某机器人教育硬件公司 · ROS 系统开发工程师**　2026.06 – 至今<br>
**ROS System Engineer, robotics education hardware company**　Jun 2026 – Present

- 负责 ROS 系列机器人产品的开发与测试，含 RDK 开发板平台上的产品迁移与适配
- 承接客户定制项目：需求拆解 → ROS 节点实现 → 联调交付
- 撰写技术文档与部署说明，沉淀可复用的调试流程
- _（待补充：可量化数字 —— 客户项目数 / 适配产品型号数 / 文档篇数）_

**高校机电创新实验室 · ROS / 视觉方向 实验室总负责人**　2021.12 – 2025.06<br>
**Head of ROS / Vision Lab, university mechatronics lab**　Dec 2021 – Jun 2025

- _（待补充：团队规模 / 主导技术方向 / 带教人数 / 可量化产出）_

**高校科技创新研究院 · 实习生**　2022.05 – 2023.09<br>
**Intern, university science & technology innovation institute**　May 2022 – Sep 2023

- Scratch 图形化编程上位机开发，支撑教学场景的课程与示例
- ROS 机器人研发与测试，参与样机功能验证

## 专业技能 · Skills

| 方向 · Area | 内容 · Details |
| --- | --- |
| 机器人框架 · Robotics | ROS 1 / ROS 2（DDS、Action、Lifecycle Node）、Topic / Service 通信、功能包工程化 |
| SLAM 与导航 · SLAM & Navigation | EKF-SLAM（里程计预测、卡方门限数据关联）、Nav2、TF、OccupancyGrid 建图、Gazebo 仿真 |
| 仿真与 Sim2Real · Simulation | Webots、Gazebo Classic；关注传感器噪声、通信延迟差异与参数迁移 |
| 计算机视觉 · Computer Vision | 目标检测（YOLO / Faster R-CNN）、图像分类（CNN / Keras）、人脸识别与跟踪（LBPH + 卡尔曼滤波）、视线估计（MPIIGaze / MPIIFaceGaze） |
| 嵌入式部署 · Edge Deployment | Jetson Nano、树莓派、RDK 开发板、Linux；模型轻量化与 ONNX 推理加速 |
| 编程与框架 · Programming | Python、PyTorch、TensorFlow / Keras、C++（基础）、MATLAB |
| 工具链 · Toolchain | OpenCV、ONNX Runtime、MAVLink、Tkinter、Git、GitHub Actions、GitHub Pages |

## 竞赛与荣誉 · Competitions & Honors

- **2023 国际自主智能机器人大赛 · 人形机器人现实世界标准赛 · 一等奖**<br>
  First Prize, 2023 International Autonomous Intelligent Robot Competition — Humanoid Real-World Standard Track
- **2023 国际自主智能机器人大赛 · 机器人仿真赛 · 三等奖**<br>
  Third Prize, 2023 — Robot Simulation Track
- **2022 国际自主智能机器人大赛 · 机器人仿真赛 · 三等奖**<br>
  Third Prize, 2022 — Robot Simulation Track
- **2022 机械创新大赛 · 省赛 · 三等奖**<br>
  Third Prize, 2022 Provincial Mechanical Innovation Competition
- **Kaggle 竞赛铜牌 · UM - Game-Playing Strength of MCTS Variants**（[认证](https://www.kaggle.com/certification/competitions/qibensu/um-game-playing-strength-of-mcts-variants)）<br>
  Kaggle Competition Bronze Medal — UM: Game-Playing Strength of MCTS Variants

**相关实践 · Related practice**

- **无人机人脸识别与跟踪系统（论文发表）**：LBP 特征级联分类器 + LBPH 直方图实现特定人脸实时识别，卡尔曼滤波补偿遮挡与运动偏移，结果经 MAVLink 回传飞控形成跟随闭环 · OpenCV / MAVLink / 树莓派 / Pixhawk
- **大模型 + 机器人决策 / Sim2Real 专项**：GPT-4V 解析自然语言指令并对接 `/cmd_vel`，在 Webots / Gazebo 中对比仿真与真机的摩擦力、延迟差异并尝试 PID 补偿 · LLM / Gazebo

## 教育背景 · Education

**某省属理工类本科院校 · 机电工程（本科）**　2021.09 – 2025.06<br>
**Provincial polytechnic university · Mechanical and Electrical Engineering (B.Eng.)**　Sep 2021 – Jun 2025

- 核心课程：计算机视觉、人工智能、机器学习、数据结构、数字图像处理
- 自修方向：机器人控制基础、ROS 开发、大模型 + 机器人决策
- 毕业设计：基于人眼视线追踪的驾驶员监控系统，Jetson Nano 端到端部署，单帧延迟 ≤ 50 ms

<br>

- Core courses: Computer Vision, Artificial Intelligence, Machine Learning, Data Structures, Digital Image Processing
- Self-study: robot control fundamentals, ROS development, LLM-based robot decision making
- Thesis: driver monitoring via eye-gaze tracking, deployed end-to-end on Jetson Nano at ≤50 ms per frame

## 其他仓库 · Other repositories

- [blog](https://github.com/Zhuqiben/blog) — 中英双语博客与作品集站点，原生 HTML/CSS/JavaScript，项目与文章数据集中在 `data.js`，GitHub Pages 发布，附单元测试
- [Zhuqiben](https://github.com/Zhuqiben/Zhuqiben) — 本主页仓库

> 视线估计部分的训练与评估流程源自 [hysts/pytorch_mpiigaze](https://github.com/hysts/pytorch_mpiigaze)（MIT），已在 `gaze_estimation/` 内维护并在 `THIRD_PARTY_NOTICES.md` 中署名。

## 联系方式 · Contact

- 📧 邮箱 / Email：[zhuqibensu@proton.me](mailto:zhuqibensu@proton.me)
- 🐙 GitHub：[@Zhuqiben](https://github.com/Zhuqiben)
- 📝 博客 / Blog：[zhuqiben.github.io/blog](https://zhuqiben.github.io/blog/)
- 📊 Kaggle：[qibensu](https://www.kaggle.com/qibensu)

## 技术栈 · Tech Stack

![Python](https://img.shields.io/badge/Python-3776AB?style=flat-square&logo=python&logoColor=white)
![PyTorch](https://img.shields.io/badge/PyTorch-EE4C2C?style=flat-square&logo=pytorch&logoColor=white)
![TensorFlow](https://img.shields.io/badge/TensorFlow-FF6F00?style=flat-square&logo=tensorflow&logoColor=white)
![ROS 2](https://img.shields.io/badge/ROS__2-22314E?style=flat-square&logo=ros&logoColor=white)
![Gazebo](https://img.shields.io/badge/Gazebo-FF6600?style=flat-square&logo=gazebo&logoColor=white)
![OpenCV](https://img.shields.io/badge/OpenCV-5C3EE8?style=flat-square&logo=opencv&logoColor=white)
![ONNX](https://img.shields.io/badge/ONNX-005CED?style=flat-square&logo=onnx&logoColor=white)
![MATLAB](https://img.shields.io/badge/MATLAB-0076A8?style=flat-square&logo=mathworks&logoColor=white)
![Linux](https://img.shields.io/badge/Linux-FCC624?style=flat-square&logo=linux&logoColor=black)
![Git](https://img.shields.io/badge/Git-F05032?style=flat-square&logo=git&logoColor=white)
