---
title: windows docker desktop安装mysql
date: 2023-06-20
categories:
  - docker
tags:
  - mysql
---

# 1.拉取 mysql 镜像

```shell
docker pull mysql:5.7
```

# 2.查看并启动镜像

```shell
#列出已下载的镜像
docker images
#启动容器，挂载配置文件和数据
docker run --name mysql -v D:/docker/mysql/conf/my.cnf:/etc/mysql/my.cnf -v D:/docker/mysql/logs:/logs -v D:/docker/mysql/data:/var/lib/mysql -v  D:/docker/mysql/conf/conf.d:/etc/mysql/conf.d -e MYSQL_ROOT_PASSWORD=123456 -d -i -p 3306:3306 mysql:5.7
```

# 启动成功

![图片](/image/posts/25961526-2eacc808409edb5f.png)
![图片](/image/posts/25961526-9badcd49512f38c4.png)

# 3. 进入容器内 bash,连接 mysql

```shell
docker exec -it mysql bash
```

> ### 注意：我这里使用的是 Git bash,提示错误 the input device is not a TTY. If you are using mintty, try prefixing the command with 'winpty'
>
> ### 在命令前加 winpty 即可

```shell
#进入容器内
winpty docker exec -it mysql bash
#连接mysql
mysql -u root -p
```

# 4. 添加远程登录用户

```shell
CREATE USER 'test'@'%' IDENTIFIED WITH mysql_native_password BY '123456';
```

# 5. 授予权限

```shell
GRANT ALL PRIVILEGES ON *.* TO 'test'@'%';
```

# 6.使用 navicat 连接成功

![图片](/image/posts/25961526-b3102cd404a8038b.png)

# 7.修改本地配置文件验证是否生效

### 修改 mysql/conf/my.cnf 文件

```shell
[mysqld]
#设置表名区分大小写
lower_case_table_names=1
```

### 重启 mysql 查看效果，已经生效

![图片](/image/posts/25961526-1716891e7347b99a.png)

# 如果修改配置没有生效, 修改容器中 mysql.cnf 文件的权限为 644, 再重启即可生效

```shell
chmod 644 mysql.cnf
```

> 作者：小鱼大头<br>
> 链接：https://www.jianshu.com/p/fd5d388dbf7d<br>
> 来源：简书<br>
> 著作权归作者所有。商业转载请联系作者获得授权，非商业转载请注明出处。
