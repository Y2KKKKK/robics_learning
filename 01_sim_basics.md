
$\color{#ff69b4}{\textbf{MuJoCo}}$：用来**搞清楚身体怎么动**  

适合高校、实验室、做控制/RL/人性运动的学生，但对于需要大规模并行的项目则很不适用。  
企业一般用于做算法原型、baseline\系统辨识，不作为最终视觉训练平台。  

优点：  
- 接触动力学稳：走路、跑、跌倒恢复、灵巧手、人形跟踪动作，不容易炸。  
- 单线程/CPU 上非常快，调算法飞快。
- MJCF 模型清晰，PHC / UHC / ExBody 系工作很多基于它。  
- 适合做：motion imitation、locomotion、WBC baseline、RL 快速验证。  
- 现在也支持 GPU、batch simulation，但“大规模万级并行”不是它最舒服的场景。  

缺点：  
- :bangbang: 默认渲染一般，不适合直接训 VLA / 视觉策略。  
- :bangbang: 大规模并行不如 Isaac Lab。  
- :bangbang: 真机传感器（RGB-D、LiDAR）生态不如 NVIDIA。





$\color{#ff69b4}{\textbf{PyBullet}}$:新手第一个"Hello Robot"
