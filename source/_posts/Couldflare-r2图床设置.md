---
title: Couldflare r2图床设置
categories: 
  - 博客设置
tags: [博客设置, 图床设定]
sidebar:
  - blogger
  - toc
copyright:
  type: type1
  author: null
  ref: null
  title: null
  url: null
date: 2026-08-19 15:45:29
description:
image:
---

对于静态网站来说，主要的维护成本主要源于域名和图床。域名每个月都比较便宜，但是图床就不见得了。图床即存储博客中的图片让他们能在公网中访问。本文介绍使用cloudflare r2来设置图床。

<!-- more -->

{% note info::在本篇文章之前图片的图床并非由cloudflare r2来存储 %}

## 前置准备

要想使用cloudflare r2的免费套餐需要使用PayPal账号来下单，其实PayPal并不难，它在大陆网络可以正常使用，只是安装包需要从谷歌商店下载。注意在使用PayPal时尽量不要使用科学上网工具。在PayPal中绑定一张废弃的银行卡即可正常使用。

## 订阅cloudflare r2

在cloudflare r2的主页中，选择r2订阅，通过PayPal账号下单后即可进入以下页面：
{% Image https://pub-ce7b6c77079a495b9bed89b22efe5e2a.r2.dev/2026/08/178ecdb325681af98f10141fee07b00d.png cloudflare r2界面 fancybox:true %}

随后自行创建存储桶，存储桶的名称可以自己定义，但是建议使用英文。点击新建的存储桶进入设置。最关键的使用自定义域还是通过公共开发 URL（r2.dev）方式实现。

自定义域时相对比较安全的方式。如果要对图床设定自定义域名，需要在cloudflare中托管域名。对于大陆互联网来说使用cloudflare来托管域名解析可能会导致网站访问速度变慢（具体我没测试过）。因此本文介绍相对简单的使用公共开发域名来实现图床的访问，
在设置总仅需在打开公共开发url即可。

更详细的自定义域配置可以参考教程：
[Cloudflare R2 白嫖指南：10G存储+免流量费，打造免费图床](https://zhuanlan.zhihu.com/p/1899044076168394425)

## 配置PicGo

PicGo时一个简单的图片上传工具，通过配置图床将图片上传到cloudflare r2中。
{% link PicGO下载页面::https://github.com/Molunerfinn/PicGo/releases %}

进入PicGo主页，在插件中搜索s3插件点击安装即可。
{% Image https://pub-ce7b6c77079a495b9bed89b22efe5e2a.r2.dev/2026/08/f6d914d73dc63ce4f11eca285b1f56c7.png PicGo插件页面 fancybox:true %}

回到图床列表，选择Amazon S3新建配置，配置名自定义即可。在配置中需要填写以下内容：
{% Checkbox checked:true 应用密钥 ID：填入 Access Key ID %}

{% Checkbox checked:true 应用密钥：填入 Secret Access Key %}

{% Checkbox checked:true 桶 (Bucket)：填入你的存储桶名称 %}

{% Checkbox checked:true 自定义节点 (Endpoint)：填入 https://<你的账户ID>.r2.cloudflarestorage.com %}
账户ID页面可以在R2主页中的右下角的账户详情看到：
{% Image https://pub-ce7b6c77079a495b9bed89b22efe5e2a.r2.dev/2026/08/fa3976e95d12b28a3ecc58f3f1f26713.png 账户ID位置 fancybox:true %}

{% Checkbox checked:true 地区 (Region)：留空或填 auto %}

{% Checkbox checked:true 自定义输出 URL 模板：填入 公共开发URL/{path} %}
公共开发在设置页面中找到：
{% Image https://pub-ce7b6c77079a495b9bed89b22efe5e2a.r2.dev/2026/08/bcc8213838ca36086e8c3e41b27ef9c8.png 公共开发URL fancybox:true %}

设置完成后，可以测试以下上传是否正常。有时候好像在上传cloudflare的时候会报错有可能是因为网络问题。多尝试几次即可。


