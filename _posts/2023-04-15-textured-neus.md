---
title: Textured-NeuS
excerpt: An extension of NeuS - when exporting the mesh, the color of the vertices will also be given
tags: [Reconstruction, Texture, NeRF, SDF]
# cover-img: /assets/img/2023-04-15-example.png
thumbnail-img: /assets/img/2023-04-15-example.png
category: project
---

![](/assets/img/2023-04-15-example.png)

Thanks for the great work by [@Totoro97](https://github.com/Totoro97). For the original work, please see [https://github.com/Totoro97/NeuS](https://github.com/Totoro97/NeuS).

<span id="link"></span>

## Project Link

[https://github.com/xrr-233/Textured-NeuS](https://github.com/xrr-233/Textured-NeuS)

## Origin of the project

In this project, joint method of NeRF, IDR and NeuS are used to reconstruct a 3D object. The original NeuS output is a plain model without texture, and it can only render the novel image with the trained model. However in downstream applications, the huge demand of 3D modeling costs large manpower, time and strengths. We must admit that in current stage computer graphics techniques cannot completely replace elaborately hand-crafted 3D models, especially for those with more complicated hierarchy (e.g. skeleton, clothes, MMD, metahumans). But within tolerated accuracy, reconstruction effect is actually enough for related applications and has significant potential in certain industries including game industries and daily life (including video making using C4D).

3D modeling is a very tough work in 3DMax and Maya, requiring one to fully master the usage of the functions in the software. But for general public, they usually have no time and cost digging into the learning of the software, keeping the modeling work isolated from daily life. Therefore, this project is developed to solve this problem.

## Nature of the project

This project is a undergraduate final year project, trying to find a method of generating 3D models automatically with low-cost publicly owned device, namely, mobile phones. Newer version of iPhone support using LiDAR to scan the surrounding environment, but with poor quality in empirical use. Also, in downstream industries, mesh objects, instead of point cloud objects, are largely used in applications. The successful representation methods in the work of NeRF provide us with a new view to settle down MVS construction problem -- using rays to optimize the networks. Combined NeRF ray representation with SDF representation, NeuS simultaneously maintain four networks to generate the scene objects.

For further details, please check the [link provided](#link).