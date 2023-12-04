---
title: go运行时（runtime）
date: 2022-06-10 10:34:06
categories:
- golang
tags:
- golang
- intro
---

`Go` 编译器产生的可执行代码实际上是运行在 `Go` 的 `runtime` 当中。

### 什么是Go的runtime

`runtime` 由 `C` 语言编写，目录在 `$GOROOT/src/runtime` ，类似 `Java` 和 `.NET` 的虚拟机，
负责：

- 内存分配
- 垃圾回收
- 栈处理
- `goroutine`
- `channel`
- `slice`
- `map`
- `reflection`
- ...

---

### 其他

`Go` 编译后的可执行文件比源代码大很多，这是因为 `Go` 的 `runtime` 嵌入到了每一个可执行文件中。
