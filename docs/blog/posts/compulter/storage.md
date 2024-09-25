---
date:
  created: 2024-09-24
draft: true
categories: 
  - Compulter
authors:
  - squidfunk
---

# [存储芯片](https://www.cnblogs.com/rijiyuelei/p/17320772.html)

## Flash Memory



## 3D Xpoint

## 使用Flash ID查看SSD颗粒

[下载地址](http://vlo.name:3000/ssdtool/)

先需要知道自己的主控是什么，常见的是这些

* Phison = 群联

* SMI = 慧荣

* Marvel = 美满电子（马牌主控）

* Maxio = 联芸

* Yeestor(SiliconGo) utility = 得一微

我一般的猜测顺序： 杂牌盘（移速、铨兴）先试 Yeestor，然后是 SMI ，Phison ，Marvel

正规盘可以跳过 Yeestor 从SMI 开始

## 名词解释

Flash type：颗粒类型

关于 MLC / TLC /QLC 的区别强烈建议看硬件茶谈这个

[【硬件科普】固态硬盘的缓存是干什么的？有缓存和无缓存有什么区别？_哔哩哔哩_bilibili](https://www.bilibili.com/video/BV1aF411u7Ct/?spm_id_from=333.999.0.0)

**Channel：通道**

提到一个固态硬盘的通道数量，多数时候说的是闪存通道，但M.2 NVMe固态硬盘会有PCIE通道的参数。我们这里谈的是前者。

闪存通道数量直接反映了固态硬盘的并发读写能力。可以简单理解为马路上有多少条车道，显然通道数量越多，理论性能越好。当然，还有很多影响因素，通道数量只是一个底子。

**CE：片选信号**

紧跟闪存通道之后的往往就是CE数量。经常可以在一些固态硬盘评测中看到这样的介绍，某某主控支持X通道，每通道支持Y CE。CE是Chip Enable片选的缩写，下图是一个东芝闪存颗粒的逻辑结构，2 Die封装，拥有两个CE信号。

除了通道可以并行提升吞吐量之外，多CE交错也可以提高固态硬盘性能。主控的闪存通道以及每通道支持的CE数量还会影响它最终能够提供多大的固态硬盘容量。


