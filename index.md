# Discovering Control-Intensive State Regions With Deeper Policy Networks

<a href="https://github.com/ylajaaski/state_space_page/raw/gh-pages/StateSpaceFinalPaper.pdf">Click here to read our paper</a>

## Abstract

A key knowledge gap in deep reinforcement learning (DRL) is the role of depth in policy networks. While the conventional 2-layered fully-connected networks (FCNs) tend to work sufficiently well for most tasks, we hypothesize that additional layers contribute to the expressivity of FCN policies by introducing finer-grained mapping from the state space to actions. Our fine-tuning experiments isolate the effects of additional layers for a DRL agent deployed on a simple 1D toy car problem. Both qualitative and quantitative analyses are presented to examine the evolution of added layers as fine-tuning progresses. Our results indicate that deeper layers afford more granularity in state-action mappings to control-intensive regions in the state space.

## Environment

We examine a toy 1-dimensional car environment is a simple 1D line where the agent has a starting position at zero and the goal is located at 100. The agent can either accelerate or deaccelarate to reach the goal state from the starting position. 

![Screen-Recording-2022-05-18-at-1 36 22](https://user-images.githubusercontent.com/50364479/168923762-e985f555-eebb-4727-8686-fc28beda565b.gif)

## State Space Divisions of a 2x2 ReLU Policy Network (Teacher)

We examine states in a fixed window within the state space of the environment. For each state, we extract a binary embedding by binarizing and concatenating corresponding ReLU activations resulting from learned weights and biases. Visualizing the embeddings results in linear regions or "cells".

<!-- Here we have visualized the cell divisions and actions during the training for teacher which has a 2x2 policy. The figure below shows the evolution of the actions during the training. Yellow color represents acceleration while purple denotes deacceleration. In all of the visualizations, the trajectory of the car is shown as a black line. 
 -->
 
As an example, here is the visualization of a 2x2 networ's evolution as it goes through the iterations of PPO.
 
<img src="https://user-images.githubusercontent.com/50364479/171622561-cfa84caa-2e6b-46b1-ac3f-7291b7ab9dd9.gif" width="600">

The figure below shows the cell divisions of the agent during the training.

<img src="https://user-images.githubusercontent.com/50364479/171622575-b7ccef67-0981-43e4-b5e4-541222a3f699.gif" width="600">

The figure below visualizes the cell divisions of the last layer of the agent.

<img src="https://user-images.githubusercontent.com/50364479/171622838-d517b639-bcc0-45eb-a8f5-db98ab470bc6.gif" width="600">

### State Space Divisions of a 2x2x2x2 ReLU Policy Network (Student)

Next, we train a 2x2x2x2 student using the the teacher that was given as an example in the previous section. The actions during the training are visualized below. The first two layers are copied from the teacher and not optimized during the training.

<img src="https://user-images.githubusercontent.com/50364479/171622802-8d872a30-1d40-4a44-936d-c40017d0f68f.gif" width="600">

The figure below shows the cell divisions of the agent during the training.

<img src="https://user-images.githubusercontent.com/50364479/171622816-f781f7de-9507-4ac5-9531-ceb8d2c33e0a.gif" width="600">

The figure below visualizes the cell divisions of the last two layers of the agent.

<img src="https://user-images.githubusercontent.com/50364479/171622597-197b9e1b-338e-4252-9312-ff51f3483dc5.gif" width="600">


