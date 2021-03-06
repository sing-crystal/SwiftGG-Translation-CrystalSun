title: "如何检测摇一摇手势"
date: 
tags: [IOSCREATOR]
categories: []
permalink: 
keywords: 
custom_title: 
description: 

---
原文链接=https://www.ioscreator.com/tutorials/detect-shake-gestures-ios-tutorial-ios10
作者=Arthur Knopper
原文日期=2017/04/18
译者=Crystal Sun
校对=
定稿=
发布时间=

<!--此处开始正文-->

iOS 设备可以检测摇一摇手势，在本节教程中，我们将学习如何检测摇一摇手势，检测到该手势后，更新 label 的文案。本节教程使用的是 Xcode 8.3 和 iOS 10.3。

### 设置工程

打开 Xcode，创建一个 Single View Application。

![](https://static1.squarespace.com/static/52428a0ae4b0c4a5c2a2cede/t/58ff88928419c2b2a27d0754/1493141675229/single-view-xcode-template?format=1500w)

Product Name 使用 **IOS10ShakeGestureTutorial**，填写自己的 Organization Name 和 Organization Identifier，Language 一栏选择 Swift，Devices 一栏选择 iPhone。

![](https://static1.squarespace.com/static/52428a0ae4b0c4a5c2a2cede/t/58f52d5a86e6c05ecb274592/1492462962478/shake-gesture-project?format=1500w)

打开 **Storyboard**，从 Object Library 中拖拽一个 Label 控件放到 View Controller 上，双击 Label 控件将文案修改为 *“Shake me”*。选中该 Label，点击 Auto Layout 的 Align 按钮。选中 “Horizontally in Container”，点击 “Add 1 Constraint”。

![](https://static1.squarespace.com/static/52428a0ae4b0c4a5c2a2cede/t/58f52e1e8419c215a1514cc4/1492463192365/auto-layout-horizontally-in-container?format=750w)

选中 Label，点击 Auto Layout 的 Pin 按钮，选中上边距约束线，点击 “Add 1 Constraint”。

![](https://static1.squarespace.com/static/52428a0ae4b0c4a5c2a2cede/t/58f52ef0e58c62578c514aef/1492463458639/auto-layout-pin-to-top?format=750w)

Storyboard 看起来应如下图所示。

![](https://static1.squarespace.com/static/52428a0ae4b0c4a5c2a2cede/t/58f5b9cc9de4bb2a1d108012/1492498913076/shake-gesture-storyboard?format=1000w)

打开 Assistant Editor，确保 **ViewController.swift** 可见。按住 Control 键，将 Label 拖拽到 ViewController 类下，创建下图的 Outlet。

![](https://static1.squarespace.com/static/52428a0ae4b0c4a5c2a2cede/t/58f5b9fb9de4bb2a1d108134/1492498955592/shake-label-outlet?format=750w)

打开 ViewController.swift 文件，首先要让 View Controller 回应点击事件，可以通过 ViewController FirstResponder 实现，添加下列方法：

```swift
override func becomeFirstResponder() -> Bool {
    return true
}
```

接下来，要想检测摇一摇手势，添加 **motionEnded(_:with:)** 方法。

```swift
override func motionEnded(_ motion: UIEventSubtype, with event: UIEvent?) {
    if motion == .motionShake {
        shakeLabel.text = "Shaken, not stirred"
    }
}
```

如果确实是一个 Shake Gesture（摇一摇），那么 Label 的文案就会更新。运行工程，摇一摇测试机。可以点击 iOS 模拟器菜单栏 Hardware 选项下的 Shake Gesture 来摇一摇。

![](https://static1.squarespace.com/static/52428a0ae4b0c4a5c2a2cede/t/58f5bae9d1758e82948d91eb/1492499213334/shake-gesture-simulator?format=750w)



可以从 [github](https://github.com/ioscreator/ioscreator) 上下载 **IOS10ShakeGestureTutorial** 教程的源代码。