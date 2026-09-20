# WBC
> 偏向研究底层，解决如何稳当落地或者动作怎样满足约束的问题  
> 关注底层约束求解（平衡、接触、关节限位、上下肢协调），常作为动作模仿/高层策略的“执行底座”。

> 与动作模仿有区别：motion imitation着重“模仿得像不像”，而WBC着重“执行得稳不稳、策略可行不可行”

## 关键技术、论文
### 经典基线、统一控制器
- HOVER（神经全身控制器，NVIDIA 系）:统一全身控制接口，常作为人形 WBC或者通用控制器基线，衔接仿真与真机。
  - GitHub:https://github.com/NVlabs/HOVER
  
- ExBody / ExBody2（表达性全身控制）:上半身强表达（模仿），下半身稳定（WBC 本质），Teacher-Student + 重定向，体现“表达 vs 稳定”折中。
  - GitHub（ExBody2 衍生/训练流程，以官网为准）:https://github.com/jimazeyu/exbody2
 
### 工程落地、仿真框架
- Unitree_RL_Lab：这篇在上一个部分motion imitation已经提过
  - GitHub:https://github.com/unitreerobotics/unitree_rl_lab
 
- Drake：基于梯度的控制系统设计，接触动力学/轨迹优化极强，适合 WBC 底层约束求解研究（非深度学习主流，但理论扎实）。
  - GitHub:https://github.com/RobotLocomotion/drake
 
### 前沿研究和多重交叉
- ASAP：两阶段（仿真运动跟踪预训练 → 真实轨迹+delta action 对齐微调），解决仿真能跑但真机翻车的问题，涉及全身动态约束与接触对齐。
  - GitHub:https://github.com/LeCAR-Lab/ASAP
 
- BeyondMimic：从动作追踪到通用控制都覆盖，扩散+动作追踪（有motion imitation也有WBC），真机依托Unitree G1，Isaac Lab和MuJoCo跑仿真都没问题。
  - GitHub（跟踪）:https://github.com/HybridRobotics/whole_body_tracking  
  - GitHub（部署）:https://github.com/HybridRobotics/motion_tracking_controller
 
### 进阶拓展（肌肉/高动态，作为WBC延伸）
- MuscleMimic：肌肉骨骼级控制，WBC生物力学延伸；MuJoCo Warp 并行，肌肉驱动人形，SMPL 重定向，全身操作，涉及底层力学约束。
  - GitHub:https://github.com/amathislab/musclemimic

- PBHC/KungfuBot：物理人形全身控制，高动态技能，强约束求解。
  - GitHub:https://github.com/TeleHuman/PBHC
 
## 在github上面自己找到了两个库，有分享价值
- Awesome Humanoid Robot Learning:https://github.com/YanjieZe/awesome-humanoid-robot-learning
- Robot Lab:https://github.com/fan-ziqi/robot_lab
