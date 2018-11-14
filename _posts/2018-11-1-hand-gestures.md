---
layout: post
title: "Wisture: Touch-less Hand Gesture Classification in Unmodified Smartphones Using Wi-Fi Signals"
date: 2018-11-1
category: machine learning
tags: [time series, LSTM, pattern recognition, Android]
---
Our paper, (together with [Dr. Ramviyas Parasuraman](http://cobweb.cs.uga.edu/~ramviyas))
got accepted for publication in IEEE Sensors Journal (2018). Subset of the 
work reported was part of my master's thesis. A preprint can be found 
[here](https://arxiv.org/abs/1707.08569), and the paper can be found 
[here](https://ieeexplore.ieee.org/document/8493572).

The paper introduces Wisture, a solution for recognizing touch-less dynamic 
hand gestures on smartphones from the Wi-Fi Received Signal Strength (RSS). 
Unlike other Wi-Fi based gesture recognition methods, the proposed
method does not require a modifying the smartphone hardware or the operating 
system, and performs the gesture recognition without interfering with the 
normal operation of other smartphone applications.
A Long Short-Term Memory (LSTM) Recurrent Neural Network (RNN) is trained to
predict hand gestures from a pre-processed Wi-Fi RSS input sequence.

Below is a video demonstration of Wisture.

<a href="https://youtu.be/5v4KpAFvxpU" target="_blank"><img src="{{ site.baseurl }}/public/posts_imgs/wisture.png" title="Click to play"></a>
