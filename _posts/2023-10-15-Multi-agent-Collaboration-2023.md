---
layout:     post
title:      Multi-agent-Collaboration			# 标题 
subtitle:   Centralized or Decentralized Systems   #副标题
date:       2023-10-15 				# 时间
author:     JiahaoLi 						# 作者
header-img: img/bolg-background.jpg 	#这篇文章标题背景图片
catalog: true 						# 是否归档
tags:								#标签
    - Multi-Agent
    - Collaboration   
---

## 📖 Abstract

文章主要研究了利用LLMs作为multi-agent的task planners.比较了四种多智能体通信框架（集中式、分散式和两种混合式）的任务成功率和令牌效率，应用于四个依赖于协调的多智能体 2D 任务场景（智能体数量不断增加），发现混合框架在所有四项任务中实现了更好的任务成功率，并且可以更好地扩展到更多agent。
过去的研究证明通过初始提示技术（例如，上下文学习、思维链）还是通过反馈进行迭代重新提示（例如，环境状态变化、检测到的错误），planning绩效都得到显着提高。但可能的coordinating action的数量和可能的action相互依赖性都随着agent的数量呈指数增长，使得语言模型的推理变得更加困难。同时，不同agent的response也要在每一轮反馈给LLM，context token length的limit也是需要考虑的，较长的promt可能会使得直接相关的context被淡化。
文章提出了四种cooperative dialogue frameworks来保证LLMs对multi-agent planning的通用性，同时应对agents数量增加的挑战。

