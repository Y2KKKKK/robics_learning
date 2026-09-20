# Human to Robot
> 偏向研究“人如何变成机器人数据/控制”，核心是**人类演示/遥操作 → 重定向/映射 → 机器人策略/执行**。
> 与动作模仿区别：motion imitation 侧重“照着参考动作做”，本类侧重“人怎么产生数据并映射到机器人”。
> 与WBC区别：WBC是底层执行底座，本类常作为**数据管线/上层映射**，可驱动WBC或模仿策略。

## 关键技术、论文

### 核心：从人学人（动捕/RGB → 重定向 → 策略）
- **HumanPlus**：HST（仿真RL遥操作/影子）+ HIT（真实世界行为克隆）；单RGB/动捕+重定向→Unitree H1。
  - GitHub：`https://github.com/MarkFzp/humanplus`
  - 项目页：`https://humanoid-ai.github.io`

- **OmniH2O**：运动姿态为通用接口；VR/RGB/语言；特权教师蒸馏；OmniH2O-6 数据集（全身遥操作+学习）。
  - GitHub：`https://github.com/LeCAR-Lab/human2humanoid`
  - 项目页：`https://omni.human2humanoid.com`

### 遥操作数据采集（模仿学习的数据从哪来）
- **Open-TeleVision**：Vision Pro/Quest 视角，双手/全身遥操作参考，沉浸采集。
  - GitHub：`https://github.com/OpenTeleVision/TeleVision`

- **ALOHA / ACT**（操作模仿经典，思想互通，可交叉引用05_manipulation）：
  - ALOHA（Mobile ALOHA）：`https://github.com/MarkFzp/act-plus-plus`
  - ACT：`https://github.com/tonyzhaozh/act`

### 重定向与接触迁移（人→机映射的关键）
- **UMR**：点到点云对应+接触迁移，对“模仿时的接触（手-物/脚-地）”关键，常作为动作模仿/人→机的前置。
  - GitHub：`https://github.com/hanyang9/UMR`

## 交叉引用
- 常依赖 **02_motion_imitation**作为参考动作或者模仿目标，**03_whole_body_control**作为底层执行。
- 数据可归入 **08_datasets**，真机对齐参考 **07_sim_to_real**。

## 实操路线建议
1. Open-TeleVision 理解遥操作采集
2. UMR 看重定向/接触
3. HumanPlus/OmniH2O 串起“人→数据→策略”
4. 结合WBC(03)做执行，结合模仿(02)做目标。
