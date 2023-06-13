---
title: vue禁止浏览器回退
date: 2023-06-13
categories:
  - vue
tags:
  - vue
---

# vue 禁止浏览器回退

感觉这个作者写的很好，收藏一下地址：

[[高级]深入浅出浏览器的 history 对象 - 掘金](https://juejin.cn/post/6948746074504986655)

[浏览器禁止页面回退 - 掘金](https://juejin.cn/post/6885718550146482184)

> 禁止登录之后通过浏览器返回到登录页面
> 登陆成功用 router.replace 代替 router.push
>
> [编程式导航 | Vue Router](https://next.router.vuejs.org/zh/guide/essentials/navigation.html#%E5%AF%BC%E8%88%AA%E5%88%B0%E4%B8%8D%E5%90%8C%E7%9A%84%E4%BD%8D%E7%BD%AE)
>
> 想要导航到不同的 URL，可以使用 router.push 方法。这个方法会向 history 栈添加一个新的记录，所以，当用户点击浏览器后退按钮时，会回到之前的 URL。
>
> router.replace 的作用类似于 router.push，唯一不同的是，它在导航时不会向 history 添加新记录，正如它的名字所暗示的那样——它取代了当前的条目。

## 禁止退出之后通过浏览器返回到之前的页面

### 退出功能页面

```js
logout(){
   sessionStorage.clear();
   this.$router.push("/login");
 },
```

### 退出后跳转到的页面 在要禁止回退页面的 mounted( )方法中添加禁止浏览器的后退的方法

### 触发后禁止浏览器的后退键

history.pushState(null, null, document.URL);

window.addEventListener("popstate",function(e) {

        history.pushState(null, null, document.URL);

    }, false);

### 在 HTML 文档中，history.pushState() 方法向当前浏览器会话的历史堆栈中添加一个状态（state）

参考地址：[History.pushState() - Web API 接口参考 | MDN](https://developer.mozilla.org/zh-CN/docs/Web/API/History/pushState)
