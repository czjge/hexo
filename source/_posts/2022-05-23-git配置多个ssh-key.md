---
title: git配置多个ssh key
date: 2022-05-23 14:43:38
categories:
- git
tags:
- git
---

比如我们现在要在家里的 `PC` 上配置2个 `git` 账号：
- 一个公司的 `gitee` 账号：`czjge@gitee.com`
- 一个个人的 `github` 账号：`czjge@github.com`

首先我们来配置码云账号

1. 生成 `ssh key`
   ``` bash
   $ ssh-keygen -t rsa -C "这里是该ssh key的标识" -f ~/.ssh/gitee_czjge_rsa
   ```
2. 在 `~/.ssh` 目录下创建 `config` 文件，内容如下：
   ``` bash
   Host gitee_czjge # 这里可以是任何非重复的标识符，但会影响这里：git clone git@gitee_czjge:czjge/wechat-vote.git
   HostName gitee.com
   PreferredAuthentications publickey
   IdentityFile ~/.ssh/gitee_czjge_rsa
   ```
3. 添加 `ssh key`
   ``` bash
   ssh-agent bash
   ssh-add ~/.ssh/gitee_czjge_rsa
   ```
4. 测试
   ``` bash
   ssh -T git@gitee_czjge
   ```
5. `gitee` 设置里添加公钥
   
`github` 账号同理可配置
