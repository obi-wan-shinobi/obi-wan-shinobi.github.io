---
layout: page
title: Miyazaki GAN
description: Miyazaki Style landcape generation using cycle GANs
img: assets/img/miyazaki-gan/thumbnail.jpg
importance: 4
category: Machine Learning
---

An experiment to leverage the power of cycle-GANs to generate Studio Ghibli like anime landscapes from live images.
Cycle Generative Adversarial Networks, often abbreviated as Cycle GANs, are a
powerful class of deep learning models designed for image-to-image translation
tasks. They were introduced to the machine learning community by researchers at
UC Berkeley in 2017. Cycle GANs are particularly remarkable for their ability to
learn mappings between two different domains of images, such as transforming
photographs into paintings, making them the perfect tool for this use case.

# Data

Japanese landscapes are a mesmerizing fusion of natural beauty and cultural
significance, from the iconic Mount Fuji to serene Zen gardens, captivating with
their timeless charm and deep spiritual resonance. I used a selenium script to
scrape data off of an Instagram page [RawJapan](https://www.instagram.com/raw_japan_/?hl=en).
This page contains beautiful pictures of Japanese landscapes and proved to be the best source.

This is what that data looked like:

<div class="row">
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.html path="assets/img/miyazaki-gan/distribution-A.jpg" title="distribution A" class="img-fluid rounded z-depth-1" %}
    </div>
</div>
<div class="caption">
    Live landscapes: Distribution A.
</div>

I used a python script to extract frames from different Ghibli movies. This resulted in a large dataset with tons of duplicate images. I used VisiPics to identify and remove similar images from the dataset and we are left with a diverse collection of Ghibli images.

<div class="row">
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.html path="assets/img/miyazaki-gan/distribution-B.jpg" title="distribution B" class="img-fluid rounded z-depth-1" %}
    </div>
</div>
<div class="caption">
    Screenshots from Ghibli movies: Distribution B.
</div>

After training the GANs in cyclic fashion for about 3 epochs, we start getting wonderful results.

<div class="row">
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.html path="assets/img/miyazaki-gan/output1.png" title="output1" class="img-fluid rounded z-depth-1" %}
    </div>
</div>
<div class="row">
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.html path="assets/img/miyazaki-gan/output2.png" title="output2" class="img-fluid rounded z-depth-1" %}
    </div>
</div>
<div class="row">
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.html path="assets/img/miyazaki-gan/output3.png" title="output3" class="img-fluid rounded z-depth-1" %}
    </div>
</div>
<div class="row">
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.html path="assets/img/miyazaki-gan/output4.png" title="output4" class="img-fluid rounded z-depth-1" %}
    </div>
</div>
<div class="row">
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.html path="assets/img/miyazaki-gan/output5.png" title="output5" class="img-fluid rounded z-depth-1" %}
    </div>
</div>
<div class="caption">
    Outputs from the Generator
</div>

You can find details of implementation in the notebook [here](https://github.com/obi-wan-shinobi/Miyazaki-GAN/blob/master/Miyazaki_CycleGAN.ipynb).
