---
title: Amazon Insights 360
summary: A Deep Dive into Reviews and Recommendations.
tags:
  - Deep Learning
  - Data Analytics
date: '2023-03-01T00:00:00Z'

# Optional external URL for project (replaces project detail page).
external_link: ''

image:
  focal_point: Smart

links:
url_code: 'https://github.com/KULcoder/Comprehensive-Amazon-Reviews-Project/tree/main'
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

(Detailed methods and results in source code)

# Section 1: EDA

Dive deeper into the electronics reviews in Amazon Reviews Dataset (3,091,024 data points).

## Cleaning the data
- Missing Values
- Duplicate Values
- Irrelevant Data

## Univariate Analysis
- Basic statistics of each features

Found that the reviews ratings are skewed to higher side and the helpful and total votes skewed to lower side.
### Review Date
![Review Date](images/review_dates.png)
Review data are growing rapidly and causing a much larger portion of data points clustered after 2012.
![Review Weekdays](images/review_weekdays.png)
People likes to write reviews on weekdays compares to weekends.

### Review Word Cloud
![Review Wordcloud](images/review_wordcloud.png)

## Multivariate Analysis

### Ratings vs. Brands
![Rating Brands](images/rating_brands.png)

### Ratings vs. Review Length
![Rating Length](images/review_length_rating.png)
Notice that lowest and highest ratings generally have a shorter review length.

# Section 2: Recommender System

**Problem Statement**: Given an user-item pair, predict how will this user rate this item.

## Similarity Based Model
By using Jaccard similarity, we estimate their similarities. 

**Mean Squared Error**: 1.947

## Latent Factor Model
Using singular value decomposition, we can find latent factor representing each user/item.
- with `surprise`

**Mean Squared Error**: 1.689

## Neural Network: Neural Collaborative Filtering
Reference: https://arxiv.org/abs/1708.05031
Direct use neural networks to find the relationships between users and items.
- with `PyTorch` and `PyTorch Lightning`

**Mean Squared Error**: 0.701