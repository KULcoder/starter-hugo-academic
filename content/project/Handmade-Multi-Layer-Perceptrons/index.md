---
title: Handmade Multi Layer Perceptron
summary: An implementation of Multi-Layer-Perceptron model with Stochastic Gradient Descent with CuPy. And designed to be easy to reuse.
tags:
  - Deep Learning
date: '2022-12-01T00:00:00Z'

# Optional external URL for project (replaces project detail page).
external_link: ''

image:
  focal_point: Smart

links:
# url_code: 'https://github.com/KULcoder/Multi-Layer-Perceptron-with-Cupy-and-Application'
url_code: ''
url_pdf: ''
url_slides: ''
url_video: ''

# Slides (optional).
#   Associate this project with Markdown slides.
#   Simply enter your slide deck's filename without extension.
#   E.g. `slides = "example-slides"` references `content/slides/example-slides.md`.
#   Otherwise, set `slides = ""`.
slides: ""
---
(Detailed implementation can be found in the source code.)

# Implementation

## Back-Propagation
Back-propagation is one of the cornerstones of modern deep neural networks. In this project, we implement back-propagation by adhering to the following rules:

![Learning Rule](images/formula.png)  

## Activation Functions
Three activation functions have been implemented: 'sigmoid', 'tanh', and 'ReLU'.

## Momentum Method
This method uses an accumulated gradient, which can theoretically accelerate training and help avoid local minima.

## Regularization
Both L1 and L2 regularization methods have been implemented.

# Performance

## CIFAR-10
Source: [CIFAR10](https://www.cs.toronto.edu/~kriz/cifar-10-python.tar.gz)

**Test Accuracy**: ~50%

## MNIST
Source: [MNIST](https://www.openml.org/search?type=data&status=active&id=554)

**Test Accuracy**: ~97%

<!-- # How to Use
1. Copy following files
  - NeuralNet.py
  - Util.py
  - PersonalMLP.py
2. Use this template

  ```python
   import PersonalMLP
   
   # load data 
   X_train = ...
   y_train = ...
   X_test = ...
   y_test = ...
   X_valid = ...
   y_valid = ...
   
   # ensure to normalize the X data, as a requirement of neural network
   
   # configs
   config = personalMLP.Config()
   # check configs
   config()
   # change configs
   config.hyperparameter1 = specific_value
   config.hyperparameter2 = specific_value
   
   # set up the model
   model = PersonalMLP.Model(config)
   
   # train the model
   statistics = model.train(X_train, y_train, X_valid, y_valid)
   
   # use the model to generate predict test
   y_test_pred = model.forward(X_test)
   
   # calculate matrics and demonstrate result
   ```

3. Format of Hyperparameter
  ```python
  layer_specs: [3072, 128, 10]
  activation: tanh
  learning_rate: 0.01
  batch_size: 128
  epochs: 100
  early_stop: True
  early_stop_threshold: 5
  L1_constant: 0
  L2_constant: 0
  momentum: False
  momentum_gamma: 0.9
  ``` -->
