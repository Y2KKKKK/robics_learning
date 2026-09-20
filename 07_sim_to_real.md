# Sim to Real
> 解决“仿真能跑，真机翻车”的鸿沟
> 关注仿真模型与真实物理的一致性以及动力学在环境中转移成不成功

> 常作为 02(模仿)、03(WBC)、06(VLA) 的最终落地桥梁。

## 关键技术、论文

### 核心物理对齐与动力学校准
- ASAP：两阶段（仿真运动跟踪预训练 → 真实轨迹+delta action对齐微调），涉及全身动态约束与接触对齐。
  - GitHub:https://github.com/LeCAR-Lab/ASAP
  - 项目页:https://agile.human2humanoid.com

### 域随机化和鲁棒性
- 域随机化（Domain Randomization）：在仿真中随机化物理参数（摩擦力、质量、延迟、视觉纹理），迫使策略学到鲁棒特征。
  - 工程框架：Isaac Lab / Unitree_RL_Lab（03提及）天然支持大规模DR。

- RMA (Rapid Motor Adaptation)：学习“环境编码”，在真机实时适应未知扰动（如负载变化、地面起伏）。
  - 项目页:https://rma.cs.princeton.edu/

### 真实数据微调与视觉对齐
- **真实轨迹微调**：用少量真机数据（如遥操作，见04）微调仿真预训练策略，缩小视觉/动力学差距。
  - 代表：ALOHA（04提及）的“仿真预训练+真实微调”路线。

- **视觉Sim2Real**：渲染域对齐（如RGB渲染与真实相机差异），常用NeRF/3DGS提升仿真真实感。
  - 关联：VLA（06）常需视觉对齐才能泛化。

## 交叉引用
- 依赖 **03_WBC**（底层执行稳了才能谈转移）、**02_Motion_Imitation**（参考动作常来自仿真）。
- 数据来自 **04_Human_to_Robot**（遥操作真机数据）。
- 最终服务 **06_VLA**（大模型落地需物理一致）、**05_Manipulation**（操作抓取需接触真实）。


## 必看综述 & 索引
- **Awesome Sim2Real**:https://github.com/ManifoldFR/awesome-sim2real
- **Isaac Lab 官方文档**:https://isaac-sim.github.io/IsaacLab/
- **Genesis 项目页**:https://genesis-embodied-ai.github.io/
