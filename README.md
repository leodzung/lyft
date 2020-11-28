# [Lyft Motion Prediction for Autonomous Vehicles](https://www.kaggle.com/c/lyft-motion-prediction-autonomous-vehicles)

Autonomous vehicles (AVs) are expected to dramatically redefine the future of transportation. However, there are still significant engineering challenges to be solved before one can fully realize the benefits of self-driving cars. One such challenge is building models that reliably predict the movement of traffic agents around the AV, such as cars, cyclists, and pedestrians.

The ridesharing company Lyft started Level 5 to take on the self-driving challenge and build a full self-driving system (they’re hiring!). Their previous competition tasked participants with identifying 3D objects, an important step prior to detecting their movement. Now, they’re challenging you to predict the motion of these traffic agents.

In this competition, you’ll apply your data science skills to build motion prediction models for self-driving vehicles. You'll have access to the largest Prediction Dataset ever released to train and test your models. Your knowledge of machine learning will then be required to predict how cars, cyclists,and pedestrians move in the AV's environment.

Lyft’s mission is to improve people’s lives with the world’s best transportation. They believe in a future where self-driving cars make transportation safer, environment-friendly and more accessible for everyone. Their goal is to accelerate development across the industry by sharing data with researchers. As a result of your participation, you can have a hand in propelling the industry forward and helping people around the world benefit from self-driving cars sooner.

Update 11/28/2020
- [Using wget widget to download data from Kaggle to Google Colab](https://www.kaggle.com/kool777/ultimate-google-colab-training-batch-size-64)
Note: Chrome had a widget that is very handy to get the wget command, but had been removed due to potential mallicious code. I since used [cliget](https://github.com/zaidka/cliget) on Firefox.
Note: wget is much faster than curl for downloading.

- [Training using TPU](https://www.kaggle.com/doanquanvietnamca/tpu-resnet50-faster-better)
For this particular competition, TPU is not very useful because the bottle neck is the GPU, which is heavily utillized in the rasterization process. Also, there is a known bug in TPU that only allows training on single core. With this limitation, Colab GPU's performance is slightly better than the TPU counterpart.

- [Train on complete training dataset](https://www.kaggle.com/philculliton/lyft-full-training-set)
Google Colab has a limit on Cloud storage that didn't allow me to store the complete training dataset for training.
A workaround is to rasterize the training dataset locally with small size to reduce the size of the whole set. However, my local computer doesn't have sufficient RAM to support this (it hangs whenever reaching 50 - 60% completion).

- Different backbone architectures. 
For this particular competition, ResNet performs better than EfficientNet. ResNet18 produces more consistent validation and test score than ResNet34 and ResNet50. My final submission using ResNet18 as the backbone.

- Learning rate scheduler
CosineAnnealingWarmRestarts perform better than OneCycleLR. The reason is that with ConsineAnnealing scheduler, the learning rate drops faster and model converges faster, while with OneCycleLR, the learning rate in the beginning increases to a point that the loss starts to increase.
