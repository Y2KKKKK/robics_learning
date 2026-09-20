# Sim to Real
> 偏向解决“仿真能跑，真机翻车”的鸿沟。核心是**物理对齐、域随机化、系统辨识、真实数据微调**。
> 与WBC区别：WBC关注底层约束求解（稳不稳），本类关注“仿真模型与真实物理的一致性”（像不像真）。
> 与动作模仿区别：模仿关注“动作像不像”，Sim2Real关注“环境/动力学转移成不成功”。
> 常作为 02(模仿)/03(WBC)/06(VLA) 的最终落地桥梁。

## 关键技术、论文

### 核心物理对齐 & 动力学校准
- **ASAP**（敏捷全身技能物理对齐）：两阶段（仿真运动跟踪预训练 → 真实轨迹+delta action对齐微调），解决“仿真能跑真机翻车”，涉及全身动态约束与接触对齐。
  - GitHub：`https://github.com/LeCAR-Lab/ASAP`
  - 项目页：`https://agile.human2humanoid.com`
  - 来源：LeCAR-Lab 官方仓库/项目页；前期动作模仿/Sim2Real脉络交叉

- **SysID (System Identification) / 参数估计**：通过真实数据反推机器人动力学参数（质量、摩擦、阻尼等），是传统Sim2Real底座。
  - 关联框架：Drake（03_WBC提及）接触动力学强，常配合做SysID。
  - 来源：机器人控制理论共识

### 域随机化 & 鲁棒性（DR）
- **域随机化（Domain Randomization）**：在仿真中随机化物理参数（摩擦力、质量、延迟、视觉纹理），迫使策略学到鲁棒特征。
  - 工程框架：Isaac Lab / Unitree_RL_Lab（03提及）天然支持大规模DR。
  - 来源：OpenAI 早期经典（Rubik's cube）；Isaac Lab文档

- **RMA (Rapid Motor Adaptation)**：学习“环境编码”，在真机实时适应未知扰动（如负载变化、地面起伏）。
  - 项目页：`https://rma.cs.princeton.edu/`
  - 来源：Princeton 人形/足式控制经典

### 真实数据微调 & 视觉对齐
- **真实轨迹微调**：用少量真机数据（如遥操作，见04）微调仿真预训练策略，缩小视觉/动力学差距。
  - 代表：ALOHA（04提及）的“仿真预训练+真实微调”路线。
  - 来源：具身操作经典路线

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

> 写进仓库时提醒：Sim2Real不是单一算法，而是“工程体系”。Isaac Lab + DR，再深入物理对齐（ASAP/RMA），最后结合真机数据微调。
