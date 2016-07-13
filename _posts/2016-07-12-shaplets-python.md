---
layout: post
title: "Python implementation of the Learning Time-series Shapelets method (LTS)"
date: 2016-07-12
category: machine learning
tags: [time series, pattern recognition]
---
![attributes_prediction]({{ site.baseurl }}/public/posts_imgs/lts.png)

[Jump to usage](#usage) if you have no patience to hear my life story :). A month ago or so, I was looking for an implementation of a time-series classification/clustering method that uses shapelets, a widely researched topic within the time-series research community, and to my surprise, I found none <a name="found">1</a>. So I thought it will be great if I did an implementation and made it available to whoever interested. I was also motivated by the interesting idea behind [the LTS method](http://www.ismll.uni-hildesheim.de/pub/pdfs/grabocka2014e-kdd.pdf) method, and I imagined it would be fun to spend time to fully grasp the method and implement it.

A shapelet is a time-series sub-sequence that is discriminative to the members of one (or more) class. LTS learns a time-series classifier (that uses a set of shaplets) with stochastic gradient descent. Refer to the [LTS](http://www.ismll.uni-hildesheim.de/pub/pdfs/grabocka2014e-kdd.pdf) paper for details.

This implementation, [found here](https://github.com/mohaseeb/shaplets-python), views the model as a layered network (the shown diagram), where each layer implements a forward, a backward and parameters update method. This abstraction makes it easy to port the implementation to frameworks like Torch or Tensorflow. A bunch of unit-tests were also implemented for the forward and backward methods (so I can rest assured that the gradients are calculated correctly).

Note, the loss in my implementation is an updated version of the one in the paper, and that is to enable training a single network for all the classes in the dataset (rather than one network/class as I understood from the paper). The impact on performance caused by this deviation was not investigated. For details check the shapelets/network/cross_entropy_loss_layer.py in [the implementation](https://github.com/mohaseeb/shaplets-python).

## Usage ##
See below. Also have a look at example.py in [the implementation](https://github.com/mohaseeb/shaplets-python).

```python
from shapelets.classification import LtsShapeletClassifier
# create an LtsShapeletClassifier instance
classifier = LtsShapeletClassifier(K=20, R=3, L_min=30, epocs=2, regularization_parameter=0.01,
                                       learning_rate=0.01, shapelet_initialization='segments_centroids')
# train the classifier. train_data (a numpy matrix) shape is (# train samples X time-series length), train_label (a numpy matrix) is (# train samples X 1). 
classifier.fit(train_data, train_label, plot_loss=True)
# evaluate on test data. test_data (a numpy matrix) shape is (# test samples X time-series length)
prediction = classifier.predict(test_data)
```

Although I believe the architecture is good, I think the implementation is way from optimal, and there is plenty of room for improvement. Off the top of my head, the usage of python arrays/lists has to be improved.

For a stable training, make sure all the timeseries in the dataset are [standardized](https://en.wikipedia.org/wiki/Feature_scaling#Standardization) (i.e. each has zero mean and unit variance). 


<sup>[1](#found) At the beginning of my search, I tried to contact the author of the LTS method asking for access to his implementation. The author granted me access but that was late; after I was done with the python implementation :)</sup>