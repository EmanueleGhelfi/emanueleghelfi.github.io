---
author: "manughelfi"
layout: post
title:  "Paper Notes: Toward Multimodal Image-to-Image Translation"
slug:  multimodal-image-to-image-translation
date:   2019-06-26 8:00:00
categories: machine-learning
tags: machine-learning gan paper-notes image-translation
description: "Multimodal Image-To-Image Translation"
mathjax: true
social-share: true
comments: true
---
The paper [Toward Multimodal Image-to-Image Translation](https://junyanz.github.io/BicycleGAN/) {% cite zhu_toward_2017 %} faces the problem of multimodal image-to-image translation in a principled way. The same problem is faced in {% cite isola_image--image_2016 %} (pix2pix) but in a not-so-effective manner (enabling Dropout at inference time).

<blockquote class="blockquote"><p>
In this paper, the authors encourage a <bold>bijection</bold> between the output and the latent code. 
</p>
</blockquote>

**What does it mean?**

A bijection is an **invertible** mapping. If the mapping is invertible it means that given a latent vector and a condition the output is unique. At the same time, given the same condition and a different latent vector, corresponds a different output. In other words the latent code contains information about the output.

## The problem: Multimodal Image-to-Image Translation

The problem of image-to-image translation is inherently ambiguous since at a **single** input image may corresponds **many** outputs. 

<center>
<figure>
<a href="/blog/figs/multimodal/teaser.jpg"> <img src="/blog/figs/multimodal/teaser.jpg" style="width: 80%;" alt="Figure 1 - Multimodal"> </a>
<figcaption> Multimodal Image-to-Image translation, from {% cite zhu_toward_2017 %} </figcaption>
</figure>
</center>

The generator in this context needs to find a mapping from the source domain to a **distribution** of potential results.

## Possibilities and Related Work

In order to encourage a variety of results the pix2pix model uses two different approaches:

- Concatenate a latent vector to the condition. 

- Enable Dropout at inference time.

The concatenation of latent vector is not very effective in the pix2pix case since it's ignored by the model. 

The Dropout at inference time is not a principled and controllable way to perform multimodal image-to-image translation.

## BicycleGAN

The idea, as said before, is to encourage a bijection between output and latent space.

The authors propose different options.

Notation:
- A is the input image (condition)
- B is the target image (real image corresponding to the input A)
- z is the latent vector
- \\( \widehat{B} \\) is the image generated starting from A and z \\( \widehat{B} = G(A, z) \\)
- G is the Generator
- E is the Encoder
- D is the Discriminator

**cVAE-GAN**: Conditional Variational AutoEncoder GAN. First encode B (target image) into latent space through E. The latent distribution is regularized through KL-penalty, enforcing a structure on the latent space and permitting sampling during inference. 

**cLR-GAN**: Conditional Latent Regressor GAN. Feed a **random** latent vector into G, the encoding of \\( G(A, z) \\) should resemble the feeded noise z. In other words we require:

$$
E(G(A, z)) = \widetilde{z} \approx z .
$$

**BicycleGAN**: Combine both **cVAE-GAN** and **cLR-GAN** to enforce the connection between the encoding and the output.

## Losses

Bicycle GAN combines different losses. Let's pass through all of them.

### Pix2Pix Loss

The Pix2Pix loss combines the adversarial loss and the L1 loss between the generated output and the real output. In math therms:

$$
\mathcal{L}_{\text{GAN}}(G, D)  = E[\log (D(A, B))] + E[\log (1 - D(A, G(A)))]
$$

$$
\mathcal{L}_{1}(G)  = ||B - G(A)||_1
$$

Using a latent vector this becomes \\( G(A, z) \\) with z coming from the prior distribution (i.e. \\( z \sim p_z \\) ).

### cVAE-GAN

The cVAE-GAN model uses also the Encoder and enforces the random vector to contain information about the target image.

$$
\mathcal{L}_{\text{GAN}}^{\text{VAE}}(G, D, E) = E[\log (D(A, B))] + E[\log (1 - D(A, G(A, E(B))))]
$$

$$
\mathcal{L}_{1}^{\text{VAE}}(G, E)  = ||B - G(A, E(B))||_1
$$

To enable sampling at inference time we need to add a KL penalty:

$$
\mathcal{L}_{KL}(E) = KL(\mathcal{N}(0,1), E(B))
$$

### cLR-GAN

We have z coming from the prior distribution, thus we cannot enforce an L1 penalty. This because for an input image we have multiple output image (remember, we are in a multimodal setting).
By the way the goal of this part is to recover the latent vector starting from the generated image. In order to do this we add an L1 loss on the latent vectors:

$$
\mathcal{L}_{1}^{LR}(G,E)= ||z-E(G(A,z))||_1
$$

In words, E should be able to replicate the input latent vector.

### BicycleGAN

Bicycle GAN combines all the previous losses:

$$
\mathcal{L}_{\text{Bi}} = \mathcal{L}_{\text{GAN}}^{\text{VAE}} + \lambda_1 \mathcal{L}_{1}^{\text{VAE}} + \mathcal{L}_{\text{GAN}} + \lambda_{LR} \mathcal{L}_{1}^{LR} + \lambda_{KL} \mathcal{L}_{KL}
$$

## How to feed noise inside G?

The authors explored two ways of injecting the latent vector z to in the generator:

- add_to_input: spatially replicate a Z-dimensional latent vector z to an H × W × Z tensor and concatenate it with the H × W × 3 input image
- add_to_all: we add z to each intermediate layer of the network G, after spatial replication to the appropriate sizes

## Details

- The generator is a UNET model
- The \\( \mathcal{L}_{\text{GAN}} \\) loss is actually a [Least Square GAN loss](https://arxiv.org/abs/1611.04076) {% cite  leastsquaregan %}
- **Not** conditioning the discriminator D on input A leads to better results
- Hyperparameters: \\( \lambda = 10 \\), \\( \lambda_{LR} = 0.5 \\) and \\( \lambda_{KL} = 0.01 \\)
- Train using Adam with a batch size of 1 and with a learning rate of 0.0002
- latent dimension \\(||z|| = 8\\) across all the datasets

## Results

<center>
<figure>
<a href="/blog/figs/multimodal/results_matrix.jpg"> <img src="/blog/figs/multimodal/results_matrix.jpg" style="width: 80%;" alt="Figure 1 - Multimodal"> </a>
<figcaption> Multimodal Image-to-Image translation, from {% cite zhu_toward_2017 %} </figcaption>
</figure>
</center>


References
----------

{% bibliography --cited %}
