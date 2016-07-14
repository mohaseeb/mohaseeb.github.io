---
layout: post
title: "Predicting human face attributes from images with deep learning"
date: 2016-05-30
category: deep learning
tags: [image recognition, transfer learning, MatConvnet]
---
![attributes_prediction]({{ site.baseurl }}/public/posts_imgs/attributes.png)
Deep learning is prooved powerful in solving many problems, but requires plenty of data and computational resources which unfortunately few possess (the likes of Google, facebook and Amazon, etc..). The good news is that those who don't have these resources can still benefit from deep learning using [transfer learning](https://en.wikipedia.org/wiki/Inductive_transfer) techniques. Transfer learning alows one to use a model trained on a task X and fine-tune it for another taks Y (not that different from X), using a small dataset related to task Y. One still needs to find a pretrained deep model available for use.

For the final project of an image recognition course (at KTH), I used deep Convolutional Neural Networks (CNN) to predict human attributes like skin tune, hair color and age from a face image. I used a dataset of face images annotated with facial attributes (40 attributes per image), called [CelebA](http://mmlab.ie.cuhk.edu.hk/projects/CelebA.html), to fine-tune a CNN pre-trained for a general object classification task (a VGG CNN trained for the [ImageNet](http://www.image-net.org/challenges/LSVRC/) challenge), to predict facial attributes given a face image. As a baseline, a linear classifier was trained for attribute prediction using representations extracted from the pre-trained CNN. When trained on 20% of CelebA dataset, the fine-tuned CNN achieved an average accuracy of ∼ 89.9% predicting 40 different attributes per image.

Check [this document]({{ site.baseurl }}/public/posts_imgs/mohamed_abdulaziz_project_report.pdf) for the deep network details, the fine-tuning procedure, the conducted experiments and a discussion on the results.
