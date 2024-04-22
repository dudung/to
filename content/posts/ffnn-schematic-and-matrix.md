+++
title = 'ffnn schematic and matrix'
date = 2024-04-22T09:53:00+07:00
draft = false
math = true
tags = ['machine learning', 'neural netwok', 'feed forward']
url = '0018'
authors = ['viridi']
+++
Schematic for feed forward neural network and its matrix <!--more-->


## intro
A Feedforward Neural Network (FFNN) is the simplest kind of artificial neural network, where information moves only in one direction, from the input layer through any hidden layers and finally to the output layer [^rameshkumar_2023]. With the unidirectional flow of data, absence of cycles, and reliance on backpropagation and activation functions, it forms a crucial component of the artificial intelligence (AI) and machine learning (ML) landscape, due to its ability to model complex relationships through a relatively simple architecture, which has made this kind of neural network (NN) indispensable in both historical and contemporary contexts [^fox_2024]. Normaly a schematic of FFNN is showing flow of data from left to right, i.e. input layer is on the left and output layer is on the right, but there is also a visualization of NN showing flow of data from right to left [^fulton_2019].

In this post both schematics showing flow of data from left to right or from right to left are presented and also their matrix representation, in showing which schematic would have better relation to its mathematical formulation.


## schematics
A FNN with input layer, hidden layer, and output layer with some nodes can be drawn as follow.


## notes
[^rameshkumar_2023]: Sasirekha Rameshkumar, "Deep Learning Basics — Part 7 — Feed Forward Neural Networks (FFNN)", Medium, 7 Dec 2023, url https://medium.com/p/93a708f84a31 [20240422].
[^fox_2024]: Josh Fox, "Feedforward Neural Network", Deepgram, 16 Feb 2024, url https://deepgram.com/ai-glossary/feedforward-neural-network [20240422].
[^fulton_2019]: Lawrence V. Fulton, Diane Dolezel, Jordan Harrop, Yan Yan, Christopher P. Fulton, "Classification of Alzheimer’s Disease with and without Imagery Using Gradient Boosted Machines and ResNet-50", Brain Sciences [Brain Sci], vol 9, no 9, p 212, Sep 2019, url http://doi.org/10.3390/brainsci9090212.