---
title: "CSS之float布局"
date: 2019-11-24T12:07:00+08:00
draft: false
---

# Float 布局简介

**Float 布局是一种经典的布局方式，对 IE 浏览器可以做到很好的兼容，在兼容 IE6/7 时，首选 Float 布局**

# Float 布局的步骤

1. 子元素上加 float:left/right
2. 在父元素上加 class=“clearfix” **(重要)**

```CSS
.clearfix::after{
        content:"";
        display:block;
        clear:both;
}
```

# Float 布局的经验

1. 留一些空间或最后一个不设 width
2. 无需考虑响应式(IE6/7 不存在移动端)
3. IE6/7 存在双倍 margin 的 bug，解决方式有两种:
   1. 将错就错，针对 IE6/7 把 margin 减半
   2. 加上 display:inline-block

# Float 不同布局

- float 两栏布局:用于顶部条
- float 三栏布局:用于内容区
- float 四栏布局:导航条
- float 平均布局:产品展示区

# 在 Float 布局过程中的注意事项

1.  如果发现图片下有多余的东西，则在图片的 CSS 属性中加 vertical-align:top/middle
2.  border 因为会占据像素可能会对布局产生干扰，可以改用 outline
3.  有 width 的块级元素水平居中的方式
    ```CSS
    .item{
        margin-left:auto;
        margin-right:auto;
    }
    ```
4.  Q:在平均布局中如何解决最后一个元素被顶下去的问题？

    A:在平均框的父元素上加 div，div 的样式为 margin-right:- (一个空隙的大小)px

# Float 布局的例子

[一个简单的 Float 布局](http://js.jirengu.com/hanut/1/edit?output)
