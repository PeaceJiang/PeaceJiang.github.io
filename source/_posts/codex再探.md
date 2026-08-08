---
title: codex再探
categories: 
  - 计算机
  - Codex
tags: [Vibe Coding, Codex]
sidebar:
  - blogger
  - toc
copyright:
  type: type1
  author: null
  ref: null
  title: null
  url: null
date: 2026-08-03 14:54:34
description:
image:
---

用codex做了点具体的任务，再谈谈codex的使用体验(●'◡'●)

<!-- more -->

### 任务来源

矿区的区域预测需要根据众多数据源进行特征提取，训练，最终得到预测结果。本研究确定好研究区，做好化探、物探、地质、遥感数据的预处理，通过codex实现预测。

### 执行过程

首先将预处理的文件整理整专门的文件夹中，以便于读取梳理。每一类数据已单独的文件夹存放，同时在每个文件夹中都有一个说明文档，用于说明该文件夹中的文件内容以用于后续的分析。

1. 第一步自行建立处理文档，将数据的预处理过程、目标要求、注意事项都写在文档中。使用codex读取文档，并要求它生成一个项目计划报告。

2. 通过codex生成的项目计划报告，进行审阅，修正不合理的要求或者新增要求。注意codex需要调用的skills和mcp等外置插件。

3. 根据修正后的项目计划报告，开始执行项目。此时的codex会根据计划报告中的要求，自动执行项目。
{% Image https://pic1.imgdb.cn/i/0342D5L7mYniYWzrPz2sWx.png 任务截图 download:false %}
上图看出，codex执行流程十分复杂，调用的子任务很多，同时也比较消耗token。

### 执行结果

codex的运行结果可以说是无敌了{% emoji aru aru0340 height:1.75em %}
它除了能输出指定格式的文件外，还能输出项目的报告。在没有强行规定字数的情况下，它应该输出5000字左右的报告。

在前面的项目要求中可以约束输出报告的提纲、文字字体、图片内的文字要求等等。报告中的图片可以调用较好的skills来进行制图，报告结果位docx文档，排版合适。表格与文字排版符合要求，但有些多余的格式需要手动调整。

{% Image https://pic1.imgdb.cn/i/0342E56h3NMla6kJy9is2N.png 报告总览 download:false %}

比起Deep Seek，codex的报告生成能力要强得多。果然贵有贵的好处。如果DeepSeek 4 Pro 能够新增多模态并在执行任务中形成如此完善的报告，相信也具有很强的吸引力。{% emoji tieba huaji height:1.75em %}
