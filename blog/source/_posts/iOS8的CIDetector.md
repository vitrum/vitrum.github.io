title: iOS的CIDetector
date: 2015-08-07 18:04:52
tags: CIDetector,图像识别
---

前两天还在抱怨说为啥iOS不自带矩形识别之类的功能，今天就被抽脸了。

下午在[Tim9Liu9的个人iOS开发总结项目](https://github.com/Tim9Liu9/TimLiu-iOS#%E5%8A%A8%E7%94%BB)中发现了这个[IPDFCameraViewController](https://github.com/mmackh/IPDFCameraViewController)用的就是iOS自带的CIDetector功能，屌炸天了。

![IPDFCameraViewController](https://raw.githubusercontent.com/mmackh/IPDFCameraViewController/master/mockup.png)

这个项目是InstaPDF公司开发的。他们以前的[MAImagePickerController](https://github.com/mmackh/MAImagePickerController-of-InstaPDF)项目确实用的也是OpenCV。

现在IPDFCameraViewController支持相机定焦拍摄、滤镜、闪光、实时边框检测以及透视矫正功能，并有简单易用的API。

CIDetector是CoreImage的功能，现在常用于人脸识别、笑容识别、QRCode识别等领域。

[xamarin上更多CoreImage的介绍](http://developer.xamarin.com/guides/ios/platform_features/introduction_to_coreimage/)

##另

人家说至少要iOS8,iPhone5以上。

呵呵

