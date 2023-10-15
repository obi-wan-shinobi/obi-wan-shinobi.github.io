---
layout: page
title: Galaxy EfficientNets
description: A galaxy morphology classification project dubbed "The Galaxy Zoo 2"
img: assets/img/galaxy-zoo/thumbnail.jpg
importance: 1
category: Machine Learning
related_publications: kalvankar2020galaxy
---

# Introduction

Studying and categorizing galaxies has long been a challenge in astrophysics. Scientists have worked tirelessly to identify distinct groups of galaxies, examining their traits to understand the complex processes behind their formation. Galaxy morphology, driven by physical characteristics and orbital structures, is a key focus, where a galaxy's gravitational potential influences its orbital families, resulting in unique appearances like bars, rings, and bulges.

Our project aimed to create an efficient system for automated galaxy classification, reducing the labor-intensive nature of manual classification. With the growing volume of data from sky surveys, we harnessed deep learning to address this need.

We tackled two main challenges. First, using Convolutional Neural Networks (CNNs), we quantitatively assessed morphological features to predict vote fractions. Second, we directly classified galaxy images into seven morphological classes using these predictions.

By employing an ensemble of EfficientNet architectures, we achieved promising results in both vote-fraction predictions and image classification. Our project successfully automated galaxy classification, alleviating the human effort required for this time-consuming task.

<div class="row">
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.html path="assets/img/galaxy-zoo/samples.jpg" title="galaxy classes" class="img-fluid rounded z-depth-1" %}
    </div>
</div>
<div class="caption">
    Example galaxy images from the dataset. Each row represents a class. From top to bottom, their Galaxy Zoo 2 labels are class 0, 1, 2, 3, 4, 5 and 6
</div>

# Dataset

After the retirement of the Galaxy Zoo 1 project, a new challenge, Galaxy Zoo 2, was initiated. This project entailed the analysis of 304,122 galaxy images sourced from the Sloan Digital Sky Survey. Both Galaxy Zoo projects were citizen science endeavors that received over 16 million image classifications.

While the original Galaxy Zoo project focused on categorizing galaxies into broad groups like early-types, late-types, or mergers, Galaxy Zoo 2 took a more granular approach by quantifying morphological features such as bars, bulges, disks, spirals, and more. It introduced a system of quantified data, providing information on the strength of bulges and the number of spiral arms.

Our project was developed in the context of the Galaxy Zoo challenge, hosted on Kaggle, with the objective of automating galaxy classification. The primary image dataset comprised the brightest 25% of resolved galaxies from the Sloan Digital Sky Survey's North Galactic Cap. The competition aimed to develop a generalized algorithm applicable to various images, and the dataset was meticulously selected to represent diverse colors, sizes, and morphologies.

The training set included 61,578 RGB images with probabilities for 37 categories in the GZ2 decision tree, while the evaluation set consisted of 79,975 similar images without morphological data. The goal was to predict these probabilities with precision, transforming a classification task into a regression problem. Our model's performance was evaluated using root-mean-squared error (RMSE) for predicted values against known probabilities.

Additionally, the study segmented galaxies into seven classes and refined the dataset by applying thresholds based on sufficient votes. This approach facilitated more specific classifications, with class sizes ranging from 578 to 8107 samples. The resulting dataset consisted of 25,941 images, divided into a 9:1 train-test ratio, with 23,352 images for training and 2,589 for testing.

<table class="mb-2">
  <tr>
    <th>Class</th>
    <th>Sample</th>
    <th>Tasks</th>
    <th>Selection</th>
    <th>Nsample</th>
  </tr>
  <tr>
    <td rowspan="3">0</td>
    <td rowspan="3">Completely round</td>
    <td>T01</td>
    <td>𝑓<sub>𝑠𝑚𝑜𝑜𝑡ℎ</sub> ≥ 0.469</td>
    <td rowspan="3">8107</td>
  </tr>
  <tr>
    <td>T07</td>
    <td>𝑓<sub>𝑐𝑜𝑛𝑝𝑙𝑒𝑡𝑒𝑙𝑦𝑟𝑜𝑢𝑛𝑑</sub> ≥ 0.5</td>
  </tr>
  <tr>
    <td>T06</td>
    <td>𝑓<sub>𝑜𝑑𝑑/𝑛𝑜</sub> ≥ 0.5</td>
  </tr>
  <tr>
    <td rowspan="3">1</td>
    <td rowspan="3">In-between</td>
    <td>T01</td>
    <td>𝑓<sub>𝑠𝑚𝑜𝑜𝑡ℎ</sub> ≥ 0.469</td>
    <td rowspan="3">7782</td>
  </tr>
  <tr>
    <td>T07</td>
    <td>𝑓<sub>𝑖𝑛−𝑏𝑒𝑡𝑤𝑒𝑒𝑛</sub> ≥ 0.5</td>
  </tr>
  <tr>
    <td>T06</td>
    <td>𝑓<sub>𝑜𝑑𝑑/𝑛𝑜</sub> ≥ 0.5</td>
  </tr>
  <tr>
    <td rowspan="3">2</td>
    <td rowspan="3">Cigar shaped</td>
    <td>T01</td>
    <td>𝑓<sub>𝑠𝑚𝑜𝑜𝑡ℎ</sub> ≥ 0.469</td>
    <td rowspan="3">578</td>
  </tr>
  <tr>
    <td>T07</td>
    <td>𝑓<sub>𝑐𝑜𝑛𝑝𝑙𝑒𝑡𝑒𝑙𝑦𝑟𝑜𝑢𝑛𝑑</sub> ≥ 0.5</td>
  </tr>
  <tr>
    <td>T06</td>
    <td>𝑓<sub>𝑜𝑑𝑑/𝑛𝑜</sub> ≥ 0.5</td>
  </tr>
  <tr>
    <td rowspan="3">3</td>
    <td rowspan="3">Lenticulars</td>
    <td>T01</td>
    <td>𝑓<sub>𝑓𝑒𝑎𝑡𝑢𝑟𝑒𝑠/𝑑𝑖𝑠𝑘</sub> ≥ 0.430</td>
    <td rowspan="3">3780</td>
  </tr>
  <tr>
    <td>T02</td>
    <td>𝑓<sub>𝑒𝑑𝑔𝑒−𝑜𝑛/𝑦𝑒𝑠</sub> ≥ 0.602</td>
  </tr>
  <tr>
    <td>T06</td>
    <td>𝑓<sub>𝑜𝑑𝑑/𝑛𝑜</sub> ≥ 0.5</td>
  </tr>
  <tr>
    <td rowspan="4">4</td>
    <td rowspan="4">Barred spirals</td>
    <td>T01</td>
    <td>𝑓<sub>𝑓𝑒𝑎𝑡𝑢𝑟𝑒/𝑑𝑖𝑠𝑘</sub> ≥ 0.430</td>
    <td rowspan="4">827</td>
  </tr>
  <tr>
    <td>T02</td>
    <td>𝑓<sub>𝑒𝑑𝑔𝑒−𝑜𝑛/𝑛𝑜</sub> ≥ 0.715</td>
  </tr>
  <tr>
    <td>T03</td>
    <td>𝑓<sub>𝑏𝑎𝑟/𝑦𝑒𝑠</sub> ≥ 0.715</td>
  </tr>
  <tr>
    <td>T04</td>
    <td>𝑓<sub>𝑠𝑝𝑖𝑟𝑎𝑙/𝑦𝑒𝑠</sub> ≥ 0.619</td>
  </tr>
  <tr>
    <td rowspan="4">5</td>
    <td rowspan="4">Unbarred spirals</td>
    <td>T01</td>
    <td>𝑓<sub>𝑓𝑒𝑎𝑡𝑢𝑟𝑒/𝑑𝑖𝑠𝑘</sub> ≥ 0.430</td>
    <td rowspan="4">3307</td>
  </tr>
  <tr>
    <td>T02</td>
    <td>𝑓<sub>𝑒𝑑𝑔𝑒−𝑜𝑛/𝑛𝑜</sub> ≥ 0.715</td>
  </tr>
  <tr>
    <td>T03</td>
    <td>𝑓<sub>𝑏𝑎𝑟/𝑛𝑜</sub> ≥ 0.715</td>
  </tr>
  <tr>
    <td>T04</td>
    <td>𝑓<sub>𝑠𝑝𝑖𝑟𝑎𝑙/𝑦𝑒𝑠</sub> ≥ 0.619</td>
  </tr>
  <tr>
    <td rowspan="2">6</td>
    <td rowspan="2">Irregular</td>
    <td>T06</td>
    <td>𝑓<sub>𝑜𝑑𝑑/𝑦𝑒𝑠</sub> ≥ 0.420</td>
    <td rowspan="2">1560</td>
  </tr>
  <tr>
    <td>T08</td>
    <td>𝑓<sub>𝑑𝑖𝑠𝑡𝑢𝑟𝑏𝑒𝑑|𝑖𝑟𝑟𝑒𝑔𝑢𝑙𝑎𝑟 |𝑜𝑡ℎ𝑒𝑟 |𝑚𝑒𝑟𝑔𝑒𝑟 |𝑑𝑢𝑠𝑡𝑙𝑎𝑛𝑒</sub> ≥ 0.5</td>
  </tr>
</table>

# Approach

#### Role: Lead Researcher

#### Approach

- We surveyed different papers and methods that either empirically
  or theoritically provided a basis for a system that could be potentially implemented. A
  systematic study of galaxy morphologies and classification methods involving parametric
  and non-parametric approaches was done.

- The next step after having finalized the dataset was looking for Deep Learning methods
  that could be used. A deeper look into CNNs revealed a set of architectures fine-tuned
  for this particular task. We decided to use the VGG architecture and then look into
  Residual learning that would potentially boost the model performance over the dataset.
  A rigirous study of deep learning architectures involving Convolutional Neural Networks
  was conducted.

- Having finalized the approach, it was necessary to have an experimental setup ready.
  We decided to set up a data pipeline and network training pipeline to train the model
  over the dataset. We discovered that the dataset was not enough for the model to train
  over, hence, we decided to use data augmentation to avoid over-fitting. We
  programmed the entire network in Tensorflow and keras and the pipeline was
  set up using python. The rutime was set up in Google Colaboratory with an Nvidia
  Tesla K80 GPU and we begun our search.

- After the experimental setup was ready, we decided to implement a variety of
  architectures and search for even more promising architectures along the way. We
  created custom models with references from empirically proven architectures
  and trained them over weeks. We finally decided to use the EfficientNet
  architectures that gave the best results.

- We documented results at each stage and kept training the networks while tuning the
  hyperparameters to achieve the best results.

# Conclusion and Results

We achieved really decent results with the EfficientNet models but we decided to use an
ensemble of more than one model to achieve a greater score so as to grab a place on the
public leaderboard of the Galaxy Zoo 2 challenge.

Our results were graded using the standard competition metric, i.e. the rmse score. We
achieved an rmse score of 0.07765 and ranked in the top 3 on the public leaderboard.

The classification model provided us with decent accuracy of 93.7% on classifying the
galaxies into 7 classes with an F1 score of 0.8857.
