---
title: Unity 性能优化 | 贴图优化、声音优化 等
lang: cn
date: 2019-09-10 13:14:05
tags:
	- 性能优化
	- Unity图片优化
	- Unity贴图优化
	- Unity声音优化
categories:
	- Unity
---


## 图片相关优化

- 压缩格式优化 [简书](https://www.jianshu.com/p/f7c3741f22af)
    - 高清晰无压缩 > RGBA32 缺点 内存占用大, 显示运行内存
    - 中清晰中压缩 > RGBA16+Dithering(TexturePacker)内使用FloydSteinberg算法处理
        - Dithering抖动对拉伸放大是不友好的
        - RGB16针对不带透明通道非2次幂图片, 但是效果略逊于RGB32。
    - 低清晰高压缩 > ETC1+Alpha/PVRTC4
        - ETC1不带透明通道, 需要外挂一个携带Alpha图片
        - 使用Shader支持 在Shader 中吧RGB 和 A 合并 RGBA
    - PVRTC4
        - 必须是2次幂
    - [Android]
        - ETC1, 不支持dxt 
    - [Iphone/Ipand]
        - PVRTC4 压缩默认
        - RGBA16 清晰度高但是渐变不合适
        - RGBA32 高保真
        - 16it/尺寸减半 压缩 UI Icon 


## 声音相关优化

1.取消Preload Audio Data（预加载音频数据）选项
2. 把Override for Android选项勾上，并且设置Load Type为Streaming。
> 注：Load Type=Streaming	音频剪辑将放入缓存区中，并且从缓存区中播放，一旦播放完后，便被卸载掉

推荐将Load Type设置为Decompress on Load（在加载时解压）会运行的更流畅（并不是使用于任何的音频，只是使用于频繁使用的音频）

- 参考链接: 
	-[微信公众号(游戏蛮牛)-Unity性能优化—声音优化](http://mp.weixin.qq.com/s/4BEC9IrrTUn9_Q81_cWt2g)


--- 

版权声明：本文为博主原创文章，遵循 [CC 4.0 BY-SA](http://creativecommons.org/licenses/by-sa/4.0/) 版权协议，转载请附上原文出处链接和本声明。
本文链接：https://tdou.cc/cn/Unity-Optimize/