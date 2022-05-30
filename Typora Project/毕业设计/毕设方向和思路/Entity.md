

### Entity



------



## AnchorEntity(锚点实体)

将实体和场景绑定在一起的锚

------

### 概述

​	使用 `AnchorEntity`  来控制 **RealityKit** 如何将**虚拟对象**放入场景中。`AnchorEntity` 遵循 `HasAnchoring` 协议，这给了它一个 `AnchoringComponent` 实例。

​	`RealityKit` 根据 `AnchoringComponent` 的 `target` 属性来放置锚定。例如，您可以配置一个锚定实体，使其停留在AR场景(如桌子或地板)中检测到的水平面上，而 **RealityKit**一旦在现实世界中检测到适当的水平面，就会自动放置锚定实体。

​	有关使用 **Reality Composer** 可用的不同类型的锚的信息，请参见：[Selecting an Anchor for a Reality Composer Scene](https://developer.apple.com/documentation/realitykit/creating_3d_content_with_reality_composer/selecting_an_anchor_for_a_reality_composer_scene).



<img src="/Users/zhennan/Public/Typora Project/毕业设计/毕设方向和思路/rendered2x-1635179528.png" alt="Diagram showing the components present in the anchor entity. It contains three boxes labeled Transform component, Synchronization component, and Anchoring component." style="zoom:50%;" />





​	直接将 `AnchorEntity` 添加到 **Scene** 的锚点集合（anchors collection） 中，或者将它们添加到场景中另一个`AnchorEntity` 的子集合中，从而添加到场景层次结构中的任何地方。因为 `AnchorEntity` 是 `Entity` 的子类，你可以让一个`AnchorEntity` 成为任何其他实体的子实体。**RealityKit** 可能会随着场景的更新而移动锚定实体，所以  `AnchorEntity`  的位置和旋转可能会相对于它的父节点发生变化，即使你的代码从未修改它的 `transform` 属性。

​	如果 **RealityKit** 无法检测到它们的合适位置，一些锚实体可能根本不会出现在场景中。例如，一个带有图像目标的锚定实体直到RealityKit在现实世界中检测到指定的图像才会出现在场景中



<img src="/Users/zhennan/Public/Typora Project/毕业设计/毕设方向和思路/rendered2x-1635968966.png" alt="Block diagram showing how anchor entities attach to a scene, and how they support entity hierarchies. The root box of the hierarchy diagram represents the ARView. It has one child representing the ARView’s scene, and that scene has two children, both of which are anchor entities. Each of the anchor entities have a hierarchy of child entities beneath them, most of which are labeled Entity, but one of the entities in the hierarchy is another anchor entity." style="zoom: 50%;" />

你可以在 **RealityKit** 场景中使用多个锚。例如，一个锚可以在水平面上放置玩具车，比如桌子，而另一个锚可以将一个信息文本气泡绑定到同一场景中的图像上。









## ModelEntity(模型实体)

**RealityKit** 渲染和可选模拟的物理对象的表示

------



### 概述

使用一个或多个 `ModelEntity` 在场景中放置物理对象。除了它们从 `Entity` 类继承的组件之外，模型实体还有通过 `ModelComponent` 描述的几何形状。 `ModelEntity` 通过遵守 `HasModel` 协议来获取 `ModelComponent`。您可以指定网格和材料来控制模型实体的出现方式。

