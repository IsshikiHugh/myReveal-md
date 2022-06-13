---
title: Nobrainer
separator: <!--s-->
verticalSeparator: <!--v-->
theme: league
highlightTheme: tomorrow-night-bright
revealOptions:
  width: 960
  height: 800
  margin: 0.04
  transition: 'convex'
  slideNumber: true
---

# Nobrainer
<font size="6"> 🧠 A robust and validated **neural network tool suite** for imagers</font>

<div align="right"><font size="6"> 👉 Given by Hrz & Xy </font></div>

<div align="right"><font size="6">

👉 Powered by [reveal.js](https://github.com/hakimel/reveal.js)

Note: Test note.

</font></div>

<!--s-->

# Information
<font size="8"> <font color="orange">**What**</font> is it? </font>

1. Introduction 
2. Blueprints & Plan

<!--v-->

## Introduction

<div align="left"><font color="grey" size="6">
With the increasing need for <font color="orange">efficient and robust software</font> offering insight across the diversity of population imaging efforts underway across the BRAIN Initiative and other projects, <font color="orange">Nobrainer</font> comes into our views together with its strong ability in greatly simplifying integrating deep learning into neuroimaging research. As a <font color="orange">data-analyzing Python library</font>, the Nobrainer leverages new learning technologies including  many advances in stastical learning which can address many research applications using the extensive and varied data being produced by the projects. The whole project is led by <font color="orange">Satrajit GhoshI from MIT</font>.
</font></div>

Note:
Nobrainer 的意义 ： 更高效 更可信  让神经影像学的研究更方便且准确

<!--v--> 

## Blueprints & Plans

<font size="6">

<div align="left">

Aim 1: Basis for follow-up works
- Neural network models
  - Robust & Pre-trained
  - Scanned from over 65000 individuals

</div><!-- .element: class="fragment" -->
<div align="left">

Aim 2: Custom Datasets 
- Working on private datasets
  - Bayesian neural network models
  - Detect fail on input 
  - Visualization

</div><!-- .element: class="fragment" -->
<div align="left">

Aim 3: Open Source Maintenance 
- Engineering problems (with the community)
  - Maintain the software infrastructure
  - Improve efficiency
  - Increase the scalability of our training methods

</div><!-- .element: class="fragment" -->

</font>

Note:
1. 提供神经网络模型
2. 实现对自定义数据集的适配
3. 开源维护
<!--s-->

# Follow-up
<font size="8"> <font color="orange">**Where**</font> is it now? </font>

1. Progress & Outcomes
2. Deficiency & Improvement

Note:
<!--v-->

## Progress & Outcomes

<u>01-August-2020</u> to <u>31-July-2023</u>

1. <b>A deep learning <font color="orange">toolbox</font> for automatic segmentation of subcortical limbic structures from MRI images</b> <!-- .element: class="fragment" -->
2. <font color="grey">Quantification of volumetric morphometry and optical property in the cortex of human cerebellum at micrometer resolution</font> <!-- .element: class="fragment" -->
3. <font color="grey">Mapping the subcortical connectivity of the human default mode network</font> <!-- .element: class="fragment" -->
4. <font color="grey">Scalable mapping of myelin and neuron density in the human brain with micrometer resolution</font> <!-- .element: class="fragment" -->

Note:

- 研究进程到了预计的三分之二 ，目前认为已达到了Aim2 与Aim 3 之间。
- 着重介绍 Tool box 和 subcortical mapping 两个研究
- 用于从 MRI 图像中自动分割皮层下边缘结构的深度学习工具箱

<!--v--><!--.element: data-background-image="https://pic.imgdb.cn/item/62a6feb40947543129af0d67.jpg" data-background-size="1000px"-->

<!--v--><!--.element: data-background-image="https://pic.imgdb.cn/item/62a6feb40947543129af0d45.png" data-background-size="1000px"-->

<!--v--><!--.element: data-background-image="https://pic.imgdb.cn/item/62a6feb40947543129af0d59.jpg" data-background-size="1000px"-->

<!--v-->

## Deficiency & Improvement

<div><font color="orange">Privacy</font>-preserving quality control problems</div> <!-- .element: class="fragment" -->
<font size="6">

<div>

Reasons may preclude analyses that pool data to a single site:

> - Privacy concerns for rare disease data
> - Institutional or IRB policies
> - Access to local computational
> - Storage resources
> - Download capabilities
> - ... 

</div><!-- .element: class="fragment" -->

<div align="left">

They thought using an average of the gradients weighted by the quality of the respective local <font color="orange">t-SNE</font><font size="4">(Laurens & Geoffrey, 2008)</font> <font color="orange">embeddings</font> might be an alternative solution to their decentralized setting, but it's not clear now.

</div><!-- .element: class="fragment"-->

</font>

Note:
### 问题：
1. 隐私数据的权限和政策问题
2. 额外的带宽和计算压力
3. 已有的基于可信站点的做法有一些弊端
### 解决方案：
1. 联邦式学习
2. 两种算法
3. t-SNE
<!--s-->

# Assessment
<font size="8"> <font color="orange"><b>Why</b></font> fund? </font>


1. Value
2. <s>only 1.</s>

<!--v--><!--.element: data-transition="fade" data-transition-speed="fast"-->

## Value

<div align="left">

- Unique aspects of this tool include
  - MB / Fx / Bf / SepN segmentation supported
  - Combination of limbic regions
  - Ease-to-use
  - Self-contained (but easy integration with FS)
  - Extensive testing

</div>

Note:
乳腺体、天穹、前脑、隔核
1. 工具出现时是唯一能做乳腺体分割的软件
2. 边缘区域组合
3. 易用
4. 独立性好（但是方便和 Free Suffer 一体）
5. 广泛的测试
<!--v--><!--.element: data-transition="fade" data-transition-speed="fast"-->

## Value

<div align="left">

- Significance
  - Significantly improve data analysis and model development efficiency
  - Share data more easily
  - Increase reusability of data through greater trust in model outputs

</div>

Note:
1. 增加数据分析和模型开发效率
2. 云友好的社区协作数据分享
3. 数据可复用性强
<!--s-->

# The end
Thanks for Listening