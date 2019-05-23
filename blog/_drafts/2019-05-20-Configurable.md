---
author: "manughelfi"
layout: post
title:  "Reinforcement Learning in Configurable Continuous Environments"
slug:  RL in Conf-MDP
date:   2019-05-22 8:00:00
categories: machine-learning
tags: machine-learning, reinforcement-learning
description: "RL in Configurable Continuous Environments"
---
Most of the problems tackled by Reinforcement Learning are typically modeled as Markov Decision Processes in which the environment is considered a **fixed** entity and cannot be controlled. Nevertheless, there exist several real-world examples in which a **partial control** on the environment can be exercised by the agent itself or by an external **supervisor**. For instance, in a car race the driver can set up his/her vehicle to better suit his/her needs. With the phrase **environment configuration** we refer to the activity of altering some environmental parameters to improve the performance of the agent’s policy. This scenario has been recently formalized as a **Configurable Markov Decision Process** (**CMDP**).
Formula One engineers have to configure their cars (e.g. wings, tyres, engine, brakes) to minimize lap time. In industry, machines have to be configured to maximize the production rate. These are cases in which the goal of the configuration is to improve performance, however in the case of car race it is possible for the supervisor to improve the learning speed of the pilot by presenting tracks of different difficulty.

<center>
<img src="/blog/figs/remps/conf-env.jpg" style="width: 50%; float: left;" alt="Figure 1 - REMPS">
<img src="/blog/figs/remps/conf-env2.png" style="width: 50%; float: left;" alt="Figure 2 - REMPS">
</center>

In our paper "Reinforcement Learning in Continuous Configurable Environments", accepted at ICML 2019, we propose a trust-region method, **Relative Entropy Model Policy Search** (**REMPS**), able to learn both the policy and the MDP configuration in continuous domains without requiring the knowledge of the true model of the environment.

## Optimization and Projection
Relative Entropy Model Policy Search (REMPS), imports several ideas from the classic REPS (Peters et al., 2010); in particular, the use of a constraint to ensure that the resulting new stationary distribution is sufficiently close to the current one. REMPS consists of two subsequent phases: optimization and projection. 
In the optimization phase we look for the stationary distribution that optimizes the performance. This search is limited to the space of distributions that are not too dissimilar from the current stationary distribution. The notion of dissimilarity is formalized in terms of a threshold κ > 0 on the KL-divergence.
The resulting distribution may not fall within the space of the representable stationary distributions given our parametrization. Therefore, similarly to Daniel et al. (2012), in the projection phase we need to retrieve a policy and a configuration inducing a stationary distribution as close as possible to the optimized distribution

## Model Approximation

## Results