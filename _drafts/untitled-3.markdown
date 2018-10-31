---
layout: post
title: "(Untitled)"
---

### 1：Does setting margin-top and margin-bottom have an affect on an inline element?

```
A： Yes   B：No
```

```
答案：B
```


##### 翻译
设置margin-top和margin-bottom属性，会对内联元素产生影响吗？
##### 解析：
margin也能用于内联元素，这是规范所允许的，但是margin-top和margin-bottom对内联元素（对行）的高度没有影响，并且由于边界效果(margin效果)是透明的，他也没有任何的视觉影响。这是因为边界应用于内联元素时不改变元素的行高度，如果你要改变内联元素的行高即类似文本的行间距，那么你只能使用这三个属性：line-height，fong-size，vertical-align。

##### 引用：
[一篇文章了解HTML文档流(normal flow)](https://zhuanlan.zhihu.com/p/31261020)
[细究内联元素（你一定不知道的东西）](https://zhuanlan.zhihu.com/p/31645001)