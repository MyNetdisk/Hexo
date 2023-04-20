---
title: nodejs新版本引起的：digital envelope routines::unsupported
date: 2023-04-20
categories:
  - node
tags:
  - node
  - vue
---

## 一、前言

> 由于电脑重装系统，重新下载 nodejs,自然更新到最新版本 18，之前的版本才 16。更新到最新 nodejs 版本后，运行 vue 文件，报错：
>
> this[kHandle] = new \_Hash(algorithm, xofLen);
> ^
>
> Error: error:0308010C:digital envelope routines::unsupported

## 二、探索#

常规操作，上网查原因：

node.js 的版本问题

因为 node.js V17 版本中最近发布的 OpenSSL3.0, 而 OpenSSL3.0 对允许算法和密钥大小增加了严格的限制，可能会对生态系统造成一些影响。故此以前的项目在升级 nodejs 版本后会报错。

## 三、解决#

1.推荐：修改 package.json，在相关构建命令之前加入 SET NODE_OPTIONS=--openssl-legacy-provider

```json
"scripts": {
   "serve": "SET NODE_OPTIONS=--openssl-legacy-provider && vue-cli-service serve",
   "build": "SET NODE_OPTIONS=--openssl-legacy-provider && vue-cli-service build"
},
```

这种可以一劳永逸，以后直接通过 npm 执行 scripts 里面的命令即可。不管是项目迭代，还是团队开发，这种都比较有效。

2.当次运行的命令窗口有效：在你当前文件的 cmd 命令窗口输入：

```cmd
SET NODE_OPTIONS=--openssl-legacy-provider
```

回车后输入 npm 运行命令

这种做法，就是每次运行都要输入 SET NODE_OPTIONS=--openssl-legacy-provider，来告诉 nodejs,别使用最新的 SSL3.0,还是使用以前旧版本的。

3.就是 nodejs 版本回退到 16 版本，这样就可以直接运行了。

网上一些答主的做法：

分析下他做法错误之处：首先，他打开 cmd 之后，直接回车：
这种做法很傻，因为你起码要进入到对应文件的位置，不然的话，不出意外的话，就出意外了。

### 最后补充一点：

关于：SET NODE_OPTIONS=--openssl-legacy-provider，其实这种方法不能一劳永逸，它的 legacy 的中文意思翻译过来是经典的，传统的，对于目前 2022 年 12 月 4 号来说，openssl3.0 是最新的，之前的版本属于 legacy 版本，但是随着时间的推移，

未来可能在 2024 年，openssl3.0 可能也变成了 legacy 版本，此时再设置 SET NODE_OPTIONS=--openssl-legacy-provider，来通知 nodejs 使用传统的 openSSL 来执行，那么可能就会运行错误。那么对于产品的迭代维护来说，最好的话，还是使用旧版本的 nodejs,比如 16 版本的，这个才可能是解决问题的关键。

## 四、最后#

记录下闲话，最近在部署 vue 程序在老旧的 windows 服务器上，老旧的服务器是至强 cpu，iis6.0 的，使用起来真操蛋，关键该服务器还是在内网中的，部署起来要远程连接到另一台电脑，另一台电脑再连接到这台服务器上，需要上传部署文件都要先通过微信发给医院内部的人，医院内部的人帮我们传到这台服务器上，是的，远程连接不支持传文件，真操蛋，医院又不给我们权限，自己上传，部署起来真心累，周六日这两天都用来搞这玩意了，最后因为 iis 没办法安装 url 重写和 APR 路由映射，果断放弃使用 iis,使用了 nginx,浪费老子这么多时间！！！！

> 作者：兜里还剩五块出头
>
> 本文链接：https://www.cnblogs.com/hmy-666/p/16949982.html
