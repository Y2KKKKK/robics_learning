# VLA：Vision-Language-Action 大模型
> 具身智能的"大脑"：看图 + 听懂话 + 输出动作。  
> 与前面几个库的区别：
> - 02 motion imitation：照着动捕做（底层跟踪）
> - 03 WBC：全身怎么稳（底层执行）
> - 04 human to robot：人怎么变成数据（数据管线）
> - **05 manipulation：机械臂怎么抓（操作任务）**
> - **本库 VLA：上层语义理解 → 下层动作生成的端到端范式**

---

##  奠基工作

### RT-1 / RT-2（Google DeepMind，开山之作）
- **RT-1**：Transformer 直接输出离散化动作 token，语言条件操作策略。
- **RT-2**：视觉-语言模型（PaLM-E/PaLI-X）微调出动作能力，把互联网知识迁移到机器人。
- **GitHub（RT-2）**:https://github.com/rt2-public/rt2
- **项目页**:https://robotics-transformer2.github.io/

### OpenVLA（开源 RT-2 替代，社区主流）
- **简介**：7B 参数，基于 Llama 2 + SigLIP + DINOv2，在 Open X-Embodiment 数据集上训练，支持多机器人，可微调。
- **GitHub**:https://github.com/openvla/openvla
- **项目页**:https://openvla.github.io/

### Octo（UC Berkeley，通用策略+微调友好）
- **简介**：Transformer 架构，支持多模态输入（语言/目标图像），预训练后在新机器人上少量数据微调即可用。
- **GitHub**:https://github.com/octo-models/octo
- **项目页**:https://octo-models.github.io/

---

## 人形/全身 VLA

### GR00T（NVIDIA，人形通用基础模型）
- **简介**：多模态人形基础模型，接受语言/视频/动作输入，输出全身动作；配套 Isaac Lab + 合成数据管线。
- **GitHub**:https://github.com/NVIDIA/GR00T
- **项目页**:https://developer.nvidia.com/gr00t

### WholeBodyVLA（全身控制 + VLA 结合）
- **简介**：将 VLA 输出映射到全身关节目标，常配合 HOVER(03) 或 WBC 执行。
- **GitHub**:https://github.com/LeCAR-Lab/WholeBodyVLA

### HumanPlus 中的 VLA 组件（04 交叉）
- **简介**：HumanPlus 的 HIT（行为克隆）部分本质是视觉条件策略，可视为 VLA 简化版。
- **GitHub**:https://github.com/MarkFzp/humanplus
- **交叉引用**：本库侧重通用 VLA 范式，HumanPlus 具体实现放 04。

---

##  动作表征方法（VLA 怎么输出动作）

### Diffusion Policy（扩散策略，操作领域主流）
- **简介**：用扩散模型去噪生成动作序列，比回归方式更平滑、多模态。
- **GitHub**:https://github.com/real-stanford/diffusion_policy
- **项目页**:https://diffusion-policy.cs.columbia.edu/

### Action Chunking（动作分块，ACT 提出）
- **简介**：一次预测一段动作（chunk），减少累积误差，ALOHA 系统核心。
- **GitHub**:https://github.com/tonyzhaozh/act（见 04 库）
- **交叉引用**：动作表征方法，本库记录，具体遥操作放 04。

### 3D Diffusion Policy（3D Diffuser-Actor）
- **简介**：点云 + 扩散策略，3D 感知操作。
- **GitHub**:https://github.com/YanjieZe/3d_diffuser_actor

---

##  前沿方向（2025-2026）

### RDT（Robot Diffusion Transformer）
- **简介**：扩散 + Transformer，大规模多机器人预训练，强泛化。
- **GitHub**:https://github.com/thu-ml/RDT

### π0 / π0.5（Physical Intelligence，2025 重磅）
- **简介**：VLA 预训练 + 后训练，支持移动操作/全身任务，真机部署。
- **项目页**:https://physicalintelligence.company/research/pi0
- **GitHub**:https://github.com/PhysicalIntelligence/pi0

### TinyVLA（轻量化 VLA）
- **简介**：小模型也能做 VLA，适合嵌入式部署。
- **GitHub**:https://github.com/TinyVLA/TinyVLA

---

## 该仓库相关资源
- 知乎《RT-2: Vision-Language-Action Models Transfer Web Knowledge to Robotic Control》
- 知乎《LeRobot: 让机器人学习像 NLP 一样简单》
- Google DeepMind 官方
- 知乎《NVIDIA Project GR00T: 人形机器人基础模型》
- 知乎《OpenVLA: An Open-Source Vision-Language-Action Model》
- 知乎一般提供部分论文的部分讲解，复现主要依靠CSDN或者github

---

##  必看综述 & 索引

- **Awesome-VLAs**:https://github.com/VolcanoDing/awesome-vlas（VLA 论文/项目汇总）
- **Awesome-Humanoid-VLA**：:https://github.com/YanjieZe/awesome-humanoid-vla（人形方向 VLA 索引）
- **Embodied-AI-Guide（Lumina）**:https://github.com/Lumina-ai-code/Embodied-AI-Guide（中文综述）

---

> VLA 不是万能的。它输出的是"意图"
> 真正让机器人不倒、不乱扭，靠的是下面几层。先搞懂 02/03/04/05，再回来学 VLA，会通透很多。
