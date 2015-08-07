title: '图形拼接技术：OpenCV, SIFT'
date: 2015-08-03 13:22:09
tags: opencv,sift,图形技术
---
某天，嘴炮打的太嗨，说可以用APP识别连续拍的几个图片，然后拼接起来，就像iPhone自带的那个全景拍照模式，Panorama mode。[很多人也在问](http://stackoverflow.com/questions/14062932/libraries-to-capture-panorama-in-ios-6)。

![](https://github.com/foundry/OpenCVSwiftStitch/raw/meta/meta/example.big.jpg)

##OpenCV

发现OpenCV里已经集成了一个stitch，附上[找到的例程代码](https://github.com/foundry/OpenCVStitch)。

##SIFT

网上搜到，说叫Rob Hess的大神搞了个基于OpenCV的SIFT算法。这个[SIFT](https://en.wikipedia.org/wiki/Scale-invariant_feature_transform)([中文介绍](http://blog.csdn.net/pi9nc/article/details/9251387))据说是碉堡扎天的很，通过比对特征点，来拼接图片。[github](https://github.com/search?l=C%2B%2B&o=desc&q=SIFT&s=stars&type=Repositories&utf8=%E2%9C%93)上面的有很多应用。

[另一篇中文SIFT使用的介绍](http://ppwwyyxx.com/2013/SIFT-and-Image-Stiching/)，[他的例程](http://github.com/ppwwyyxx/panorama)

![例子](https://github.com/ppwwyyxx/panorama/raw/master/results/small/apartment.jpg)


这有个例子[AutoStitch](http://www.cs.bath.ac.uk/brown/autostitch/autostitch.html)，据说可以免费用，有MAC版，而且我手机拍的照片直接就拼起来了，敬仰啊。可惜这个找不到源码。

![例子](http://www.cs.bath.ac.uk/brown/autostitch/half950.jpg)

![例子](http://www.cs.bath.ac.uk/brown/autostitch/serratus950.jpg)


然后又发现一个叫[Hugin](http://hugin.sourceforge.net/)的，好像很了得，就是太大了，不知道怎么搞进APP里去。

##K-Means, RANSAC

这俩是什么鬼完全不懂了～好吧，谷歌一下之后发现K-Means是聚类算法，RANSAC是什么随机一致性什么什么算法。  ：（



##总之

[一个PDF快速了解关键点～](http://mi.eng.cam.ac.uk/~cipolla/lectures/4F12/Slides/4F12-ImageStitching.pdf)

`为什么在avfoundation就没有接口啊，擦！直接开出来大家不都可以直接用了嘛！差评！`

