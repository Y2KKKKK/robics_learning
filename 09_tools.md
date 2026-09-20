# Tools
> 只放工具：仿真训练框架、RL 库、遥操作采集、重定向、数据格式、真机 SDK、部署运行时、评测。    
> 动作模仿放 02，WBC 放 03，人→机放 04，操作放 05，VLA 放 06，Sim2Real 放 07，数据放 08。  
> 本库回答：从“看论文”到“真机跑起来”中间，到底该装哪些 repo、点哪些脚本。  

##  仿真 + RL训练（练模型的地方）

- **Isaac Lab**
  - GitHub:https://github.com/isaac-sim/IsaacLab
  - 文档:https://isaac-sim.github.io/IsaacLab/
  - 来源:- NVIDIA 官方文档《Getting Started with Isaac Lab》；
         - CSDN《机器人研发开源算法选型》明确说“新用户直接从 Isaac Gym 迁到 Isaac Lab”
    
- **legged_gym**
  - GitHub:https://github.com/leggedrobotics/legged_gym
  - 来源：CSDN 博主 weixin_28718487《足式控制、双臂操作与具身智能落地指南》
  
- **rsl_rl**
  - GitHub:https://github.com/leggedrobotics/rsl_rl
  - 来源：同上一篇 CSDN；社区共识“legged_gym + rsl_rl 是足式 RL 标配”
  
- **skrl**
  - 文档:https://skrl.readthedocs.io/en/latest/intro/examples.html
  
- **MuJoCo / mujoco_playground**
  - GitHub:https://github.com/google-deepmind/mujoco
  - playground:https://github.com/google-deepmind/mujoco_playground
    
- **robosuite**
  - GitHub:https://github.com/ARISE-Initiative/robosuite
    
- **ManiSkill**
  - GitHub:https://github.com/haosulab/ManiSkill

##  数据采集/遥操作工具
- **LeRobot（HuggingFace，统一数据格式+采集+训练+部署）**
  - GitHub:https://github.com/huggingface/lerobot
  - 来源：CSDN《机器人开源算法实战清单》称“个人开发者性价比最高起点”
- **ALOHA / Mobile ALOHA（双臂主从遥操作鼻祖）**
  - ALOHA:https://github.com/tonyzhaozh/aloha
  - Mobile ALOHA:https://github.com/MarkFzp/mobile-aloha
- **Open-TeleVision（VR 沉浸全身遥操作）**
  - GitHub:https://github.com/OpenTeleVision/TeleVision
- **OmniH2O / human2humanoid（全身遥操作+数据）**
  - GitHub:https://github.com/LeCAR-Lab/human2humanoid
- **OpenWBT（宇树 G1/H1 全身遥操作，清华+银河通用）**
  - 来源：开源社《2025 中国开源报告·具身智能篇》
- **DexterCap / Open-TeleDex（灵巧手：人手套/单目重建→重定向）**
  - DexterCap:https://github.com/PKU-MoCCA/DexterCap
  - 来源：微信公众号《老马的AI机器人充电站：DP、UMI、DexCap 读懂模仿学习闭环》
- **HOMIE / Bunny-VisionPro / ACE（综述里点名的开源遥操作）**
  - 来源：CSDN《具身机器人遥操作综述》、期刊综述《具身机器人遥操作技术与产业发展》

##  重定向/shadowing工具
- **UMR（接触保持重定向）**
  - GitHub:https://github.com/hanyang9/UMR
- **hhtools（RoboParty 的人→人形重映射工具）**
  - 组织:https://github.com/Roboparty/Party_OS
  - 来源：微信公众号《PartyOS 开源上线》提 MimicLite / UFO / hhtools
- **Humanoid Retarget / xGMR**
  - xGMR 见于国内开源全景文（RexBot 整理 420+ 项目）
- **LocoMuJoCo（把 AMASS/LAFAN1 包成可直接训的模仿数据）**
  - GitHub:https://github.com/robfiras/loco-mujoco

##  数据格式
- **Open X-Embodiment / RLDS**
  - GitHub:https://github.com/google-deepmind/open_x_embodiment
- **LeRobot 数据集格式（Parquet + mp4，VLA 微调事实标准）**
  - 同 huggingface/lerobot
- **robomimic（离线模仿学习数据接口 + BC/CQL/BCQ）**
  - GitHub:https://github.com/ARISE-Initiative/robomimic
- **Dexbotic（一站式 VLA 开发箱：Dexdata 格式 + π0/CogACT/OFT）**
- **starVLA（VLA 公平评测基建）**

##  真机SDK/控制中间件
- **ROS 2 / ros2_control**
  - GitHub:https://github.com/ros2/ros2
  - 控制层:https://github.com/ros-controls/ros2_control
- **MoveIt 2（机械臂运动规划）**
  - GitHub:https://github.com/moveit/moveit2
- **Unitree 官方栈（SDK2 / mujoco / rl_gym / il_lerobot）**
  - 官网:https://www.unitree.com/cn/mobile/opensource/
  - unitree_rl_gym:https://github.com/unitreerobotics/unitree_rl_gym
  - unitree_mujoco：官网列；unitree_IL_lerobot：宇树基于 LeRobot 的采集-训练-部署框架
  - 来源：宇树官方开源页（G1/H1/Z1/Dex3 全链路）
- **Fourier GRX Pipeline**
  - 组织:https://github.com/FFTAI（Wiki-GRx-*、fourier-lerobot、fourier-grx-client）
- **ROBOTIS physical_ai_tools / DynamixelSDK / cyclo***
  - 组织:https://github.com/ROBOTIS-GIT
  - 来源：ROBOTIS Physical AI 开源页（DYNAMIXEL + ROS2 + 数据集 + 部署）
- **Walker / TianGong URDF**
  - UBTECH:https://github.com/UBTECH-Robot

##  部署、评测
- **IsaacLab Arena（Isaac Lab + LeRobot 数据集 + VLA 评测）**
  - GitHub:https://github.com/isaac-sim/IsaacLab-Arena
  - 来源：NVIDIA 生态文（GR1/G1/伽利略，跑 PI0/SmolVLA/ACT/DP）
- **Wiki-GRx-Deploy（傅利叶：加载策略、下发关节命令）**
- **LeTools**
  - 来源：robotworld.top《The Developer Inflection Point》
- **Party OS / MimicLite / UFO**
  - Github:https://github.com/Roboparty/Party_OS
- **TeleOpBench**

##  新手装工具的顺序
1. Python + PyTorch + Gymnasium
2. PyBullet（跑 CartPole/机械臂）→ MuJoCo（看 humanoid.xml）
3. LeRobot（采 20 条桌面数据 → 训 DP → 跑）
4. Isaac Lab（训 G1 行走，rsl_rl / skrl 二选一）
5. Unitree SDK2 + unitree_mujoco（仿真控制程序接真机）
6. 遥操作：Open-TeleVision / ALOHA / unitree IL_lerobot
7. 重定向：UMR / LocoMuJoCo
8. 部署：Wiki-GRx-Deploy / IsaacLab Arena / 自家 ROS2 节点

##  索引
- Awesome Physical AI:https://github.com/ishandutta2007/Awesome-Physical-AI
- Awesome Humanoid Robot Learning:https://github.com/YanjieZe/awesome-humanoid-robot-learning
- 国内开源全景（420+ 项目）：RexBot 微信文《国内具身智能的开源全景》
- 开源社《2025 中国开源报告·具身智能篇》:https://kaiyuanshe.github.io/2025-China-Open-Source-Report/embodied-intelligence.html

> 具身方向里最容易被低估的是 tools。  
> 论文里一句“we collect 3k demos”背后是：相机同步、手柄映射、重定向、LeRobot 格式、域随机化、SDK 心跳、关节限幅、部署宕机。  
> 本库可以看作装机清单。  
