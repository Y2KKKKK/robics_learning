
$\color{#ff69b4}{\text{MuJoCo}}$：用来**搞清楚身体怎么动**  

适合高校、实验室、做控制/RL/人性运动的学生，但对于需要大规模并行的项目则很不适用。

优点：  
1.接触动力学稳：走路、跑、跌倒恢复、灵巧手、人形跟踪动作，不容易炸。  
2.单线程/CPU 上非常快，调算法飞快。  
3.MJCF 模型清晰，PHC / UHC / ExBody 系工作很多基于它。  
4.适合做：motion imitation、locomotion、WBC baseline、RL 快速验证。  
5.现在也支持 GPU、batch simulation，但“大规模万级并行”不是它最舒服的场景。  

缺点：  
1.默认渲染一般，不适合直接训 VLA / 视觉策略。  
2.大规模并行不如 Isaac Lab。  
3.真机传感器（RGB-D、LiDAR）生态不如 NVIDIA。  
