---
layout: post
short_title: Deep Motion Planners
title: Neural Network-based Algorithms for Motion Planning
description: A CSE 571 Class Project to replicate the Motion Planning Networks paper.
icon: motionplanning_icon.png
github: https://github.com/NakuraMino/Deep-Motion-Planner
date: 2021-06-05
show_date: false
ready: true
---
![motion planning non-holonomic](/assets/images/projects/motionplanning.png){:class="blog-img"}

## Introduction

Existing path planning methods, such as A* and Rapidly-exploring Random Trees (RRT), are known to provide collision-free paths from a start state to a goal state. However such methods become computationally expensive in high dimensional planning spaces. Recent work in this area has shown neural networks to be a viable and computationally inexpensive alternative to such traditional motion planning methods. In this report, we explore neural network-based algorithms that imitate these path planning algorithms. Specifically, we present two neural network architectures and consider three neural network-based planning algorithms. We demonstrate the applications of these planning algorithms on a holonomic point robot in a grid world and on a car-like robot with non-holonomic constraints in a continuous 2D plane. We then evaluate these algorithms on a variety of maps and present the results.

## Final Report:
[Link](https://nakuramino.github.io/assets/pdf/CSE_571_Project_2_Final_Report.pdf)
