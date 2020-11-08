---
title: >-
  [Paper Reading] SurfaceFleet: Exploring Distributed Interactions Unbounded
  from Device, Application, User, and Time
date: 2020-11-03 21:45:27
tags: cross-device interaction; distributed systems; mobility; 
---

From UIST'20.

Article: 文献出处（方便再次搜索）
Data: 文献数据（总结归纳，方便理解）
Comments: 对文献的想法 （强迫自己思考，结合自己的学科）
Why: 为什么看这篇文献 （方便再次搜索）; 为什么精读这篇文献，为什么做文献笔记？了解课题背景/用于实验设计/用于写作模仿
Summary: 文献方向归纳 （方便分类管理）。可以是文献关键词的结合，也可以是你对文献方向的总结。精简！精简！

DATA
这篇文章的目的
结论
背景介绍
结果
方法（可选）

## What's this and Why

### Introduction

In this paper, they propose a distributed system and cross-device interaction toolkit named SurfaceFleet which employs lightweight, semi-transparent desktop applets to de-coupling UI elements and operations from particular four dimensions --- device, application, user and time.

Instead of sharing entire documents, they focus on supporting distributed user operations(tools, inputs, content and behaviors) that can be combined with or act upon documents.

### Reasons for intensive reading

1. the storytelling method is worth learning.
2. It has a high relevance to the work we are doing and has a high degree of completion.

## Conception, Method and Implement

### Four dimensions : Device, Application, User and Time

The opinion of this paper is that user operations are largely bound to the current **device** -- runing the current **application**, for the current **user**, and at the current moment in **time**. So they design SurfaceFleet from there four dimensions.

The other are well understood except for the "time" dimension. This dimension can be explained as syschronous and asynchronous interactions. Once there is a deterministically replayable log of distrubuted state, application logic does not necessarily have to failover immediately. Finer-grained interactions can be left latent, to migrate or synchronize at a later time.

#### Usage Scenario

To give a more concrete impression of how SurfaceFleet looks and feels, this paper use a office workflow to show how Applets combine.

### System architecture

The architecture seems to be derived from this article[<sup>1</sup>](#refer-anchor-1)

## Related work and Some note

## Reference

<div id="refer-anchor-1"></div>

- [1] Jonathan Goldstein, Ahmed Abdelhamid, Mike Barnett, Sebastian Burckhardt, Badrish Chandramouli, Darren Gehring, Niel Lebeck, Christopher Meiklejohn, Umar Farooq Minhas, Ryan Newton, Rahee Ghosh Peshawaria, Tal Zaccai and Irene Zhang, A.M.B.R.O.S.I.A: providing performant virtual resiliency for distributed applications. Proc. VLDB Endow., 2020. 13(5): p. 588–601. 10.14778/3377369.3377370.

<div id="refer-anchor-2"></div>

- [2] [Wikipedia](https://en.wikipedia.org/wiki/Main_Page)
