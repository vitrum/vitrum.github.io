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

## 补一篇介绍 2015-08-10

[iOS8 Day-by-Day :: Day 13 :: CoreImage Detectors](https://www.shinobicontrols.com/blog/ios8-day-by-day-day-13-coreimage-detectors)


###Detecting Rectangles

Detecting rectangles in images is often one of the first parts of a computer vision algorithm – whether it be automatic business card interpretation, or road sign processing. Although rectangle detection sounds like it should be a really simple process, as with many problems in computer vision, it’s far harder than you might expect. So it’s great that Apple have implemented an efficient algorithm as part of the CoreImage detectors.

The main class associated with CoreImage detectors is the aptly-named CIDetector. The same class is used for all the different types of detectors, and is instantiated with the CIDetector(ofType:, context:, options:) initializer. The type argument is a string, which for a rectangle detector is CIDetectorTypeRectangle. The options argument is a dictionary of settings associated with this detector. The following method created a CIDetector to be used for detecting rectangles:

    func prepareRectangleDetector() -> CIDetector {
      let options: [String : AnyObject] = [CIDetectorAccuracy: CIDetectorAccuracyHigh, CIDetectorAspectRatio: 1.0]
      return CIDetector(ofType: CIDetectorTypeRectangle, context: nil, options: options)
    }


You can see that the options here are specifying the accuracy as high, with the CIDetectorAccuracy key, and the CIDetectorAspectRatio key is used to specify that you’re searching for squares. This aspect ratio doesn’t mean that you’re only looking for squares, but it will be used in the ranking of possible rectangles to determine which is the most likely candidate. For example, if you know that you’re going to use the detector for business cards then setting the aspect ratio to 2.0 will likely yield better results.

Once you’ve created a CIDetector it’s actually really simple to use. The method featuresInImage() takes a CIImage and then returns an array of CIFeature objects (well, a subclass of) which represent the detected objects. In the case of a rectangle detector, the CIFeature subclass is CIRectangleFeature, which has CGPoint properties for each of the four corners of the detected rectangle.

The following method demonstrates how you can use the detector to find a rectangle in a supplied CIImage:

    func performRectangleDetection(image: CIImage) -> CIImage? {
      var resultImage: CIImage?
      if let detector = detector {
    // Get the detections
    let features = detector.featuresInImage(image)
    for feature in features as! [CIRectangleFeature] {
      resultImage = drawHighlightOverlayForPoints(image, topLeft: feature.topLeft, topRight: feature.topRight,
                                                  bottomLeft: feature.bottomLeft, bottomRight: feature.bottomRight)
    }
      }
      return resultImage
    }
    
This unwraps the option detector, before using the featuresInImage() method to perform the detection itself. At the time of writing, the rectangle detector will only ever detect one rectangle in an image, so the features array will have either exactly one or zero CIRectangleFeature objects in it.

This method returns a new CIImage, which contains a red patch overlaid on the source image over the position of the detected rectangle. This uses the utility method drawHighlightOverlayForPoints() method:

    func drawHighlightOverlayForPoints(image: CIImage, topLeft: CGPoint, topRight: CGPoint,
                                   bottomLeft: CGPoint, bottomRight: CGPoint) -> CIImage {
      var overlay = CIImage(color: CIColor(red: 1.0, green: 0, blue: 0, alpha: 0.5))
      overlay = overlay.imageByCroppingToRect(image.extent())
      overlay = overlay.imageByApplyingFilter("CIPerspectiveTransformWithExtent",
    withInputParameters: [
      "inputExtent": CIVector(CGRect: image.extent()),
      "inputTopLeft": CIVector(CGPoint: topLeft),
      "inputTopRight": CIVector(CGPoint: topRight),
      "inputBottomLeft": CIVector(CGPoint: bottomLeft),
      "inputBottomRight": CIVector(CGPoint: bottomRight)
    ])
      return overlay.imageByCompositingOverImage(image)
    }


This method creates a colored image, and then uses the perspective transform filter to map it to the points provided. It then creates a new CIImage by overlaying this colored image with the source image.

In the LiveDetection sample project, the performRectangleDetection() method is used as part in the CoreImageVideoFilter class to run the detector on each of the frames received from the camera, before rendering it on screen. This class is a little more involved than you might expect it to be, and it isn’t within the scope of this article to go in to much detail, however an overview might be helpful.

An AVFoundation pipeline is created which uses the camera as input, and provides a pixel buffer of each frame to a delegate method.
In this delegate method a CIImage is created from this pixel buffer.
The provided filter function (which takes an input CIImage and returns a new CIImage, much like a map function) is passed the current image.
The image is cropped to match the view size it is to be rendered in.
The CIImage is then rendered on the OpenGLES surface using a pre-created CIRenderContext.
Rinse and repeat for each frame received from the camera.
If you need to do live video processing using CoreImage then it might be worth taking a look at this class in greater detail, but if you don’t then the performRectangleDetection() method just takes a CIImage, which you can create using one of the many constructors.

Running this app up will kick off the rectangle detection right away, and you’ll see results like the following on the screen:

![Rectangle Detector](https://www.shinobicontrols.com/wp-content/uploads/2014/08/rectangle_detector.png)

The performance is pretty good for real-time use – certainly the demo app copes well on an iPad 3.


##另

人家说至少要iOS8,iPhone5以上。

呵呵

