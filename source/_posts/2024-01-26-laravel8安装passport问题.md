---
title: laravel8安装passport问题
date: 2024-01-26 15:25:01
categories:
- php 
tags:
- composer
- php
- debug
---

### 问题

执行：

```shell
composer require laravel/passport
```

![alt 图标](https://img.czjge.cn/blog/%E5%BE%AE%E4%BF%A1%E6%88%AA%E5%9B%BE_20240126154541.png)

### 排查

命令 `composer require laravel/passport` 默认是拉取最新版本，
第一反应是这个包最新版本要求 php8，而我使用的是 php7，所以就拉取历史版本：

```shell
composer require laravel/passport:~10.4.0
```

很遗憾，依旧报同样的错误。  

仔细看 composer 的报错，发现是 `psr/http-message` 版本过高，是不是可以直接降低这个包 版本即可？问题来了，这样做会不会影响其他包？于是进入 composer.lock 文件排查，确认 这个包的被依赖包都可接受该包降低到 `^1.1` 后，问题得到确认。

### 解决

执行：

```shell
composer require psr/http-message:^1.1
```

然后继续安装 `passport`，成功：

![alt 图标](https://img.czjge.cn/blog/%E5%BE%AE%E4%BF%A1%E6%88%AA%E5%9B%BE_20240126160011.png)

