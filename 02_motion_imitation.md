# Motion Imitation（动作模仿）
> 定义即：参考动作 → 机器人跟踪/模仿  
> 输入通常是 AMASS或者SMPL 动捕序列，目标是跟踪关节或者末端位姿

## 关键技术、论文分享
- Deepmimic：动作模仿奠基地位，开创了参考动作+RL范式
    - Github:https://github.com/xbpeng/motion_imitation
      
- LocoMimic/LocoMuJoCo：人形和足式机器人“运动+模仿”基线
    - GitHub:https://github.com/robfiras/loco-mujoco（LocoMuJoCo）
      
- PHC：人形持续模仿、重定向相关，动作模仿强相关
    - GitHub:https://github.com/ZhengyiLuo/PHC
 
- AdaMimic：动作模仿 + 条件适应（仍围绕“模仿一条参考动作”）
    - GitHub:https://github.com/InternRobotics/AdaMimic

- BeyondMimic（Whole-Body Tracking + 扩散）：强调动作模仿向通用控制延伸，和WholeBody Control衔接
    - Github:https://github.com/HybridRobotics/whole_body_tracking

- UMR（动作重定向，接触保持）：更偏“模仿前的数据/重定向”，但常用在动作模仿链路，和human to robot衔接
    - GitHub:https://github.com/hanyang9/UMR
 
- Unitree_RL_Lab:宇树官方RL框架（Isaac Lab），支持 Go2/G1/H1，含 Locomotion + Mimic（动作模仿），完整 Sim2Real 链路。
    - Github:https://github.com/unitreerobotics/unitree_rl_lab

## 相关讨论网站和blog
- CSDN 《动作模仿:敏捷机器人运动技能学习》

- CSDN《人形机器人全身运动规划相关资料》

- CSDN 文献解读《BeyondMimic: 从动作追踪到通过引导扩散实现多功能人形控制》

- 知乎 开源分享《AdaMimic:兼顾动作模仿与条件适应的人形控制方法》

- 知乎 开源分享《UMR:面向接触保持的人形机器人动作重定向》

- CSDN《复现 Unitree_RL_Lab 项目:项目技术解析复现功能拓展优化》
