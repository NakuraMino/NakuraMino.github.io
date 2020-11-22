---
layout: page
title: Neural Network-based Algorithms for Motion Planning
date: 2020-06-12 1:31:00
description: Using Deep Learning to imitate traditional planning algorithms.
---

<center>
<img src='https://nakuramino.github.io/assets/img/motionplanning.JPG' width='100%'>
</center>

### Introduction

Existing path planning methods, such as A* and Rapidly-exploring Random Trees (RRT), are known to provide collision-free paths from a start state to a goal state. However such methods become computationally expensive in high dimensional planning spaces. [Recent work](https://arxiv.org/pdf/1806.05767.pdf) in this area has shown neural networks to be a viable and computationally inexpensive alternative to such traditional motion planning methods. In this report, we explore neural network-based algorithms that imitate these path planning algorithms. Specifically, we present two neural network architectures and consider three neural network-based planning algorithms. We demonstrate the applications of these planning algorithms on a holonomic point robot in a grid world and on a car-like robot with non-holonomic constraints in a continuous 2D plane. We then evaluate these algorithms on a variety of maps and present the results.

### Read the Final Report Here:

<a href='{{ site.baseurl }}/assets/pdf/CSE_571_Project_2_Final_Report.pdf'>Final Report</a>

### Github Link 

<a href='https://github.com/NakuraMino/CSE571-Project-2'>Github link</a>. Enjoy!