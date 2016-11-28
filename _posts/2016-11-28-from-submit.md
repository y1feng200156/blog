---
layout: post
title: "在 form 表单内无法用 JS 提交表单"
description: "有时在 form 表单内无法用 JS 提交表单，接下来看下原因。"
og_image: "documentation/sample-image.jpg"
tags: [jquery]
---

## 现象

　　在使用 JS or jQuery 提交表单时，表单内含有 `id="submit"` 或者 `name="submit"` 元素时，使用 `$('form').submit()` 提交表单时，表单没有工作。

　　这时使用 `document.form.submit()`，浏览器出现 `Uncaught Type Error: document.getElementById(...).submit is not a function` 错误。

## 解决办法

　　在表单内不能出现 `id="submit"` 或 `name="submit"` 的元素。