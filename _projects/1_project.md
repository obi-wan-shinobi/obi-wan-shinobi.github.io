---
layout: page
title: Galaxy EfficientNets
description: A galaxy morphology classification project dubbed "The Galaxy Zoo 2"
img: assets/img/galaxy-zoo/thumbnail.jpg
importance: 1
category: Machine Learning
Related_publications: kalvankar2020galaxy
---

# Introduction

The study of galaxies and their classification into distinct categories constitutes a long-standing challenge in the field of astrophysics. Over the years, physicists have diligently worked to identify and segregate galaxies into individual groups, systematically studying their inherent traits in an effort to unravel the intricate processes governing their formation. This quest entails a close examination of galaxy morphology, which is fundamentally determined by their physical characteristics and orbital structures. The configuration of a galaxy's gravitational potential dictates the types of orbital families that are present within it, each contributing to a distinctive appearance. Morphological features such as bars, rings, peanut bulges, and pseudo-bulges emerge as a result of the complex interplay of stars moving through specific regions in the space phase.

The primary objective of this project was to construct a robust and automated system for the classification of galaxies into various morphological classes, enabling a more efficient and comprehensive analysis of their characteristics and origins.

The visual classification of galaxies into morphological classes has traditionally been a labor-intensive endeavor, demanding significant manpower resources. However, the advent of sky surveys has ushered in an era of exponential data accumulation, emphasizing the pressing need for an automated system capable of classifying galaxies by extracting their morphological features. In response to this challenge, we harnessed the power of deep learning to streamline this process.

Our project primarily addressed two key challenges. The first was a regression problem, which involved utilizing Convolutional Neural Networks (CNNs) to calculate the vote-fractions of morphological features for a given galaxy. This allowed for a quantitative assessment of various morphological characteristics. The second challenge centered on classification, where we sought to eliminate the need for vote-fraction predictions and instead directly categorize galaxy images into one of the 7 morphological classes established by the vote fractions within the training data.

To tackle these problems effectively, we explored the application of an ensemble of EfficientNet architectures. Our approach yielded promising results for the vote-fraction predictions, and the classification model demonstrated its competence in accurately assigning galaxy images to their respective morphological categories. In the end, our project successfully implemented a robust system that automates the classification of galaxies based on their morphological features, reducing the human effort required for this time-consuming process.

<div class="row">
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.html path="assets/img/1.jpg" title="example image" class="img-fluid rounded z-depth-1" %}
    </div>
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.html path="assets/img/3.jpg" title="example image" class="img-fluid rounded z-depth-1" %}
    </div>
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.html path="assets/img/5.jpg" title="example image" class="img-fluid rounded z-depth-1" %}
    </div>
</div>
<div class="caption">
    Caption photos easily. On the left, a road goes through a tunnel. Middle, leaves artistically fall in a hipster photoshoot. Right, in another hipster photoshoot, a lumberjack grasps a handful of pine needles.
</div>
<div class="row">
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.html path="assets/img/5.jpg" title="example image" class="img-fluid rounded z-depth-1" %}
    </div>
</div>
<div class="caption">
    This image can also have a caption. It's like magic.
</div>

You can also put regular text between your rows of images.
Say you wanted to write a little bit about your project before you posted the rest of the images.
You describe how you toiled, sweated, _bled_ for your project, and then... you reveal its glory in the next row of images.

<div class="row justify-content-sm-center">
    <div class="col-sm-8 mt-3 mt-md-0">
        {% include figure.html path="assets/img/6.jpg" title="example image" class="img-fluid rounded z-depth-1" %}
    </div>
    <div class="col-sm-4 mt-3 mt-md-0">
        {% include figure.html path="assets/img/11.jpg" title="example image" class="img-fluid rounded z-depth-1" %}
    </div>
</div>
<div class="caption">
    You can also have artistically styled 2/3 + 1/3 images, like these.
</div>

The code is simple.
Just wrap your images with `<div class="col-sm">` and place them inside `<div class="row">` (read more about the <a href="https://getbootstrap.com/docs/4.4/layout/grid/">Bootstrap Grid</a> system).
To make images responsive, add `img-fluid` class to each; for rounded corners and shadows use `rounded` and `z-depth-1` classes.
Here's the code for the last row of images above:

{% raw %}

```html
<div class="row justify-content-sm-center">
  <div class="col-sm-8 mt-3 mt-md-0">
    {% include figure.html path="assets/img/6.jpg" title="example image"
    class="img-fluid rounded z-depth-1" %}
  </div>
  <div class="col-sm-4 mt-3 mt-md-0">
    {% include figure.html path="assets/img/11.jpg" title="example image"
    class="img-fluid rounded z-depth-1" %}
  </div>
</div>
```

{% endraw %}
