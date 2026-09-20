# Datasets：具身智能/人形动作模仿的数据从哪来
> 这一库只讲“数据”：动捕、重定向后动作、遥操作演示、跨本体操作数据、VLA 预训练语料。
> 不堆方法：动作模仿放 02，WBC 放 03，人→机映射放 04，操作放 05，VLA 放 06，Sim2Real 放 07。
> 本库回答的是：你训模型时，demo / trajectory / language / state / action 分别长啥样、谁开源了、能不能直接喂。

## 1. 人形动作模仿类
### AMASS
- 内容：300+ 人、11000+ 条 SMPL 动作，日常/体育/舞蹈都有，PHC/UHC 的“参考动作”常来自这。
- GitHub:https://github.com/nghorbani/amass
- 官网:https://amass.is.tue.mpg.de/
- 来源：ICCV 2019；CSDN/知乎《具身智能开源数据集调研报告》常把它列为人形模仿第一名。[3](@ref)

### Retargeted AMASS for Robotics（AMASS → Unitree G1 等）
- 内容：把 AMASS 重映射到机器人关节空间，G1 有 CSV/MuJoCo 可用轨迹，省掉自己写 retarget。
- HF：`https://huggingface.co/datasets/fleaven/Retargeted_AMASS_for_robotics`
- 来源：具身智能社群资源页 / HuggingFace 数据集页。[2](@ref)

### LAFAN1 / LAFAN1 Retargeting
- 内容：Ubisoft 动作插值数据集，CC BY 4.0，常用来测“运动补全 / in-betweening / 跟踪鲁棒性”。
- 原数据：Modelscope `OmniData/LaFAN1`
- G1 重定向：具身智能社群资源中心列有 `LAFAN1_Retargeting_Dataset`。[2,3](@ref)

### SEED
- 内容：14w+ 条、288h，含 G1 MuJoCo CSV，直接给人形模仿/语言条件策略用。
- 查看器：`https://github.com/bones-studio/seed-viewer`
- 数据集：`https://huggingface.co/datasets/bones-studio/seed`

### BABEL / HumanML3D（带语言标签的人体动作）
- BABEL：AMASS 加动作语言标签，适合“语言→全身动作”。
- HumanML3D：`https://github.com/EricGuo5513/HumanML3D`（文本-动作基准）
- 来源：CVPR/ICCV 系；做 VLA 前处理时常被引。[3](@ref)

---

## 2. 人→机 / 遥操作演示类（接 04 库）

### OmniH2O-6
- 内容：6 类日常任务的人类全身遥操作演示，行走/搬运/交互多模态，训整身策略用。
- 项目：`https://omni.human2humanoid.com`
- 代码：`https://github.com/LeCAR-Lab/human2humanoid`
- 来源：《具身机器人遥操作综述》点名 OmniH2O-6 是整身运动策略数据集。[13](@ref)

### HumanPlus 数据/流程
- 内容：动捕或单 RGB → 重定向 → HST 遥操作/影子 → HIT 行为克隆。
- 代码：`https://github.com/MarkFzp/humanplus`
- 来源：Stanford ALOHA 系；CSDN《人形机器人全身运动规划相关资料》。

### ALOHA / Mobile ALOHA（双臂操作演示鼻祖）
- 代码：`https://github.com/MarkFzp/act-plus-plus`
- 数据意义：虽然偏机械臂，但“遥操作→BC/ACT”范式被 HumanPlus 借过去。
- 来源：知乎/数据派THU《主流数据集》把 ALOHA 放第一档。[5](@ref)

### Open-TeleVision / HOMIE / Bunny-VisionPro
- 不是单纯数据集，但是“遥操作数据采集系统”：采出来的就是人形全身 demo。
- Open-TeleVision：`https://github.com/OpenTeleVision/TeleVision`
- 来源：遥操作综述里列 HOMIE / ACE / Bunny-VisionPro / Open-TeleVision 均开源。[13](@ref)

---

## 3. 跨本体操作 / VLA 预训练类（接 05 / 06）

### Open X-Embodiment（OXE）
- 内容：21 机构、60 数据集、22 本体、100w+ 真实机器人轨迹、527 技能，RLDS 格式，OpenVLA/Octo/RT-X 的命根子。
- GitHub：`https://github.com/google-deepmind/open_x_embodiment`
- 项目：`https://robotics-transformer-x.github.io/`
- 来源：DeepMind 官方博文；CSDN《Open X-Embodiment 全球具身智能开发者社区》；数据派THU。[9,11](@ref)

### LeRobot Dataset（HuggingFace 格式标准）
- 内容：相机 MP4 + state/action Parquet，SO-100/SO-101/Alice 等便宜硬件直接采，VLA 微调最友好。
- 框架：`https://github.com/huggingface/lerobot`
- 意义：现在新项目不发 LeRobot 格式都不好意思。
- 来源：HuggingFace 官方；具身智能开源日报。

### DROID / BridgeData V2 / RH20T / RoboMIND / AgiBot World
- DROID：7.6w Franka 桌面操作 → `stanford-volxy/DROID`
- BridgeData V2：Berkeley WidowX 6w 条
- RH20T：上海交大，11w 单臂遥操作
- RoboMIND：国地中心，单/双/人形/灵巧手
- AgiBot World：智元，100w+ 双臂/灵巧手真实轨迹
- 汇总文：掘金《最全具身智能数据集分享系列》[1](@ref)；数据派THU《主流数据集》[5](@ref)

---

## 4. 仿真/基准数据（不真机，但训模型天天用）

### LIBERO（VLA 操作基准）
- `https://github.com/Lifelong-Robot-Learning/LIBERO`
- 130 任务 / 4 类，语言条件操作评测标配。

### ManiSkill / SAPIEN / MetaWorld / RLBench
- ManiSkill：`https://github.com/maniskill` （GPU 并行操作）
- SAPIEN：`https://github.com/haosulab/SAPIEN`
- MetaWorld：`https://github.com/Farama-Foundation/Metaworld`
- RLBench：`https://github.com/stepjam/RLBench`

### HumanoidBench（人形全身：loco + manipulation）
- MuJoCo 上 27 个全身任务（12 行走 + 15 操作），H1/Digit/Shadow Hand。
- `https://github.com/corl-robotics/humanoid-bench`

### PHUMA / KAIST 人形 loco 数据
- Physics-constrained retargeting（PhySINK）→ G1/H1-2，消滑步、守关节限位。
- 搜 `PHUMA humanoid dataset KAIST` 即可。

---

## 5. 重定向 & 数据清洗工具（不是数据集，但没它你数据用不了）

### Humanoid Retarget
- SMPL/BVH → 机器人轨迹，IK 优化 + MuJoCo 可视化 + Web 配置。
- 社区仓库名常搜：`humanoid_retargeting` / `Humanoid-Retarget`

### UMR（接触保持重定向）
- `https://github.com/hanyang9/UMR`
- 做“手-物/脚-地”接触保真，动捕转机器人别穿模。

### LocoMuJoCo
- `https://github.com/robfiras/loco-mujoco`
- 把 AMASS/LAFAN1 包成 Gym/MuJoCo 可直接训的 motion-imitation 数据。

---

## 6. 新手怎么用这些数据集（写进仓库的实操顺序）

1. 看动作长啥样：AMASS + SEED viewer
2. 跑模仿 baseline：LocoMuJoCo（AMASS/LAFAN1 已处理）
3. 做人形数据：Retargeted AMASS → G1 CSV → MuJoCo
4. 做“人教机器人”：HumanPlus / OmniH2O / Open-TeleVision 采 demo
5. 做 VLA：LeRobot 格式存自己数据 + OXE 预训练 + LIBERO 评测
6. 上真机：自己遥操作数据（04）→ Sim2Real（07）→ WBC 执行（03）

## 7. 索引类（查漏补缺）
- Awesome Humanoid Robot Learning：`https://github.com/YanjieZe/awesome-humanoid-robot-learning`
- Awesome Physical AI：`https://github.com/junyuan-fang/awesome-physical-ai`
- 具身智能社群资源页：`https://www.unifolm.com/#/resource` [2](@ref)

> 给师弟妹的话：
> 具身方向里“数据格式”比“数据多少”更先杀人。
> AMASS 再好，不重定向就是 SMPL；
> OXE 再大，不转 LeRobot 你 PyTorch 跑得想哭；
> 真机 200 条干净遥操作，常比 10w 条脏仿真更有用。
> 这个库的价值不是“列全”，是告诉你：哪些能直接喂、哪些要先加工、哪些别碰。
