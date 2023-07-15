+++
title = "Attention based CNN for Image Classification"
date = "2021-04-01"
+++

A project implementing a deep learning attention based classification model proposed in the paper [“Learn To Pay Attention”](https://www.robots.ox.ac.uk/~tvg/publications/2018/LearnToPayAttention_v5.pdf) published in ICLR 2018 conference.

# Introduction
The basic idea behind attention models is to focus on that parts of a problem which are important. Such a model was introduced in 2014 and was mainly focused on solving NLP problem but eventually was found to be useful in the field of computer vision. Jetley et.al in the paper “Learn To Pay Attention” used attention based mechanism to solve simple image classification problem.

# The Model
The most important concept discused in this paper would be ‘attention maps’ which is a scalar matrix that represents activations of different locations of an image with respect to a target. With the help of attention maps the CNNs will eventually learn which part of an image is important for a particaular task. The image below is taken from the paper [“Grad-CAM: Gradient-weighted Class Activation Mapping”](https://arxiv.org/abs/1610.02391) and the attention map is trying to perform a similar task.

![attention](/images/attn.png)

The authors of the paper takes a VGG network and adds attention layers between a number of layers(7,10 and 13). Attention is calculated by feeding the output of some layer ‘n’ as input to the attention layer, which then calculates an “attention mask” (Binary matrix) and is multiplied with the input. This process is repeated for layers 10 and 13 also. The output of of these attention layers is represented by “g_a1”, “g_a2” and “g_a3” are then fed into the fully connected layers for classification.

# Working of the ‘attention’ part
Firstly a ‘compatibility score’ is calculated by comparing local features with the global ones. The term ‘global feature’ represents output of some convolution layer through which the input image is passed and its effective reseptive field will cover the whole image, whereas ‘local feature’ represents the features extracted from some subset of the original image. Similar to what we see in the figure above, the score will be high when a local patch is placed over the dog’s face since it is one of the most dominant feature in the image that helps in classifying it correctly. It can be calculated using two ways - by taking a dot product or by a method called ‘parametrised compatibility.’

Secondly the attention weights are calculated by transforming the compatibiltiy score to range of (0,1). This is done by using softmax function.

Thirdly using this attention weight, a weighted combination of the outputs of that particular layer is taken.

# Implementation
The authors of the paper have provided the source code for the proposed model but I have modified it a little bit and can now be run on Google Colaboratory. The batch size and number of epochs had to be reduced but still the accuracy of the model was seen to be increasing with time.

Open the notebook in Google Colaboratory : [![colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/nivedwho/Colab/blob/main/SelfAttnCNN.ipynb)





