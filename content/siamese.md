+++
title = "Siamese Network for Image Classification"
date = "2021-05-01"
+++

A project implementing a Siamese Network for image classification.

# The Problem
The dataset I used consisted of malaria infected and uninfected cell images. The task is to perform binary classification and there are numerous implementation and research papers that worked on this problem. Using a pre-trained VGG network this paper, was able to obtain an accuracy of 99.4%.

# Siamese Network
Siamese networks consists of two or more identical networks inside that shares the same parameters and are identical in every way. This way if we input 2 images to a siamese network, it compares the feature vectors of both the image from which it can learn the similarities or differences between the images. Siamese networks basically learn a similarity function.

![siamese](/images/siamese.png)

# The Solution
To top such high accuracy obtained using VGG network,I had to use a different approach ie. Siamese Network. Siamese networks are used for ‘one shot learning’ and are very effective for tasks like signature verification and face recognition which means that Siamese Network are effective in capturing and comparing very minute details present in the image. This is something that could prove beneficial for our problem.

# Implementation
I labelled images of one class as zero and the other as one. Then created a set of image pairs for training containing pairs of image of same class as 0 and different classes as 1. This list is inputted to the siamese network for training and after training, the network should possibly understand the difference betweeen a parasitized and non parasitized cell image.
I verified this using the validation set image which was not used during the training process. I obtained an accuracy of 99.70% on validation set and 99.72% on training set which is better than the VGG based approach.

Open the notebook in Google Colaboratory : [![colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/nivedwho/Colab/blob/main/SiameseNet.ipynb)
