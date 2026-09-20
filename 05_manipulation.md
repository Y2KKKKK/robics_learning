# 05 Manipulation
> 偏向研究"如何让机器人用手或者全身去触碰、抓取、操作物体"，核心是**感知 → 策略 → 动作**闭环。  
> motion imitation 侧重"照着参考动作做"，manipulation侧重"看懂场景、听懂指令后完成操作任务"。
> 而WBC是底层执行底座，本类常作为**上层策略/大脑**，输出目标后交给WBC执行。

---

## 入门平台

### LeRobot
- 简介：
  - Hugging Face官方，是最友好入门平台，安装简单
  - 支持 ACT / Diffusion Policy / OpenVLA / pi0 / GR00T 等主流策略，从数据采集→训练→部署全链路打通
- GitHub:https://github.com/huggingface/lerobot

### RoboManipBaselines
- 简介：
  -统一基准框架，AIST 开源
  - 集成多种策略
  - 统一数据格式（RMB），方便横向对比
  - MuJoCo 仿真环境开箱即用
- GitHub:https://github.com/isri-aist/RoboManipBaselines

---

## 核心策略方法

### ACT / Action Chunking
- 简介：
  - 用 Transformer 一次预测一串动作（chunk），解决双臂协调问题
  - 数据效率高（<100条demo），是双臂操作的事实标准。
- GitHub:https://github.com/tonyzhaozh/act
- ACT++（Mobile ALOHA 增强版）:https://github.com/MarkFzp/act-plus-plus

### Diffusion Policy
- 简介：
  - 用扩散模型生成动作，擅长复杂/接触密集型操作
  - DP-T（Transformer版）适合长时域任务。
- GitHub:https://github.com/real-stanford/diffusion_policy

### 3D Diffusion Policy (DP3)
- 简介：
  - 结合 3D 点云视觉 + 扩散策略，空间操作精度显著提升，多个仿真/真机 benchmark SOTA。
- GitHub:https://github.com/YanjieZe/3D-Diffusion-Policy
- 项目页:https://dp3.cs.columbia.edu/

### H³DP（三重层次扩散策略，RSS 2025 清华）
- 简介：
  - 输入层（深度分层）→ 表征层（多尺度）→ 动作生成层（层次化条件扩散）
  - 44个仿真任务 + 4个真机双臂任务验证。
- 项目页:https://h3-dp.github.io/

---

##  双臂操作、灵巧手（人形操作的核心难点）

### RDT-1B（清华扩散基础模型，双臂操作标杆）
- **简介**：清华 TSAIL 团队，1.2B 参数，46个数据集/100万+episodes预训练 + ALOHA 6K双臂数据微调；统一动作空间，支持双臂/关节/EEF/轮式。
- GitHub:https://github.com/thu-ml/RoboticsDiffusionTransformer
- 项目页:https://rdt-robotics.github.io/rdt-robotics/

### Reactive Diffusion Policy 
- 简介：
  - Slow-Fast 视觉-触觉策略，接触密集型操作，VR遥操作采集+GelSight触觉传感。
- GitHub:https://github.com/xiaoxiaoxh/reactive_diffusion_policy

### AgiBot-World
- 简介：
  - 100+机器人/100万+轨迹/100+场景
  - GO-1 基础模型，基于 LeRobot 数据格式，双手/移动/灵巧手全覆盖。
- GitHub:https://github.com/OpenDriveLab/AgiBot-World

---

## VLA

### OpenVLA
- 简介：
  - 最广泛使用开源基线
  - 7B Llama-2 骨干，Open X-Embodiment 97万条真机轨迹训练
  - OpenVLA-OFT 并行解码+动作分块，LIBERO 成功率 97.1%。
- GitHub:https://github.com/openvla/openvla

### Octo
- 简介：
  -轻量通用策略
  - 纯 Transformer + Diffusion，看图做动作，无语言模型包袱，推理速度最快的开源基准之一。
- GitHub:https://github.com/octo-models/octo

### Open X-Embodiment
- 简介：
  -Google DeepMind，跨本体数据集+RT-X模型
  - 22种机器人/527个技能/16万+任务，跨机器人通用策略学习的标准数据集。
- GitHub:https://github.com/google-deepmind/open_x_embodiment

---

## 全身操作 / Loco-Manipulation（与人形WBC交叉，放05）

### BEHAVIOR Robot Suite
- 简介：
  - WB-VIMA 算法利用运动学层级建模全身动作
  - JoyLo 遥操作接口；真实家庭场景全身操作。
- 项目页:https://behavior.stanford.edu/（仓库以官方为准）

### TRILL
- 简介：VR 采集人类示范 → WBC 将任务空间命令转为关节力矩 → 高效学习人形 loco-manipulation 策略。
- GitHub:https://github.com/UT-Austin-RPL/TRILL
- 项目页:https://ut-austin-rpl.github.io/TRILL

### HOMIE
- 简介：同构外骨骼 + 动作感应手套 + 踏板，RL 训练支持任意上身姿态下的行走/深蹲。
- GitHub:https://github.com/OpenRobotLab/OpenHomie

### FALCON
- 简介：
  -力自适应 Loco-Manipulation
  - 学习推/拉/开门等需要大力交互的全身操作，考虑纵向力/多向力。
- GitHub:https://github.com/LeCAR-Lab/FALCON
- 项目页:https://lecar-lab.github.io/falcon-humanoid

### DemoHLM
- 简介：每条任务仅需 1 条示范，自动合成数百到数千条成功轨迹，跨环境泛化。
- GitHub:https://github.com/BeingBeyond/DemoHLM

---

## 底层规划（WBC + MPC，与03交叉引用）

### wb_humanoid_mpc
- 简介：基于 OCS2 最优控制框架，质心动力学 MPC + 全身动力学 MPC，支持 Unitree G1，MuJoCo 仿真。
- GitHub:https://github.com/wei-hsuan-cheng/wb_humanoid_mpc

### CLocoMani_Humanoid
- 简介：序贯凸规划（SCP）+ SOCP 求解器，实时轨迹生成，全身运动学 + 操作动力学统一。
- GitHub:https://github.com/QingtanZeng/CLocoMani_Humanoid

## Awesome 总索引

### Awesome Embodied VLA / Manipulation
- GitHub:https://github.com/woodfsg/awesome-embodied-vla-va-vln
- 涵盖π0 / RDT-1B / OpenVLA / Octo / GR00T / CogACT 等几乎所有 VLA/manipulation 论文

### Awesome Humanoid Robot Learning（人形学习全景）
- GitHub:https://github.com/YanjieZe/awesome-humanoid-robot-learning


## 一些blog或者资源分享推荐
-  CSDN《如何用LeRobot快速构建你的第一个AI机器人：面向开发者的完整入门指南》
- CSDN《权威的具身智能机器人学习路径》（作者 qq_39777550）
- VnRobo《Hands-on: Fine-tune OpenVLA with LeRobot》
- CSDN《具身智能操作类学习路线（模仿学习与强化学习）》robotsj.cn
- Robotics Center《ACT vs Diffusion Policy: Which Should You Use? (2025)》
- ALOHA 项目主页:https://tonyzhaozh.github.io/aloha/
- 知乎/公众号《2026具身智能模型选型全攻略》（π0.5/GR00T/OpenVLA/GO-1对比）
- Berkeley 官方；具身智能综述
- IEEE Humanoids 2023；GitHub 仓库
- LeCAR-Lab 官方



## 实操路线建议

1. **LeRobot** 跑通 SO-100 抓取（理解数据采集→训练→部署）→
2. **ACT / Diffusion Policy** 在仿真里做精细操作 →
3. **3D Diffusion Policy / H³DP** 体会视觉表征的重要性 →
4. **RDT-1B / OpenVLA** 接触双臂 + VLA 大模型 →
5. **TRILL / HOMIE / BRS** 进入人形全身操作 →
6. **wb_humanoid_mpc / CLocoMani** 理解底层规划如何支撑操作


## 交叉引用
- **02_motion_imitation**：操作策略常以"动作模仿"为预训练/初始化
- **03_whole_body_control**：操作目标的底层执行（WBC/MPC）
- **04_human_to_robot**：人类示范/遥操作是操作数据的重要来源
- **07_sim_to_real**：操作策略从仿真到真机的迁移

