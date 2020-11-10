---
title: >-
  [Paper Reading] SurfaceFleet: Exploring Distributed Interactions Unbounded from Device, Application, User, and Time
date: 2020-11-03 21:45:27
tags: cross-device interaction; distributed systems; mobility; 
---

From UIST'20.

## Strengths

1. Not a novel idea, but it is complete enough. Device, app, user and time each have precedents, but this work put all of these into action simultaneously, for both tools and pieces of content, using just a few cross-device toolkit abstractions and interactions. 
2. Robust system architecture. Cloud services are userd in the system for building **resiliency** and transimitting resources.(Although I can’t fully understand the benefits, at least it looks great.)Moreover, this architecture is more suitable for "productivity tools" than the traditional TCP or UDP design.
3. The design of system components is simple and beautiful; the way of interaction is natural and simple. The design meets the current flat aesthetic. The simplest drag & drop is used for the interaction, and there is visual and animation feedback during the interaction (for example, dragging a ui out and putting it into its container will have visual effects).
4. Writing。The article mainly focuses on four dimensions. Whether it is related work, usage scenario design, system design, and component design, it is written in a sub-total structure around these four points, which makes it very clear and clear to read. In the usage scenario, how an ordinary company employee uses the system, and perfectly feedbacks the advantages in these four dimensions; every design of the system can be related to how to remove the bounds of the four dimensions; so even if there is no user experiment, it can convince reader that it can indeed improve efficiency.

## My comments

### Enlightenment

1. design the architecture as a cloud? so that our system can jump out of the simple "smart home" scenario, which is more suitable for a productivity tool.
2. They clearly stated that their contribution is at the UI level. How do we find the difference from them? Focus on "xr", focus on the interaction between the physical world and the electronic world. 
3. Knowledge work is not siloed within any single “sharing” or “messaging” app. Therefore, cross-APP is also an important feature as a "productivity tool". Web and web plugins seem to be a good choice

## What's this and Why

### Introduction

In this paper, they propose a distributed system and cross-device interaction toolkit named SurfaceFleet which employs lightweight, semi-transparent desktop applets to de-coupling UI elements and operations from particular four dimensions --- device, application, user and time.

Instead of sharing entire documents, they focus on supporting distributed user operations(tools, inputs, content and behaviors) that can be combined with or act upon documents.

### Reasons for intensive reading

1. the storytelling method is worth learning.
2. It has a high relevance to the work we are doing now and has a high degree of completion.

## Conception, Method and Implement

### Four dimensions : Device, Application, User and Time

The opinion of this paper is that user operations are largely bound to the current **device** -- runing the current **application**, for the current **user**, and at the current moment in **time**. So they design SurfaceFleet from there four dimensions.

The other are well understood except for the "time" dimension. This dimension can be explained as syschronous and asynchronous interactions. Once there is a deterministically replayable log of distrubuted state, application logic does not necessarily have to failover immediately. Finer-grained interactions can be left latent, to migrate or synchronize at a later time.

### System architecture and Implement method

The architecture seems to be derived from this article[<sup>1</sup>](#refer-anchor-1)


#### device unbound

Ambrosia (available via open source) uses declarative database techniques to persist data, providing virtual resiliency by capturing state changes in a deterministically replayable log. Achieved virtual resiliency of state changes。

Ambrosia utilizes a component known as CRA (open-source) [<sup>2</sup>](#refer-anchor-2) that virtualizes connection management. Achieved virtualization of inter-device connections。

At the network level. Both of these are good for cross-device.

For developers, adding the [Synchronizable] tag to the C# class, this content be transferred across devices?

#### App unbound

Semi-Transparent, Always-on-top Applets : always visible and always available as drag & drop targets, no matter the current application, web page, or file system window.

Multiple Formats in Clipboard ： The use of the windows clipboard formats can store multiple data formats so that the system can use the same mechanism to transfer different data across apps.

And also consider extending those programs that have not been modified, by accessing the program's COM API (Component Object Model). But for each program, this system need to write a COM interaces for processing this program.


#### time unbound

Since the state information is saved in the cloud log, when the update information is received, you can immediately, or at a later time, or even revisit past states, to cross the time dimension.

Currently using insert placeholders for content to "interaction promise"

COM API

#### About architecture

1. Each Applet in the SurfaceFleet system is an independent executable, with a cloud connection to log shared model updates in a robust and durable manner.
2. implemented in C# using the .NET Framework and Windows Presentation Foundation (WPF).
3. Major components: a shared model, robust logging of updates, OS, application-interop features

## Related work and Some note

## Reference

<div id="refer-anchor-1"></div>

- [1] Jonathan Goldstein, Ahmed Abdelhamid, Mike Barnett, Sebastian Burckhardt, Badrish Chandramouli, Darren Gehring, Niel Lebeck, Christopher Meiklejohn, Umar Farooq Minhas, Ryan Newton, Rahee Ghosh Peshawaria, Tal Zaccai and Irene Zhang, A.M.B.R.O.S.I.A: providing performant virtual resiliency for distributed applications. Proc. VLDB Endow., 2020. 13(5): p. 588–601. 10.14778/3377369.3377370.

<div id="refer-anchor-2"></div>

- [2] Ibrahim Sabek, Badrish Chandramouli and Umar Farooq Minhas. CRA: Enabling Data-Intensive Applications in Containerized Environments. in 2019 IEEE 35th International Conference on Data Engineering (ICDE). 2019. https://doi.org/10.1109/ICDE.2019.00192.



<div id="refer-anchor-3"></div>

- [Wikipedia](https://en.wikipedia.org/wiki/Main_Page)
