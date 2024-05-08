---
title: git merge和git rebase
date: 2022-05-24 14:51:10
categories:
- git
tags:
- git
- detail
---

合并分支代码是 `git` 日常使用中的高频操作

通常来讲，有以下三种方式：

- `merge` 
- `rebase`
- `cherry pick`

本文重点讲解前两种的区别

<br/>

### git merge

有三种方式：

- `fast-forward` 这是默认的方式

```bash
git checkout master
git merge dev
```

如果源分支和目标分支没有分叉

![alt 图标](https://img.czjge.cn/blog/202205241533.png)

git会简单地把源分支的HEAD指针移动到目标分支的最新提交点上

![alt 图标](https://img.czjge.cn/blog/202205241538.png)

- `no-ff` 

```bash
git checkout master
git merge dev --no--ff
```

`master` 分支会生成新的一次 `commit` 

![alt 图标](https://img.czjge.cn/blog/202205241547.png)

- `squash` 和 `no-ff` 非常类似，区别是不会保留对合入分支的引用

```bash
git checkout master
git merge dev --squash 
```

![alt 图标](https://img.czjge.cn/blog/202205241549.png)

### git rebase

对于源分支和目标分支有分叉的情况

`master` 分支在 `B` 提交后切出 `dev` 分支

随后 `master` 分支提交到 `M` ，`dev` 分支经过 `C` 和 `D` 提交

![alt 图标](https://img.czjge.cn/blog/202205241601.png)

此时，我们执行变基操作：

```bash
git checkout dev
git rebase master
```

![alt 图标](https://img.czjge.cn/blog/202205241623.png)

可以看到：`git` 从 `B` 提交后开始提取 `dev` 分支的提交 `C` 和 `D` 

然后 `dev` 分支指向 `master` 分支的最新提交 `M` 上

最后把提取的 `C` 和 `D` 提交以新的 `commit` 接到 `M` 后

此时 `dev` 分支的 `base` 是 `M` 提交
