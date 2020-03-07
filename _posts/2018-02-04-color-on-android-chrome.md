---
layout: post
title: 网站移动端定制颜色

---

在Chrome39之后的版本中，可以定制一个网页显示时appbar和statusbar的颜色。实现方法很简单。

以typecho为例，找到`header.php`，找到`<head>`标签，在下面添加：

    <meta name="theme-color" content="#0c59a0">

将#0c59a0替换为自己需要的颜色。一般来说颜色会选择跟网站的主题色一样，简单的办法就是通过网站的CSS文件找到那个颜色，填入就好了。