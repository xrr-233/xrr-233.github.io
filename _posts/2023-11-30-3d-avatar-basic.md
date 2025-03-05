---
title: Rendering Real-world 3D Avatar with Focus on Hair and Skin
excerpt: Exploration of physically-based human 3D Avatar rendering.
tags: [Unity, Rendering, Reconstruction]
thumbnail-img: /assets/img/2023-11-30-3d-avatar.webp
category: project
mathjax: true
---

![](/assets/img/2023-11-30-3d-avatar.webp)



**Note:** *Code will be public at [https://github.com/xrr-233/URP-Pass-Shader](https://github.com/xrr-233/URP-Pass-Shader) after solving copyright problem.*

A project that captures the figure of real person and creates the digital 3D avatar with specific rendering techniques. Developed by Unity URP+ShaderLab+HLSL. Based on in-depth understanding of Unity PBR-BRDF rendering scheme and popular hair rendering methods (Kajiya-Kay, Marschner, Scheuermann).

![](/assets/img/2023-11-30-workflow.png)
*Fig. 1 The workflow of the project. The person here is my teammate GZY, who is responsible for finding 3D avatar reconstruction methods. Tribute to him!*

During the process of the project, we have solved/alleviated the problem of aliasing effect due to alpha test, double-sided rendering, transparency, blending and rendering order issues.

![](/assets/img/2023-11-30-ppt-notes.png)
*Fig. 2 General Hair Rendering Scheme.*

## Some Formulas

+ PBR Reflectance Equation

$$
L_{o}(p, \omega_{o})=\int_{\Omega}f_{BRDF}(p,\omega_{i},\omega_{o})L_{i}(p,\omega_{i})(\omega_{i}\cdot n)d\omega_{i},
$$

+ Definition of BRDF (Bidirectional Reflectance Distribution Function) 

$$
f_{BRDF}=k_{d}f_{lambert}+k_{s}f_{cook-torrace},
$$
$$
f_{lambert}=\frac{c}{\pi}
$$
$$
f_{cook-torrace}=\frac{DGF}{4(\omega_{i}\cdot N)(\omega_{o}\cdot N)}
$$

+ Commonly used Normal **D**istribution, **G**eometry, and **F**resnel Term

$$
D_{Trowbridge-Reitz GGX}=\frac{\alpha^{2}}{\pi((N\cdot H)^{2}(\alpha^{2}-1)+1)^2},
$$
$$
G_{Smith GGX}=\frac{1}{((N\cdot L)(1-k)+k)((N\cdot V)(1-k)+k)}, 
$$
$$
F_{Schlick}=F_{0}+(1-F_{0})(1-(H\cdot V))^{5},
$$

+ Unity-optimized G·F approximation

$$
(G\cdot F)_{approx}=\frac{1}{(L\cdot H)^2(\alpha+0.5)} [23].
$$

+ Unity-optimized Cook-Torrace Specular Formula

$$
f_{unity}=\frac{\alpha^{2}}{\pi((N\cdot H)^{2}(\alpha^{2}-1)+1)^2(L\cdot H)^2(4\alpha+2)}.
$$

## Potential Improvement Directions

More automated hair generation algorithms (mapping hair strands into facets/generating opacity maps/...), integrate animation and rigging with FACS, more advanced skin/hair shading models (d’Eon/Double Cylinder/...)

## References

#### - PBR Theoretic Background

- [https://nedmakesgames.medium.com/mapping-our-way-to-pbr-writing-unity-urp-shaders-with-code-part-4-6c4ae9875529](https://nedmakesgames.medium.com/mapping-our-way-to-pbr-writing-unity-urp-shaders-with-code-part-4-6c4ae9875529)
- [https://learnopengl-cn.github.io/07%20PBR/01%20Theory/](https://learnopengl-cn.github.io/07 PBR/01 Theory/) / https://learnopengl.com/PBR/Theory
- 如何在Unity中造一个PBR Shader轮子 [https://zhuanlan.zhihu.com/p/68025039](https://zhuanlan.zhihu.com/p/68025039)
- 【Unity】URP Lit源码与PBR渲染公式超详细对照拆解 [https://zhuanlan.zhihu.com/p/635585362](https://zhuanlan.zhihu.com/p/635585362)
- 练习项目(十三)：简单地实现PBR [https://zhuanlan.zhihu.com/p/353705469](https://zhuanlan.zhihu.com/p/353705469)
- 【基于物理的渲染（PBR）白皮书】（五）几何函数相关总结 [https://zhuanlan.zhihu.com/p/81708753](https://zhuanlan.zhihu.com/p/81708753)

#### - Hair Transparency / Depth Issues

- Unity - Manual: ShaderLab: Culling & Depth Testing [https://docs.unity3d.com/2019.1/Documentation/Manual/SL-CullAndDepth.html](https://docs.unity3d.com/2019.1/Documentation/Manual/SL-CullAndDepth.html)
- 百人计划3.5Early-z与Z-Prepass [https://zhuanlan.zhihu.com/p/490138542](https://zhuanlan.zhihu.com/p/490138542)
- UnityShader中的透明渲染 [https://zhuanlan.zhihu.com/p/416887453](https://zhuanlan.zhihu.com/p/416887453)
- 深入URP之Shader篇4: Depth Only Pass [https://juejin.cn/post/7102741336621023262](https://juejin.cn/post/7102741336621023262)
- Order-Independent Transparency – nvidia [https://developer.download.nvidia.com/assets/gamedev/docs/OrderIndependentTransparency.pdf](https://developer.download.nvidia.com/assets/gamedev/docs/OrderIndependentTransparency.pdf)
- Order independent transparency (Depth peeling) [https://www.youtube.com/watch?v=a9ZUzu6sII0](https://www.youtube.com/watch?v=a9ZUzu6sII0)
- Weighted Blended OIT Sample [https://docs.nvidia.com/gameworks/content/gameworkslibrary/graphicssamples/opengl_samples/weightedblendedoitsample.htm](https://docs.nvidia.com/gameworks/content/gameworkslibrary/graphicssamples/opengl_samples/weightedblendedoitsample.htm)
- Unity - Manual: Cameras and depth textures [https://docs.unity3d.com/Manual/SL-CameraDepthTexture.html](https://docs.unity3d.com/Manual/SL-CameraDepthTexture.html)
- Order-independent transparency – wiki [https://en.wikipedia.org/wiki/Order-independent_transparency](https://en.wikipedia.org/wiki/Order-independent_transparency)
- This is called Order Independent Transparency, or OIT [https://bgolus.medium.com/this-is-called-order-independent-transparency-or-oit-f633411a5d2a](https://bgolus.medium.com/this-is-called-order-independent-transparency-or-oit-f633411a5d2a)
- 头发渲染的前世今生：如何在游戏中拥有一头迷人秀发？ [https://zhuanlan.zhihu.com/p/330259306](https://zhuanlan.zhihu.com/p/330259306)
- 深入剖析GPU Early Z优化 [https://zhuanlan.zhihu.com/p/53092784](https://zhuanlan.zhihu.com/p/53092784)

#### - Hair Rendering

- 图形学基础/各项异性与头发渲染 [https://blog.csdn.net/qjh5606/article/details/118117176](https://blog.csdn.net/qjh5606/article/details/118117176)
- 【Shader】URP人物渲染-头发篇 [https://zhuanlan.zhihu.com/p/659654525](https://zhuanlan.zhihu.com/p/659654525)
- Unity人物渲染篇-Scheuermann模型头发渲染 [https://zhuanlan.zhihu.com/p/654763033](https://zhuanlan.zhihu.com/p/654763033)
- Unity URP Hair Shader for hair cards [https://www.youtube.com/watch?v=EmU62lWMhSU](https://www.youtube.com/watch?v=EmU62lWMhSU)
- Anisotropic Rendering (2) Kajiya Kay Hair Rendering [https://zhuanlan.zhihu.com/p/363829203](https://zhuanlan.zhihu.com/p/363829203)
- 关于头发光照模型的介绍 [https://www.cnblogs.com/chatbot/p/16146522.html](https://www.cnblogs.com/chatbot/p/16146522.html)
- 基于Kajiya-Kay模型的毛发渲染 [https://zhuanlan.zhihu.com/p/135910659](https://zhuanlan.zhihu.com/p/135910659)
- Rendering Realistic Human Hair [https://jacob-lopez.github.io/SairHimulator/report.html](https://jacob-lopez.github.io/SairHimulator/report.html)
- Hair Rendering [https://andrew-pham.blog/2019/09/13/hair-rendering/](https://andrew-pham.blog/2019/09/13/hair-rendering/)
- [https://web.engr.oregonstate.edu/~mjb/cs557/Projects/Papers/HairRendering.pdf](https://web.engr.oregonstate.edu/~mjb/cs557/Projects/Papers/HairRendering.pdf)

#### - Code Reference

- building-quality-shaders-unity [https://github.com/Apress/building-quality-shaders-unity](https://github.com/Apress/building-quality-shaders-unity)
- Ned Makes Games [https://www.youtube.com/@NedMakesGames](https://www.youtube.com/@NedMakesGames)
- StarRailNPRShader [https://github.com/stalomeow/StarRailNPRShader](https://github.com/stalomeow/StarRailNPRShader)
- Next-Generation-Character-Rendering [https://github.com/Go1c/Next-Generation-Character-Rendering/tree/main](https://github.com/Go1c/Next-Generation-Character-Rendering/tree/main)
- Unity-URP-Hair-Shader [https://github.com/itsFulcrum/Unity-URP-Hair-Shader](https://github.com/itsFulcrum/Unity-URP-Hair-Shader)