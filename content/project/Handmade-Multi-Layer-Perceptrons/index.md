---
title: Handmade Multi Layer Perceptron
summary: An implementation of Multi-Layer-Perceptron model with Stochastic Gradient Descent with CuPy. And designed to be easy to reuse.
tags:
  - Deep Learning
date: '2022-12-01T00:00:00Z'

# Optional external URL for project (replaces project detail page).
external_link: ''

image:
  caption: Photo by rawpixel on Unsplash
  focal_point: Smart

links:
url_code: 'https://github.com/KULcoder/Multi-Layer-Perceptron-with-Cupy-and-Application'
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
Back propagation is the one of the foundations of modern deep neural network. In this project, back propagation is implemented by following rules:

Learning Rule: 

$w_{ij} = w_{ij} - \alpha \frac{\partial J}{\partial w_{ij}} = w_{ij} +\alpha \delta_j z_i$

Definition on $\delta$ (recursively):

- When $j$ is for the output layer units

$$
 \delta_j = t_j - y_j
$$

- When $j$ is for the hidden layer units

$$
 \delta_j = g'(a_j)\sum_k \delta_k w_{jk}
$$