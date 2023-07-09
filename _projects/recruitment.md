---
layout: post
short_title: Recruitment Sankey Diagrams
title: Recruitment Sankey Diagrams
description: A visualization of how my recruitment process went. 
icon: sankey.png
github: https://github.com/NakuraMino/Recruitment_Sankey_Diagram
date: 2020-11-23
show_date: false
ready: true
---

![sankey-diagram](/assets/images/projects/sankey.png){:class="blog-img"}

## Introduction

This diagram show how my internship search for summer 2020 went. As the amount of rejection letters piled up, I started to wonder what my ratios were looking like. I also wanted a quick and dirty summary of my statistics, and I saw a lot of people make sankey diagrams of their recruitment processes, so I thought I would do the same. 

## Demo

Check out [here](https://nakuramino.github.io/Recruitment_Sankey_Diagram/) for an interactive version of the diagrams!

## How I coded this project

I made the Sankey Diagram using Google’s [visualization tool](https://developers.google.com/chart/interactive/docs/gallery/sankey). I kept track of all my applications in a csv file, and I parsed them using python. The results were compiled into a .txt file, and I used that to make my Sankey Diagram in javascript.
