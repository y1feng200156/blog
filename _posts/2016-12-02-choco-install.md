---
layout: post
title: "安装 chocolatey 出现的问题"
description: "安装 chocolatey 出现‘因为在此系统中禁止执行脚本’错误。"
og_image: "documentation/sample-image.jpg"
tags: [system]
---

　　看见一个 windows 下类似 brew 管理的工具，不过这个工具开源版本是有限制，比如自定义安装目录，就只有收费的版本才有。具体不同版本之间的对比可以到官方[这里](https://chocolatey.org/pricing)去查看。

## 安装 chocolatey

　　[官方](https://chocolatey.org/install)有教程教如何安装，都挺简单的，只是在安装过程中出现了一个问题，所有的脚本执行要在 system 权限下。我使用的是第三个脚本方式安装，如下：

PowerShell v3+ (Ensure Get-ExecutionPolicy is at least RemoteSigned)

{% highlight shell %}
iwr https://chocolatey.org/install.ps1 -UseBasicParsing | iex
{% endhighlight %}

　　执行后出现以下错：

{% highlight shell %}
无法加载文件 ******.ps1，因为在此系统中禁止执行脚本。有关详细信息，请参阅 "get-help about_signing"。 
所在位置 行:1 字符: 17 
+ E:\Test\test.ps1 <<<< 
    + CategoryInfo          : NotSpecified: (:) [], PSSecurityException 
    + FullyQualifiedErrorId : RuntimeException
{% endhighlight %}

　　这个问题其实在网上已经有了解决方案，[这个博客](http://www.cnblogs.com/zhaozhan/archive/2012/06/01/2529384.html)已经提供了解决方案。下面就记录下最终解决方案。

　　在 PowerShell 中执行 `set-ExecutionPolicy RemoteSigned`，再执行开始安装 chocolatey 的脚本，就能安装成功了。