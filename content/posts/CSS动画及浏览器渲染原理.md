---
title: "CSS动画及浏览器渲染原理"
date: 2019-11-27T18:41:55+08:00
draft: false
---

# 浏览器的渲染原理

1.  浏览器的渲染过程：

    1. 根据 HTML 建立 HTML 树(DOM)
    2. 根据 CSS 建立 CSS 树(CSSOM)
    3. 将两课树合并成一颗渲染树
    4. Layout 布局(文档流，盒模型，计算大小和位置)
    5. paint 绘制(把边框颜色，文字颜色，阴影等画出来)
    6. compose 合成(根据层叠关系展示画面)


        ![](../../images/29.png)

2.  三种更新方式:

    1.  JavaScript --> Style --> Layout --> Paint --> composite

        例:div.remove()会使当前元素消失，其他元素 relayout

    2.  JavaScript --> Style --> Paint --> composite

        例:改变 background，直接 repaint + composite

    3.  JavaScript --> Style --> composite

        例:改变 transform，只需 composite

# CSS 动画优化

CSS 动画优化的方式有很多，本文主要讲解两个方面，如果您想了解完全可以参考该[链接](https://developers.google.com/web/fundamentals/performance/rendering/stick-to-compositor-only-properties-and-manage-layer-count)

1.  Js 优化:

    使用 requestAnimationFrame 代替 SetInterVal 和 setTimeOut

2.  CSS 优化:

    使用 will-change 或 translate

# transform 的简单功能介绍

**transform 属性用于旋转，缩放，倾斜或平移给定元素**

1.  translate:用于给定元素位移(属性值可以是百分数或者长度)

    1.  translateX() 在 X 方向的位移
    2.  translateY() 在 Y 方向的位移
    3.  translate( , ) 在(X,Y)上的位移
    4.  translateZ() 距离视点的位移

        **在使用 translateZ 时，需要对父元素加 perspective**

        ```HTML
        <div id="father">
            <div id="demo"></div>
        </div>
        ```

        ```CSS
        #father{
            perspective:1000px;
        }
        #demo{
            transform:translateZ(-500px);
        }
        ```

    5.  translate3d(x,y,z)

    **经验:利用 translate 可以使绝对定位元素居中**

    ```CSS
    .item{
        position:absolute;
        left:50%;
        top:50%;
        transform:translate(-50%,-50%);
    }
    ```

2.  scale:用于对给定元素进行缩放(属性值为数字)

    1. scaleX() 在 X 方向缩放
    2. scaleY() 在 Y 方向缩放
    3. scale( , ) 在(X,Y)方向缩放

3.  rotate:用于对给定元素进行旋转(属性值为角度)

    1.  rotateZ() 绕 Z 轴旋转，也是最多用的
    2.  rotateX() 绕 X 轴旋转
    3.  rotateY() 绕 Y 轴旋转
    4.  rotate3d( , , )

    **经验:一般情况下用于旋转 360deg 来做 loading**

4.  skew:用于倾斜给定元素(属性值为角度)
    1.  skewX() X 方向倾斜
    2.  skewY() Y 方向倾斜
    3.  skew( , ) (X,Y)方向倾斜

# transition 属性的简单介绍

- **transition 属性用于补充中间帧**

* 语法:

```CSS
transition:属性名 时长 过度方式 延迟
```

- 语法内参数:
  1. 属性名:使某个 CSS 属性的变化变为动画 可以填入 all 代表所有属性
  2. 时长:动画时间 可填秒或毫秒
  3. 过度方式:主要有 linear/ease/ease-in/ease-out 等，[具体需要参考数学知识](https://developer.mozilla.org/zh-CN/docs/Web/CSS/timing-function)
  4. 延迟:动画延迟多长时间后开始

* 注:
  1. 并不是所有的元素都可以过度
  2. display:none ==> block 无法过度，改为 visibility:hidden ==> visible(元素会保留位置)
  3. background 可以过度
  4. opacity 可以过度，但是元素还会保留位置

# animation 属性的简单介绍

- **animation 用于动画**

* 语法:

```CSS
animation:时长 过度方式 延迟 次数 方向 填充模式 是否暂停 动画名
```

- 语法内参数:

  1. 时长:动画时间 可填秒或毫秒
  2. 过度方式:与 transition 一致
  3. 延迟:动画延迟多长时间后开始
  4. 次数:填入数字 也可以填入 infinite
  5. 方向:reverse(反向)/alternate(交替)/alternate-reverse
  6. 填充方式:none/forward/backwards/both
  7. 动画名

     **以上均有对应的属性**

* 如何写 animation 的动画

  - 用@keyframes 方法

        **keyframe 中有两种写法**

        1. 百分数写法
        ```CSS
        @keyframes (动画名){
                0%{
                    (动画样式);
                }
                (任意百分数){
                    (动画样式);
                 }
                100%{
                    (动画样式);
                }
        }
        ```

        2. from to 写法:
        ```CSS
        @keyframes (动画名){
                from{
                    (动画样式);
                }
                to{
                    (动画样式);
                }
        }
        ```

# 两种动画的写法

1. transform 动画:

   - 思路:
     1. (a 状态) ===transform===> (b 状态)
     2. (b 状态) ===transform===> (c 状态)

   * Q:如何知道状态的改变？
   * A:通过 setTimeOut 或者监听 transitionend 事件
   * [一个小例子](http://js.jirengu.com/nadaq/1/edit?html,css,js,output)

2. animation 动画

# 以上属性的综合运用

[CSS 桃心动画](http://js.jirengu.com/waneroguqe/1/edit?html,css)
