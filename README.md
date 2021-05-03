# PhUn
PyTorch model PhUn for phase unwrapping



Original network was designed in TensorFlow framework, and this is the PyTorch version of it.

# Changes
I've added following moments to the structure:

1. Replication padding mode in conv3x3 blocks, because experiments have shown that it's important at the edges of phase maps,
otherwise unwrapping quality will be low

# Dataset
Dataset was generated synthetically according to articles [2,3]
So, dataset data was generated using two methods (in equal proportions):

1. Interpolation of squared matrixes (with uniformly distributed elements) of different sizes (2x2 to 15x15) to 256x256 and multiplying by random value, so the magnitude is between 0 and 22 rad
2. Randomly generated Gaussians on 256x256 field with random quantity of functions, means, STD, and multiplying by random value, so the magnitude is between 2 and 20 rad. From experiments with real simple phase images it's clear, that that method makes net more adapted for real-life examples

![example1](https://user-images.githubusercontent.com/73649419/115595429-95d36d00-a2df-11eb-8d83-1a629635a66f.png)
![example2](https://user-images.githubusercontent.com/73649419/115595433-97049a00-a2df-11eb-95d0-73c631d73240.png)

# Model
Model can be shown as following (from original article [1]):

![PhUn](https://user-images.githubusercontent.com/73649419/116903791-88a27080-ac45-11eb-92a6-c6e5d378bc3d.jpg)


# References
1. Gili Dardikman-Yoffe, Darina Roitshtain, Simcha K. Mirsky, Nir A. Turko, Mor Habaza, and Natan T. Shaked, "PhUn-Net: ready-to-use neural network for unwrapping quantitative phase images of biological cells," Biomed. Opt. Express 11, 1107-1121 (2020).
2. K. Wang, Y. Li, K. Qian, J. Di, and J. Zhao, “One-step robust deep
learning phase unwrapping,” Opt. Express 27, 15100–15115 (2019).
3. Spoorthi, G. E. et al. “PhaseNet 2.0: Phase Unwrapping of Noisy Data Based on Deep Learning Approach.” IEEE Transactions on Image Processing 29 (2020): 4862-4872.
