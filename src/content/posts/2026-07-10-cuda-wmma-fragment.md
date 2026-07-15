---
title: "CUDA学习之路[1]：WMMA fragment 是什么"
published: 2026-07-10
description: "整理 wmma::fragment、load_matrix_sync、mma_sync 和 store_matrix_sync 的基本关系。"
image: "api"
tags: ["CUDA", "Tensor Core", "GEMM", "WMMA"]
category: "CUDA学习之路"
draft: false
---

## 今天学习内容

今天主要理解了 WMMA 的基本流程：

1. `wmma::fragment` 用来声明矩阵小块；
2. `wmma::load_matrix_sync` 从全局内存或共享内存加载 tile；
3. `wmma::mma_sync` 在 Tensor Core 上执行矩阵乘加；
4. `wmma::store_matrix_sync` 把结果写回内存。

## 我的理解

WMMA 可以看作 CUDA 对 Tensor Core 的高级封装。

它不是让每个 thread 单独算一个元素，而是让一个 warp 协作完成一个小矩阵乘法。

## 后续问题

- WMMA 的 fragment 具体如何映射到 warp 内线程？
- `wmma::load_matrix_sync` 对内存布局有什么要求？
- WMMA 和 MMA 指令有什么区别？
