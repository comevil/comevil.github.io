---
layout:     post
title:      HSCCTF-2024 Misc Writeup
subtitle:   HSCCTF2024部分WP
date:       2024-03-24
author:     Whitea
header-img: img/post-bg-coffee.jpeg
catalog: true
tags:
    - CTF比赛
    - HSCCTF
---
## 前言
这次的HSCCTF比赛难度蛮高的，我主要做了Misc以及Osint方向的题目。由于个人水平有限，故本篇博客主要分享比赛时的解题思路，以及遇到的问题为主。

## Misc

### SIGN_IN
附件是一张jpg文件，查看图片的详细内容以及编码，发现编码里还隐藏了另一个jpg文件，用foremost分离看看另一张图片是什么。

图片如下：
![foremost-img][foremost-img]

图片比原来多了`HAPPY_NEW_YEAR`的英文，试了一下，不是flag

猜测可能是LSB隐写，用stegsolve去调整RGB通道，然而却没有什么用。到这里我便不知道如何进行下一步。

后来查看了下大佬的[Writeup](https://yurogod.github.io/ctf/events/HSCCTF-2024)，发现是通过outguess工具就可以得到flag

由于outguess似乎是Linux系统的工具，所以几乎没有使用过该工具。估计是我题目做的少了，下次也给自己电脑弄个Linux系统，不然有些题目不好做。


## Osint
这次osint的题难度挺高的，难的不是找到地方，而是精度。

### NICE_RIVER
图片如下：
![Nice_river][Nice_river]

通过谷歌识图可以识别到该地，图片的桥就是琶洲大桥。

在谷歌地图下看，就是这样
![Nice_river2][Nice_river2]

对比对照图片和谷歌地图的卫星图片，就可以找到大致的地方。
虽然我当时在做的时候坐标一直没有输入正确.....

具体位置如下（借用大佬[WP](https://zhuanlan.zhihu.com/p/686482158)的图片）
![Nice_river3][Nice_river3]

大厦所在的经纬度大约为 23.104156701885007, 113.38407155776493 附近，因此 Flag 为 `{HSCCTF{23.10416,113.38407}`，太阴间了。

### BUILDING
图片如下
![Building][Building]

谷歌识图，可以知道是广州W酒店

这是在百度地图的3D影像，几乎和题目给的图片一模一样
![hotel][hotel]

知道是W酒店，就按照地图给的坐标输入答案，发现怎么都不对

遂放弃....

WP出来后也没有看到具体的定位方法，0.0
Flag：`HSCCTF{23.12188,113.32819}`


## 其他
后面的其它题目几乎是一点思路都没有了，有思路的答案也是差一点才弄出来。实在是太绝望了.......


[hotel]:https://i0.imgs.ovh/2024/03/23/goyGe.jpeg
[Building]:https://i0.imgs.ovh/2024/03/23/govev.jpeg
[foremost-img]:https://i0.imgs.ovh/2024/03/23/goaWW.jpeg
[Nice_river]:https://i0.imgs.ovh/2024/03/23/goqsI.md.jpeg
[Nice_river2]:https://i0.imgs.ovh/2024/03/23/go9iV.png
[Nice_river3]:https://pic3.zhimg.com/80/v2-d437601d4dd7abe1f981fff174d175a6_1440w.webp
