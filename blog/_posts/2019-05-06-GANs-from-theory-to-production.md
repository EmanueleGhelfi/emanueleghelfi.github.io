---
author: "manughelfi"
layout: post
did: "blog6"
title:  "PyCon X - GANs: From Theory to Production"
slug:  pyconx-gans
date:   2019-05-06 8:00:00
categories: machine-learning
tags: machine-learning tutorial conference pyconit gan image-translation
description: "GANs: from theory to production."
gh-repo: "zurutech/gans-from-theory-to-production"
gh-badge: [star, watch, follow, fork]
social-share: true
comments: true
image_sliders:
  - pycon
---
Me and my colleagues (Federico Di Mattia, Paolo Galeone, Michele De Simoni) held the training: "Deep Diving into GANs: From Theory To Production" at [PyCon X](https://www.pycon.it/conference/talks/deep-diving-into-gans-form-theory-to-production) in Florence.

<center>
<img src="/blog/figs/gan/social.png" style="width: 80%;" alt="Figure 1 - PyConX">
</center>

GANs are the new hottest topic in the ML arena; however, they present a challenge for the researchers and the engineers alike. Their design, and most importantly, the code implementation has been causing headaches to the ML practitioners, especially when moving to production.

Starting from the very basic of what a GAN is, passing trough Tensorflow implementation, using the most cutting-edge APIs available in the framework, and finally, production-ready serving at scale using Google Cloud ML Engine.

The material is available on [Github](https://github.com/zurutech/gans-from-theory-to-production).

Take a look at the slides of the theory part:

<center>
<iframe src="//www.slideshare.net/slideshow/embed_code/key/gO6APBMKpbeKWE" width="595" height="485" frameborder="0" marginwidth="0" marginheight="0" scrolling="no" style="border:1px solid #CCC; border-width:1px; margin-bottom:5px; max-width: 100%;" allowfullscreen> </iframe> <div style="margin-bottom:5px"> <strong> <a href="//www.slideshare.net/EmanueleGhelfi/gan-theory-and-applications-143737572" title="GAN - Theory and Applications" target="_blank">GAN - Theory and Applications</a> </strong> from <strong><a href="https://www.slideshare.net/EmanueleGhelfi" target="_blank">Emanuele Ghelfi</a></strong> </div>
</center>

The training is divided in 4 parts:
- [GANs - Theory and applications](https://github.com/zurutech/gans-from-theory-to-production) - [Slides](https://www.slideshare.net/EmanueleGhelfi/gan-theory-and-applications-143737572)
- [GANs in Tensorflow](https://github.com/zurutech/gans-from-theory-to-production/tree/master/2.%20GANs%20in%20Tensorflow)
- [TFGAN](https://github.com/zurutech/gans-from-theory-to-production/tree/master/3.%20TFGAN)
- [Production](https://github.com/zurutech/gans-from-theory-to-production/tree/master/4.%20Production)

Here some photos of the tutorial:

{% include slider.html selector="pycon" %}

<span>
</span>