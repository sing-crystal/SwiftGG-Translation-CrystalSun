title: ""
date: 
tags: [IOSCREATOR]
categories: []
permalink: 
keywords: 
custom_title: 
description: 

------

原文链接=https://www.ioscreator.com/tutorials/facebook-ios-tutorial-ios10
作者=Arthur Knopper
原文日期=2017/04/26
译者=Crystal Sun
校对=
定稿=
发布时间=

<!--此处开始正文-->

借助 Social Framework，可以给自己的 App 添加社交网络分享的功能。在本节教程中，将使用 social framework 往 Facebook 上发布一条状态。本节教程使用的是 Xcode 8.3 和 iOS 10.3。

### 设置工程

打开 Xcode，创建一个 Single View Application。

![](https://static1.squarespace.com/static/52428a0ae4b0c4a5c2a2cede/t/58ff88928419c2b2a27d0754/1493141675229/single-view-xcode-template?format=1500w)

Product Name 使用 **IOS10FacebookTutorial**，填写自己的 Organization Name 和 Organization Identifier，Language 一栏选择 Swift，Devices 一栏选择 iPhone。

![](https://static1.squarespace.com/static/52428a0ae4b0c4a5c2a2cede/t/58ff88c71b10e3c8c1dc6a0d/1493141718478/facebook-project?format=1500w)



### 设置 Storyboard

从 Object-Library（控件库）中拖拽一个 Button 到主界面，将其标题改为 *“Post to Facebook”*。选中该控件，点击 Storyboard 右下角 Auto Layout 的 Align 按钮，选择 “Horizontally in Container”，点击 “Add 1 Constraint”。

![](https://static1.squarespace.com/static/52428a0ae4b0c4a5c2a2cede/t/58ff890c1b10e3c8c1dc7050/1493141792034/auto-layout-horizontally-in-container?format=750w)



仍然选中该 Button 控件，点击 Auto Layout 的 Pin 按钮，选中上面的线，点击 “Add 1 Constraint”。

![](https://static1.squarespace.com/static/52428a0ae4b0c4a5c2a2cede/t/58ff89c62994caa7f86f42db/1493141974045/auto-layout-pin-to-top?format=750w)



Storyboard 看起来应如下图所示：

![](https://static1.squarespace.com/static/52428a0ae4b0c4a5c2a2cede/t/58ff8a0703596e67a225d6a2/1493142038417/facebook-storyboard?format=1000w)



点击 Assistant Editor，确保 **ViewController.swift** 文件可见。Control 拖拽或右键点击拖拽，将 Button 控件拖拽到 ViewController 类下面，创建下列 Action。

![](https://static1.squarespace.com/static/52428a0ae4b0c4a5c2a2cede/t/58ff8a62ff7c503f699573bd/1493142138444/post-to-facebook-action?format=750w)



打开 **ViewController.swift** 文件，引入 social framework。

```swift
import Social
```

接下来实现 **postToFacebook** 方法：

```swift
@IBAction func postToFacebook(_ sender: Any) {
    // 1
    if SLComposeViewController.isAvailable(forServiceType: SLServiceTypeFacebook) {
        // 2
        if let controller = SLComposeViewController(forServiceType: SLServiceTypeFacebook) {
            // 3
            controller.setInitialText("Testing Posting to Facebook")
            // 4
            self.present(controller, animated:true, completion:nil)
        }
    }
    else {
        // 3
        print("no Facebook account found on device")
    }
}
```

1. 检查设备上的 Facebook 账户是否可用。
2. 创建 SLComposeViewController 对象，该对象用于显示 Facebook 状态发布界面和全部的功能。
3. 设置发布 Facebook 状态的默认文案。
4. 显示该 controller。
5. 如果 Facebook 账户尚未设置，在控制台（console）里显示提示信息。

**运行**程序，开始往 Facebook 上发状态，确保模拟器的 Facebook 账户已经设置好了，在模拟器的菜单栏 Settings -> Facebook 里可以设置。

![](https://static1.squarespace.com/static/52428a0ae4b0c4a5c2a2cede/t/58ff9349e3df280d3d0dbafe/1493144421077/facebook-simulator?format=750w)

可以从 [github](https://github.com/ioscreator/ioscreator) 上下载 **IOS10FacebookTutorial** 教程的源代码。