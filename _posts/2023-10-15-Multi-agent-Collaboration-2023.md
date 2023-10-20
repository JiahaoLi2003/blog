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

## 🧐 Methods
- prompt structure consists of the following main components:
    - Task Description
    - Step History
    - Current State
    - Robot State & Capability
    - Agent Specialized Prompt
    - Communication Instruction
    - Plan Syntactic Checking Feedback

- Communication Frameworks for Sub-task Plan


    - Decentralized Multiagent System framework (DMAS)：去中心化多智能体系统框架,是之前关于LLMs as multi-agent planners 的工作中使用的frameworks.Each robot is assigned an LLM planner and another agent to whom it should send its comments. The agents use a turn-taking approach for dialogue.
    - Centralized Multi-agent System framework (CMAS)：中心化多智能体系统框架，这种方法仅包含一个 LLM 作为central planner，负责在每次planning iteration assigning actions for each robo.
    - Hybrid Multi-agent System-1(HMAS-1)：A central LLM planner proposes an initial set of actions for the current planning iteration that is provided to each of the robots’ LLM planners.然后LLMs和在DMAS中的运营方式相同。
    - Hybrid Multi-agent System-2(HMAS-2)：a central LLM planner generates an initial set of actions for each robot, as done in CMAS; however, each robot has an LLM agent that checks its assigned action and provides feedback to the central planner. In the case of a local agent disagreeing with its assigned action, the central agent will re-plan. This process repeats until each robot’s LLM agrees with its assigned action.


















