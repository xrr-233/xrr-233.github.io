---
title: Escape Drill
excerpt: A simulated experiment to investigate human behavior during evacuation.
tags: [VR/AR, HCI, Unity]
thumbnail-img: /assets/img/2022-11-24-escape-drill-teaser.png
category: project
---

![](/assets/img/2022-11-24-escape-drill-teaser.png)

## Introduction

This project was in collaboration with Mr. Zhang Ming.

<span id="link"></span>
**Link:** [https://doi.org/10.1016/j.jobe.2023.106041](https://doi.org/10.1016/j.jobe.2023.106041)

As an important part of our project, we have set up a simulated environment using Unity Engine to record and analyze the collected experimental data in order to discover human behavior during evacuation. Due to some external assets in the project, the developed Unity project cannot be made public. Therefore, the content of the project will be explained here.

## Part O. UI

The user interface was developed in the last step to create the convenience of accessing the desired part of the experiment. Sprites, sounds and input form were included. Three modes are provided, which will be stated.

![](/assets/img/2022-11-24-8fe6dc6b0719bec4b7e7cc6398c7cb5.png)
*Fig. The form used to adjust the parameters of the scene*

## Part I. Experiment

![](/assets/img/2022-11-24-564f517f01e95184ec6fb8a6e332b9a.png)

In this scene, participant will conduct an escape drill following the crowd to the specified safe place. We use several external tools, including fire burning and explosion particle effects, population system with human avatar, animation controller and pre-defined route, the FirstPerson-AIO script to control the first-person perspective, as well as SteamVR SDK for displaying the scene in VR environment.

![](/assets/img/2022-11-24-330cd50d29769ea3de4133c0c5d62fb.png)

## Part II.Generation

![](/assets/img/2022-11-24-f478fe31abe53e6c972ae52dfb1f90e.png)

To figure out the efficiency of evacuation with respect to the placement of escape sign, we conducted the experiment and collected the movement trajectory as well as the facing direction (a set of coordinates and orientation information) of the participants by recording the sensing data of the VR device with given high frequency. 

With these data, by setting the visual range (a pyramidal range within a given distance) of human naked eyes, we can define the effectiveness of a sign by measuring the seen time and the seen area. The escape sign surface is gridded with the center as the origin of coordinate axis and the density is adjustable. The seen area is computed by the number of grids in the visual range without any obstacles.

We did a hierarchical judgement on the distance first to reduce the computation cost, then use Unity Engine ray-casting functions for detecting the collision, as well as calculation of included angle between the rays and the central Line of sight to determine the valid seen area. By the method provided, we can measure a sign's effectiveness. We also generated standard trajectory data files with anchored route by C++ scripts. To make the process more intuitive, we also developed visualization by utilizing line renderer. These data were also analyzed in depth using python scripts.

![](/assets/img/2022-11-24-cfc49c96f4485f11a97e2dfbcb26eed.png)

![](/assets/img/2022-11-24-2a83b563a745123ae724ed533e4bdbc.png)

## Part III.Visualization

![](/assets/img/2022-11-24-cda96579424b2351b28b98773e9c789.png)

Used to display intuitive performance of different teams. Videos can be retrieved on th [link provided](#link).