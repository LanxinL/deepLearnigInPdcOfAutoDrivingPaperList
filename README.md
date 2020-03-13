# deepLearnigInPdcOfAutoDrivingPaperList
Paper list for deep learning in deciding and planning of auto-driving

## Planning
CVPR-2019
- [End-to-end Interpretable Neural Motion Planner](http://www.cs.toronto.edu/~wenjie/papers/cvpr19/nmp.pdf)
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

- [Advanced planning for autonomous vehicles using reinforcement learning and deep inverse reinforcement learning](http://dcsl.gatech.edu/papers/ras18b%20(Printed).pdf#page=17&zoom=100,414,861)

## Control
- [Path Tracking Control Using Imitation Learning with Variational Auto-Encoder](https://ieeexplore.ieee.org/document/8971711) ICCAS`(rank - B4)` 2019
- [Trajectory VAE for multi-modal imitation](https://openreview.net/forum?id=Byx1VnR9K7) ICLR(rejected) 2019
- [Variational Autoencoder for End-to-End Control of Autonomous Driving with Novelty Detection and Training De-biasing](https://people.csail.mit.edu/rosman/papers/iros-2018-variational.pdf) IROS 2018
