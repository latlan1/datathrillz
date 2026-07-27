---
title: "Regression & Classification Models in PyTorch"
date: 2020-05-05T23:41:00Z
tags: [classification, deep learning, pytorch, regression]
categories: [algorithms, data science, deep learning, machine learning]
draft: false
---

The purpose of this article is to share what I learned from a recent PyTorch course. We will share general machine learning tips as well as insights specific to deep learning library PyTorch. 

PyTorch is a deep learning library for Python and was created by Facebook in 2016. PyTorch is good for deep learning beginners. There are several other popular deep learning frameworks such as TensorFlow, Keras, Chainer, and ONNX. TensorFlow was developed by Google and now includes Keras (previously a separate framework). I chose to deepen my knowledge in PyTorch because it is easy to learn and is commonly used for deep learning. Fastai is another deep learning open source library that is really awesome and intuitive to use. While using Fastai, I found myself curious about the inner workings so it's a plus that fastai wraps PyTorch as I can gain a better understanding of both libraries at once. Two birds, one stone!

In this PyTorch course, the instructor shared three deep learning model examples to illustrate the basic capabilities of PyTorch:

  * Regressions
  * Classifiers



# **Build Regression Models in PyTorch**

  * Created a Sequential feed forward neural network to approximate a linear regression model
  * Used a model with 3 layers: 
    * nn.Linear (input), nn.ReLu (hidden) and nn.Linear (output)
    * Activation function ReLu captures the non-linear relationships between variables
    * Other activation functions are Sigmoid or Tanh
  * Defined a Loss Function (function over which the model optimizes, defines predictive power of model)
    * Chose Mean Squared Error (MSE) because MSE is good for regression problems
  * Defined an Optimization function
    * Selected Adam because it is efficient 
  * Converted all train and test data sets (from numpy arrays) to torch tensors
  * If the data set is large and cannot be held in your computer's memory, you should use a DataLoader to iterate over the data in batches. It also permits shuffling of the data during model training.



## **How Backpropagation Works**

  * Steps make up Epochs
    * 1 Step is trained over 1 batch of data
    * 1 epoch represents training the model over the entire training data set
  * **For each epoch:**
    * **For each batch of training data:**
      * Calc loss using the function = f(y_pred, y_train_tensor)
      * Zero the gradients over the loss function (model.zero_grad)
      * Update the gradients in the model using loss.backward()
      * Update the model parameters based on the optimizer by calling optimizer.step()



# **Build Classification Models in PyTorch**

  * Build multi-classifier model that returns predicted class and probability scores of belonging to each class
  * Import torch.functional as F to build custom NNs in Torch
  * Create a NN class that specifies the architecture of the model
    * Accepts nn.Module
    * __init__: defines number and types of layers (input, hidden and output, Linear, Dropout, Activation Functions, etc.)
    * Define forward() function that returns predictions from the model 
      * Accepts training data.
    * Log softmax function is applied to the output layer to get the probability scores for each target class
    * Negative Log Likelihood (NLL) used as loss function 
    * Softmax + Cross-entropy = Log Softmax + NLL loss (but the latter is more numerically stable, faster and more efficient)
  * model.train() activates dropout layers before actually training the model
