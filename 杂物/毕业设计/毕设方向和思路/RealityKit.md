### 概述

使用 RealityKit 框架实现高性能的 3D 模拟和渲染，RealityKit 利用 ARKit 框架提供的信息，将虚拟对象无缝集成到现实世界中

使用 RealityKit 丰富的功能来创建吸引人的 AR 体验

- 







#### WWDC 19 :RealityKit 和 RealityComposer



##### AR 效果的不足之处

- AR 物体和真实世界的交互 （重力模拟？）
- AR 附着于真实世界的物体（在 Reality Composer 中存在的3D物体、人脸、图像锚点）
- 虚拟物体可以影响真实世界 （没感觉到）
- AR 效果和真实世界匹配 （没感觉到）



苹果推出新的 AR 框架 Reality，具有以下特征

- AR First
- 真实感渲染和模拟

- 只支持 swift 语言
- 跨平台，支持 iOS 和 macOS



RealityKit 融合了各种功能以及 ARKit 和 Metal技术

- Randering（渲染）：使用 metal 技术构建，针对苹果 GPU 进行优化，支持**最新特性**，支持**物理着色**，专注于 AR 设计
- 动画：skeletal 和 transform
- 物理效果：碰撞检测，刚体力学
- 网络同步：多人协作构建 AR
- 实体和组件系统
- 音频空间源



RealityKit 框架右四大组件构成： ARView、Scene、Anchor、Entity

在 AR view 中添加锚点、在锚点中添加实体



ARView 的功能

- 建立环境 
- 处理手势
- 聚焦于 APP
- 真实感镜头效果

这些功能的具体体现有：阴影(Shadowing),运动模糊(Motion Blur),景深(Depth of Field),摄像机噪点(Camera Noise)



#### WWDC 20 Reality 的新功能

- Video materials：视屏材料，应用 vedio 作为 AR 模型的渲染材料，使得其展示更加多样化且让开发者能够更加方便的定义展示的 AR 模型，同时使得 Entity 作为 vedio 的空间音频源
- Scene understanding ：实现虚拟内容与现实世界互动， ARView 的 environment 属性





WWDC 21 发布了 RealityKit2，更新了 3D 渲染能力 和 AR 能力（slam 和 cv）

WWDC 21 发布了 Object Capture 将一组高清2D图片转化为 3D模型

![img](/Users/zhennan/Public/Typora Project/毕业设计/毕设方向和思路/26cf319a4ee11597449d3bef79d480ad.png)

图片锚点：App Clip Code

mac 独占的 Object Capture，作为跨平台的 RealityKit 在 mac 上的







现在，你已经了解了苹果最新，最出色的RealityKit框架，该框架首先为AR设计，旨在帮助降低AR开发人员每天必须面对的复杂性。





相关 WWDC 内容

- WWDC19：[Introducing RealityKit and Reality Composer]()

- WWDC20： [What's new in RealityKit](https://developer.apple.com/videos/play/wwdc2020/10612/)

- WWDC21： 

