---
title: codex初探
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
date: 2026-07-27 19:24:35
description:
image:
---
最近Codex编辑器大火，也是跟风体验了一下。免费额度不够，token烧太快了⊙﹏⊙

<!-- more -->

### Codex的安装

使用codex当然科学上网是必不可少的，此处不多作介绍。使用代理即可从官网上下载安装软件，codex已经与openai整合了，因此去openai官网下载即可。

{% link openAI官网::https://openai.com/ %}

官方渠道下载的居然是Windows商店版本，至于桌面端的下载途径可能得去GitHub上找了。使用codex最大的麻烦主要来自于账号登陆后的手机验证，因为openai的防控措施很严格，像Google Voice这类的虚拟号码服务商是无法接收验证码的。

主流的解决方案就是使用接码平台或者使用外国的实体卡（Giffgaff等），我通过NexSMS进行验证，大概花个几块钱的样子。

{% link NexSMS::https://nexsms.net/ %}

但是这种途径能不能一劳永逸不得而知，也存在着账户封号的风险，有意者谨慎尝试。

### Codex的使用

在使用codex之前，我曾体验过腾讯的workbuddy。可以看出workbuddy算细粒度copy的codex，在一些文件组织上我并不喜欢。以下几点：
1. codex文件的组织基本放在C盘用户目录下面，而且再调用工具是往往会默认自己安装依赖（python，nodejs），其实我个人习惯是让他调用本地已经安装的环境。这样也可以避免少安装一些包。
2. codex会按照任务建立文件夹生成文件，尤其是一些简单的任务也会这样做，这样感觉复杂化了。
3.不知道是网络的原因还是其他，codex的反应速度比较慢。我用过的trae虽然排队，但基本排完队就能立马输出，思考时间比较短，而codex需要等待一段时间才能输出结果。

### 费用相关

codex的免费额度是远远不够的，在下午几个小时的使用中，一个月的免费额度很快就会被消耗完。贵是真的贵╮(╯-╰)╭ 并且在免费的版本下很多功能受限，甚至不能生成图。基本来说要用codex，那么plus版本是最低要求了。

对于轻度用户来说，用一个月拼车的plus的钱买deepseek的api可以用很久了。

OK！！ 言尽于此，目前还没体会到codex的强大，也不是性价比之选，也许深度使用后会找到非用不可的理由。
