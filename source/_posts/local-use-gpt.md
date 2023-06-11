---
title: 本地使用 gpt 的方式
date: 2023-06-11
categories:
  - ChatGPT
tags:
  - ChatGPT
---

## 本地使用 gpt 的方式

1.下载并安装 Docker [官网下载]:[https://www.docker.com/products/docker-desktop/]

2.使用开源项目：潘多拉 (Pandora) [【github】]:[https://github.com/pengzhile/pandora]

3.一键安装命令：

```shell
docker pull pengzhile/pandora

docker run  -e PANDORA_CLOUD=cloud -e PANDORA_SERVER=0.0.0.0:8899 -p 8899:8899 -d pengzhile/pandora
```

4.获取自己的 Access TOKEN：<http://chat.openai.com/api/auth/session>

5.访问本地链接：<http://127.0.0.1:8899> 即可搞定！
