# deepLearnigInPdcOfAutoDrivingPaperList
Paper list for deep learning in deciding and planning of auto-driving

CVPR-2019
[End-to-end Interpretable Neural Motion Planner](http://www.cs.toronto.edu/~wenjie/papers/cvpr19/nmp.pdf)
 - input and output
   - A holistic model that takes as input raw LIDAR data and a HD map and produces interpretable intermediate representations in the form of 3D detections and their future motion forecasted over the planning horizon. 
   - Our final output representation is a space-time cost volume that represents the “goodness” of each possible location that the SDV can take within the planning horizon. 
   - Our planner then scores a series of trajectory proposals using the learned cost volume and chooses the one with the minimum cost.
- loss function
  - $L = L_perception + β·L_planning$
  - Our planning loss encourages the minimum cost plan to be similar to the trajectory performed by human demonstrators.Note that this loss is sparse as a ground-truth trajectory only occupies small portion of the space. As a consequence, learning with this loss alone is slow and difficult.
  - To mitigate this problem, we introduce an another perception loss that encourages the intermediate representations
to produce accurate 3D detections and motion forecasting.This ensures the interpretability of the intermediate representations and enables much faster learning.
