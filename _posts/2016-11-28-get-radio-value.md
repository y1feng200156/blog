---
layout: post
title: "正确的 jQuery 获取 radio 选中值的写法"
description: "如何正确的获取 radio 的值。"
og_image: "documentation/sample-image.jpg"
tags: [jquery]
---

先看下面一段代码

{% highlight html %}
<label><input type="radio" name="radio" value="1" checked="true" /> raio1</label>
<label><input type="radio" name="radio" value="2" /> radio2 </label>
<label><input type="radio" name="radio" value="3" /> radio3 </label>
<input type="button" value="ok" onclick="doChecked()"/>

<script language="JavaScript">
function doChecked(){
  alert($(":radio[checked]").val());
}
</script>
{% endhighlight %}

网上流行的说法就是

{% highlight JavaScript %}
$(":radio[checked]").val()
{% endhighlight %}

能取到选中项的 `value`，但通过测试后发现，只有 IE 下有效，在 FireFox 与 Chrome 中不论选中哪一项，或不选，取到的值都是第一项的 `value`。

## 正解

{% highlight javaScript%}
$(":radio:checked").val()
{% endhighlight %}

## 扩展

同样这种写法也可以用于 `checkbox` 上。