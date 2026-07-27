---
title: "Recurrent Neural Networks in PyTorch"
date: 2020-09-07T17:13:17Z
tags: [deep learning, neurons, pytorch, recurrent, rnn]
categories: [data science, deep learning, machine learning]
draft: false
---

Feed forward networks cannot learn from the past, but Recurrent Neural Networks (RNNs) can learn by accepting data in a sequence. Examples of applications for RNNs include the text autocomplete feature on your phone and performing language translations. 

Recurrent Neurons (RNs) act as the building blocks of RNNs. The difference between RNs and feed forward neurons is that RNs accept input x, at time t, as well as a hidden state or output from time t-1 from another RN. The output of a RN is a vector, unlike for a feed forward neuron. RNNs are trained (i.e. their weights are calculated) using backpropagation via Gradient Descent Optimization in time. Output from a single RNN layer at time instance,t is an input to the next layer. Each layer in the RNN represents an instance in time. 

RNN cells are composed of RNs, but there are other types such as Long/Short-Term Memory (LSTM). Long memory cells such as LSTM cells can recall what happened very far back in time, which RNs cannot do. RNN cells  are prone to gradient issues (where the gradient goes to zero and/or stops changing), which can be mitigated by LSTM cells. LSTM neurons have more memory or more hidden states than RNs as they have long-term and/or short term states. LSTM cells that store states for more than 1 period are called peephole connections. Gated Recurrent Unit (GRU) cells are another type of RNN cell, which are simplified LSTM cells with better performance.

# **Build a Character Generation Engine for Names Using RNNs**

  * Built a custom RNN for generating names in a selected language (English, Japanese, etc.)
  * The end user provides a starting character and desired language e.g. ‘L’ and English, then the RNN outputs the next character e.g. ‘u’ and a hidden state, which are both passed back to the proceeding layer of the RNN. This process is repeated until the end of sequence (EOS) character is found, which indicates that the character generation process for a single name is complete. 
  * NLL Loss is used to train the RNN
  * To train the RNN:
    * Initialize the hidden state to be all zeros (before the first character is generated)
    * Set gradient and loss to zero
    * Feed target names into the RNN- one character at a time 
    * Output the next character and hidden state for every character while summing the NLL Loss
    * Calculate the gradients via loss.backward()
    * Update the RNN weights using gradient and pre-specified learning rate
