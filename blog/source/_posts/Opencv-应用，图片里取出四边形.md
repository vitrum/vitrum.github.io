title: Opencv应用，图片里取出四边形
date: 2015-07-28 10:18:26
tags:opencv,图形识别
---

有这样一个需求，在桌上有张纸，可能是票据，合同什么的，用手机咔嚓咔嚓拍下来，然后自动把纸张缩放到合适的大小。可是拍的时候有可能是歪的，不一定就对的很正，桌子也可能是有花纹啊，边上有小干扰物啥的。

这要是做APP的话，可怎么搞，总之是要检测纸张边缘，取出四边形，然后拉伸成规则长方形。

好像选opencv是必然的，还有更好的选择吗？

一、图像预处理
据说通常都要对图像进行降噪避免误测，常见的做法是先进行高斯模糊，然而这并没有什么卵用，会把图像弄模糊，边界都不清楚就没法玩了。所以有人说，可以用Mean Shift，Mean Shift的优点就在于如果是像背景桌面的浅色纹理，图像分割的过程中相当于将这些小的浮动过滤掉，并且保留相对明显的纸张边缘，结果如下：

原图
!(http://www.linuxidc.com/upload/2015_01/150118102418484.png)
处理后
!(http://www.linuxidc.com/upload/2015_01/150118102418485.png)

顺便说一句，现在手机分辨率好高，直接处理这么大的图片会比较消耗资源，把图缩小之后处理速度会提升，而且也变相消除了部分干扰。

二、边缘检测
边缘检测这一步，最好是能有人工干预，把大范围标出来，类似这样：
!(http://www.linuxidc.com/upload/2015_01/150118102418486.png)

但实际上这样的用户体验肯定是负分了，所以假设用户的桌面不会这么极端，而是使用相对整洁的桌面并且纸张放置相对规整，类似这样的：
!(http://ww2.sinaimg.cn/large/6cea169fjw1edopgxi1vvj21kw2t4e81.jpg)

这样就不需要用GrabCut做分割，而是直接灰度处理后用canny算子检测边缘。

    // bw is the grayscaled source image
    cv::Canny(bw, bw, 100, 100, 3);

得到边缘图：
!(http://ww4.sinaimg.cn/large/6cea169fjw1edorxrxncwj205k07ewf3.jpg)

三、直线检测

待...




四、判断有效多边形

待...




五、求四顶点坐标

待...



























参考资料：

[用OpenCV实现“扫描全能王”APP](http://daisygao.com/2014/02/17/%E7%94%A8opencv%E5%AE%9E%E7%8E%B0%E6%89%AB%E6%8F%8F%E5%85%A8%E8%83%BD%E7%8E%8Bcamscanner/)

[利用OpenCV检测图像中的长方形画布或纸张并提取图像内容](http://www.linuxidc.com/Linux/2015-01/111962.htm)好像原帖在知乎上

[Automatic perspective correction for quadrilateral objects](http://opencv-code.com/tutorials/automatic-perspective-correction-for-quadrilateral-objects/)
注：我是觉得这篇里硬要凑4条线拼一个四边形有点难，还是检测出一些，然后判断抛弃一些比较好。

[自动透视校正为四边形对象](http://blog.csdn.net/mysteryrat/article/details/8955229) 上一篇加了写中文注释。

[深入剖析mean shift 图像分割 原理及代码](http://blog.163.com/liangq_11/blog/static/35743824201092242725214/) 