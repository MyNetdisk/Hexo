---
title: 解决 grid 布局 item 被子元素撑开的问题
date: 2023-07-25
categories:
  - css
tags:
  - grid
---

# 一、问题描述

当 item 的高度或者宽度单位是 fr 或者 auto 时，其子元素高度或者宽度高于 item 时，子元素会把 item 撑开
![Why](/image/posts/up-cde079bf456ca3d54f3aabf42e1f0fadb4f.webp)

```html
<div class="container">
  <div class="item">
    <div class="inner">
      <p class="content">1</p>
    </div>
  </div>
  <div class="item">
    <div class="inner">
      <p class="content">2</p>
    </div>
  </div>
</div>
```

```html
<style>
  .container {
    height: 500px;
    background-color: aliceblue;
    display: grid;
    grid-template-columns: 1fr;
    grid-template-rows: 1fr 1fr;
  }

  .item {
    border: 1px solid #d0d0d0;
    padding: 10px;
    box-sizing: border-box;
  }

  .inner {
    height: 100%;
    overflow-y: auto;
  }

  .content {
    box-sizing: border-box;
    background-color: aqua;
    height: 300px;
    margin: 0;
  }
</style>
```

# 二、原因分析（仅基于目前的认知，可能是错的）

当 grid-template-rows、grid-template-columns 设置成 px、百分比时不会存在该问题，fr 或者 auto 时相当于高度未设置，所以类似于块级元素会被子元素撑开

# 三、解决方案

方案 1：item 设置 min-height:0

方案 2：grid-template-rows、grid-template-columns 不用 fr 单位，或者将 fr 改成 minmax(0, 1fr)

grid-template-rows: minmax(0, 1fr) minmax(0, 1fr);

方案 3：item 设置 overflow: hidden

### 关于本文

> 作者：Clover286
>
> 本文链接：https://my.oschina.net/Cubicluo/blog/5356233
