---
layout: page
title: Projects
subtitle: Presentations, Projects, Research, Blogs.
---


## Public presentations

* Deep Diving into GANs: from theory to production @ PyConX 2019, Florence. ([PyConX](https://www.pycon.it/conference/talks/deep-diving-into-gans-form-theory-to-production)), ([Github](https://github.com/zurutech/gans-from-theory-to-production)), ([SlideShare](https://www.slideshare.net/EmanueleGhelfi/gan-theory-and-applications-143737572))
* Reinforcement Learning in Configurable Environments: an Information Theoretic approach, Thesis discussion, 20.12.2018 ([SlideShare](https://www.slideshare.net/EmanueleGhelfi/reinforcement-learning-in-configurable-environments))

## Thesis

### Reinforcement Learning in Configurable Environments: and Information Theoretic Approach
Master's thesis
Politecnico di Milano, Computer Science and Engineering, December 2018
[Online](https://www.politesi.polimi.it/handle/10589/144736)

## Projects

### Learning To Run
Project for the Deep Learning Course @ Polimi.
Topics: Deep Learning, Reinforcement Learning.
<iframe width="560" height="315" src="https://www.youtube.com/embed/HVOrhxypOGg" frameborder="0" allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>

The project takes inspiration from the 2017 NIPS Competition: ([CrowdAI](https://www.crowdai.org/challenges/nips-2017-learning-to-run)).
In this competition, you are tasked with developing a controller to enable a physiologically-based human model to navigate a complex obstacle course as quickly as possible. You are provided with a human musculoskeletal model and a physics-based simulation environment where you can synthesize physically and physiologically accurate motion. Potential obstacles include external obstacles like steps, or a slippery floor, along with internal obstacles like muscle weakness or motor noise. You are scored based on the distance you travel through the obstacle course in a set amount of time.
The aim of the project is to study the problem and try to apply Deep Reinforcement Learning algorithms to replicate results of the top teams.

- [Github](https://github.com/MultiBeerBandits/learning-to-run)
- [Slides])(tobe)

### Computer Vision for Computer Art. A pencil writing on a virtual plane
Project for the Image Analysis and Computer Vision Course @ Polimi.
Topics: Image Analysis, Feature Extraction, Tracking, Camera Calibration, 3D reconstruction.

<iframe width="560" height="315" src="https://www.youtube.com/embed/U7XAzXeBx-U" frameborder="0" allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>

Wouldn't be great to write or draw on any surface, without the need of ink, and obtain the result in digitalized format? The task of this project is to develop an algorithm that, given a video of someone drawing using a pen without ink, recovers the 3D trajectory of the pencil tip.
Given that, it is possible to reconstruct the drawing, by simply keeping the part of the trajectory near the writing surface. 
The project is implemented in MATLAB.

- [Github](https://github.com/EmilianoGagliardiEmanueleGhelfi/inkless-painting)
- [Youtube](https://www.youtube.com/watch?v=U7XAzXeBx-U)

### Recommender System Challenge @ Polimi: Music Recommendation
I took part to the annual Kaggle competition on Recommender Systems held by Politecnico di Milano in 2017. That year topic was music recommendation, so we implemented and trained several Machine Learning algorithms to suggest songs to users based on their tastes.
We placed among the best teams in the competition and we were invited to present our approach and solutions to the recommendation problem[1].
We used Python, Numpy/Scipy, Jupyter Notebooks and C++ as technology tools to efficiently implement our ideas.

- [Slides](https://www.slideshare.net/EmanueleGhelfi/recommender-system-challenge)
- [Github](https://github.com/MultiBeerBandits/recsys\_challenge\_2017)

### CNN Quantization - Performance Evaluation
Project for the Advanced Computer Architecture Course @ Polimi.
Topics: Convolutional Neural Networks, Quantization, Performance, Cache, Tensorflow, Caffe. 
For real world application, convolutional neural network(CNN) model can take more than 100MB of space and can be computationally too expensive. Therefore, there are multiple methods to reduce this complexity in the state of art. Ristretto is a plug-in to Caffe framework that employs several model approximation methods. For this project, first a CNN model is trained for Cifar-10 dataset with Caffe, then Ristretto will be used to generate multiple approximated versions of the trained model using different schemes. The goal of this project is the comparison of the models in terms of execution performance, model size and cache efficiency in the test and inference phase. The same steps are done with Tensorflow and Quantisation tool. The quantisation schemes of Tensorflow and Ristretto are then compared.

- [Slides](https://www.slideshare.net/EmanueleGhelfi/cnn-quantization)
- [Github](https://github.com/EmilianoGagliardiEmanueleGhelfi/CNN-compression-performance)
