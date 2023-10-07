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

(Detailed methods and results can be found in the source code.)

# Section 1: EDA

Delve into the electronics reviews from the Amazon Reviews Dataset, which comprises 3,091,024 data points.

## Cleaning the data
- Address missing values
- Remove duplicate values
- Filter out irrelevant data

## Univariate Analysis
- Evaluate basic statistics for each feature

It was observed that review ratings lean towards the higher end, whereas helpful and total votes are skewed towards the lower end.
### Review Date
![Review Date](images/review_dates.png)
There's a rapid growth in review data, leading to a significant concentration of data points after 2012.
![Review Weekdays](images/review_weekdays.png)
Users tend to write reviews on weekdays compared to weekends.

### Review Word Cloud
![Review Wordcloud](images/review_wordcloud.png)

## Multivariate Analysis

### Ratings vs. Brands
![Rating Brands](images/rating_brands.png)

### Ratings vs. Review Length
![Rating Length](images/review_length_rating.png)
It's noticeable that both the lowest and highest ratings typically correspond to shorter review lengths.

# Section 2: Recommender System

**Problem Statement**: For a given user-item pair, how will the user rate this item?

## Similarity Based Model
Utilizing the Jaccard similarity metric, their similarities can be estimated.

**Mean Squared Error**: 1.947

## Latent Factor Model
Through singular value decomposition, latent factors representing each user or item can be discerned.
- with `surprise`

**Mean Squared Error**: 1.689

## Neural Network: Neural Collaborative Filtering
Reference: [Neural Collaborative Filtering](https://arxiv.org/abs/1708.05031)

Leverage neural networks to uncover relationships between users and items.
- with `PyTorch` and `PyTorch Lightning`

**Mean Squared Error**: 0.701

# Section 3: NLP with BERT

**Problem Statement**: Based on the review content, can we predict the rating and determine whether it's positive or negative?

## TF-IDF with Logistic Regression

- with `Sci-Kit Learn`

**Sentiment Accuracy**: 91.95%

### Confusion Matrix
![tfidf Confusion Matrix](images/tfidf_confusion.png)

## BERT
Reference: [BERT: Pre-training of Deep Bidirectional Transformers for Language Understanding](https://arxiv.org/abs/1810.04805)

Using the BERT model (part of transformers), and transfer learning techniques.

**Sentiment Accuracy**: 98.34%

### Confusion Matrix
![BERT Confusion Matrix](images/bert_confusion.png)


