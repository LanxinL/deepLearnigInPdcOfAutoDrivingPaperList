# deepLearnigInPdcOfAutoDrivingPaperList
Paper list for deep learning in deciding and planning of auto-driving

## Planning

### Interpretation
- `2020` Interpretable End-to-end Urban Autonomous Driving with Latent Deep Reinforcement Learning
  - 用 PGM 引入可解释的 latent Model
  - 用 Rl train PGM

### Tuning
- [Waymo (July 2019) & DeepMind - PBT (NOV 2017)](https://blog.waymo.com/2019/08/how-evolutionary-selection-can-train.html)
  - To make this process more efficient, researchers at DeepMind devised a way to automatically determine good hyperparameter schedules based on evolutionary competition (called [“Population Based Training” or PBT](https://deepmind.com/blog/article/population-based-training-neural-networks])), which combines the advantages of hand-tuning and random search.
  - To make this process more efficient, researchers at DeepMind devised a way to automatically determine good hyperparameter schedules based on evolutionary competition (called [“Population Based Training” or PBT](https://deepmind.com/blog/article/population-based-training-neural-networks])), which combines the advantages of hand-tuning and random search.
  - PBT 的思路是，在training的每一步中都评分一下参数，然后选择新参数；
    - 这样会比train完再评价+选新参数效率更高，而且是在训练过程中的搜索（PBT discovers a schedule of hyperparameter settings rather than following the generally sub-optimal strategy of trying to find a single fixed set to use for the whole course of training.）
- `Apollo-2018` An Auto-tuning Framework for Autonomous Vehicles
  - 将 AC 架构下的 IRL 简化至 Value Based
  - 假设human的得分应该在最高分附近，因此通过约束planner的得分要高于human的得分，训练cost func里的参数

### safety 
- `2020`Training Adversarial Agents to Exploit Weaknesses in Deep Control Policies`用对抗agent去寻找当前pdc的弱点`
  - 文章没写清楚input，output和model，缺少关键信息
- `2018` Parallel Planning: A New Motion Planning Framework for Autonomous Driving
  - train一个紧急情况的预测器，再train一个在紧急情况下直接生成trajectory的end-to-end的policy，以避免紧急情况下链路太长导致的相应不及时
  - 私认为该思想在高速公路上比较适用，在公路和末端train复杂的policy无太大意义，但简化的policy会有用
  
### Attention
- `2020` Learning a Directional Soft Lane Affordance Model for Road Scenes Using Self-Supervision
  - A self-supervised method for training a probabilistic network model to estimate the regions humans are most likely to drive in as well as a multimodal representation of the inferred direction of travel at each point.
- `2019-nips` Social Attention for Autonomous Decision-Making in Dense Traffic
    - 用 attention 解决了周围障碍物排序的问题
  
### Replace Cost Function
- `CVPR-2019` [End-to-end Interpretable Neural Motion Planner](http://www.cs.toronto.edu/~wenjie/papers/cvpr19/nmp.pdf)
`新的 cost map 的建模方式`
  - Input and Output
    - A holistic model that takes as **input** raw LIDAR data and a HD map and **produces** interpretable intermediate representations in the form of 3D detections and their future motion forecasted over the planning horizon. 
    - Our **final output** representation is a space-time cost volume that represents the “goodness” of each possible location that the SDV can take within the planning horizon. 
    - Our planner then **scores a series of trajectory proposals** using the learned cost volume and **chooses the one with the minimum cost**.
   - Loss function
     - <img src="https://render.githubusercontent.com/render/math?math=L=L_{perception}%2B\beta*L_{planning}">
     - Our **planning loss** encourages the minimum cost plan to be similar to the trajectory performed by human demonstrators.Note that this loss is sparse as a ground-truth trajectory only occupies small portion of the space. As a consequence, learning with this loss alone is slow and difficult.
     - To mitigate this problem, we introduce an another **perception loss** that encourages the intermediate representations
   to produce accurate 3D detections and motion forecasting.This ensures the interpretability of the intermediate representations and enables much faster learning.
- `2019` Jointly Learnable Behavior and Trajectory Planning for Self-Driving Vehicles
  - An interpretable cost function on top of perception, prediction and vehicle dynamics, and a joint learning algorithm that **learns a shared cost function employed by our behavior and trajectory components**.

### End to end
#### via Imitation Learning
- `Google brain & Waymo` ChauffeurNet: Learning to Drive by Imitating the Best and Synthesizing the Worst
  - RNN
  - Input: consists of several images of size W*H pixels rendered into this top-down coordinate system.（sec 3.1）
  - Output: a drivable trajectory.
#### via Condition Imitation Learning
  - `ICCV-2019` Exploring the Limitations of Behavior Cloning for Autonomous Driving
    - policy模型采用ResNet，与预测模型共享特征提取层，以期望提取到更好的信息，增加了一些关于如何判断done等细节设计
    - 分析了目前Imitation Learning的不足（sec 5.3）
      - Generalization in the presence of dynamic objects
      - Driving Dataset Biases
      - Causal confusion and the inertia problem
      - High Variance
      

## Control
- [Path Tracking Control Using Imitation Learning with Variational Auto-Encoder](https://ieeexplore.ieee.org/document/8971711) ICCAS`(rank - B4)` 2019
- [Trajectory VAE for multi-modal imitation](https://openreview.net/forum?id=Byx1VnR9K7) ICLR(rejected) 2019
- [Variational Autoencoder for End-to-End Control of Autonomous Driving with Novelty Detection and Training De-biasing](https://people.csail.mit.edu/rosman/papers/iros-2018-variational.pdf) IROS 2018

## Simulator
- `2019` Game-Theoretic Modeling of Multi-Vehicle Interactions at Uncontrolled Intersections
  - a framework **based on game theory** for modeling vehicle interactions at uncontrolled intersections.
  - the model exhibits reasonable behavior expected in traffic, including the capability of **reproducing** scenarios extracted from real-world traffic data and reasonable performance in resolving traffic conflicts.
