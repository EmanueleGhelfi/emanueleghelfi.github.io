---
author: "manughelfi"
layout: post
title:  "Paper Notes: Toward Multimodal Image-to-Image Translation"
slug:  "Paper Notes: Toward Multimodal Image-to-Image Translation"
date:   2019-06-25 8:00:00
categories: machine-learning
tags: machine-learning computer-vision gan paper-notes
description: "Multimodal Image-To-Image Translation"
mathjax: true
social-share: true
comments: true
---
The paper [Toward Multimodal Image-to-Image Translation](https://junyanz.github.io/BicycleGAN/) {% cite zhu_toward_2017 %} faces the problem of multimodal image-to-image translation in a principled way. The same problem is faced in {% cite isola_image--image_2016 %} but in a not-so-effective manner (enabling Dropout at inference time).

<blockquote class="blockquote"><p>
In this paper the authors encourage a <bold>bijection</bold> between the output and the latent code. 
</p>
</blockquote>

**What does it mean?**

A bijection is an **invertible** mapping. If the mapping is invertible it means that given a latent vector and a condition the output is unique, at the same given the same condition a different latent vector it corresponds a different output. In other words the latent code contains information about the output.

## The problem: Multimodal Image-to-Image Translation

The problem of image-to-image translation is inherently ambiguous since a **single** input image may corresponds **many** outputs. 

<center>
<figure>
<a href="/blog/figs/multimodal/teaser.jpg"> <img src="/blog/figs/multimodal/teaser.jpg" style="width: 80%;" alt="Figure 1 - Multimodal"> </a>
<figcaption> Multimodal Image-to-Image translation, from {% cite zhu_toward_2017 %} </figcaption>
</figure>
</center>

The generator in this context needs to find a mapping from the source domain to a distribution of potential results.

## Possibilities and Related Work

In order encourage a variety of results the pix2pix models uses two different approaches:

- Simply concatenate a latent vector to the condition. 

- Enable Dropout at inference time.

The concatenation of latent vector is not very effective in the pix2pix case since it's ignored by the model. 

The Dropout at inference time is not a principled and controllable way to perform multimodal image-to-image translation.

## Bicycle GAN

The idea, as said before is to encourage a bijection between output and latent space.

The authors propose different options.
Notation:
- A is the input image (condition)
- B is the target image (real image corresponding to the input A)
- z is the latent vector
- \\( \widehat{B} \\) is the image generated starting from A and z \\( \widehat{B} = G(A, z) \\)
- G is the Generator
- E is the Encoder
- D is the Discriminator

**cVAE-GAN**: Conditional Variational AutoEncoder GAN. First encode B into latent space through E. Latent distribution is regularized through KL-penalty, enforcing a structure of the latent space and permitting sampling during inference.

**cLR-GAN**: Feed a random latent vector into G, the encoding of \\( G(A, z)) \\)
