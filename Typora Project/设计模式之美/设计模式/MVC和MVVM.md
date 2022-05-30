#### M-V-C

------

##### 什么是MVC

​	按照类的指责将其分为**模型(model)** 、**视图(view)**、**控制器(controller)**模块，在 app 中，你可以将 View 类当作视图层，将数据作为模型层，将 ViewController类作为控制层。

​	简单来说你可以把这三个模块看作是数据的**输入、处理、输出**

![img](/Users/zhennan/Public/Typora Project/设计模式之美/设计模式/src=http%3A%2F%2Fimages.cnitblog.com%2Fblog%2F576891%2F201410%2F020901111285535.jpg&refer=http%3A%2F%2Fimages.cnitblog.com&app=2002&size=f9999,10000&q=a80&n=0&g=0n&fmt=jpeg)



##### 指责划分

**model**：数据业务模型相关，封装数据**构建逻辑**等功能

**view**：展示用户看到的视图页面以及部分用户交互相关

**controller**：

- 作为**桥梁**连接视图层和模型层，创建 view 来布局用户界面，同时创建 model 来管理数据并将数据加载到视图上。

- 当 model 发生变化时，controller 会及时通知 view 进行变更。
- 当用户进行交互需要改变数据时，需要向下传递通过 controller 来更改 mdoel



##### 优点：

- 将项目模块按照其指责**解耦合**，提高代码的可读性和可维护性，同时有利于一些通用组件的复用。

  

##### 缺点:

- **视图创建、模型创建、连接 model 和 view 通讯**等逻辑都需要在 controller 里实现，此外你还要在 controller 中实现**网络请求**和**本地存储**之类和 model 相关的逻辑，使得控制层过于臃肿，违背了设计的原则。



#### M V V-M

------

##### 什么是 MVVM

​	按照类的指责将其分为**模型(mode)、视图(view)、视图模型(viewModel)**模块，其核心是 view 和 viewModel 的**双向数据绑定**。

​	在 MVVM 中，model 和 view 的职责和 MVC 中的一致，不同的是 MVVM 将 MVC 中 **控制层(Controller)** 中的**网络请求**、**本地存储**等数据相关逻辑抽取出来封装为**视图模型(ViewModel)**模块，在这个模块中，开发者对后端获取的数据进行**转换处理、二次封装和其他处理**，生成符合 view 层使用预期的视图数据模型。

<img src="/Users/zhennan/Public/Typora Project/设计模式之美/设计模式/src=http%3A%2F%2Fupload-images.jianshu.io%2Fupload_images%2F1653926-7ed45d1af126df79.png&refer=http%3A%2F%2Fupload-images.jianshu.io&app=2002&size=f9999,10000&q=a80&n=0&g=0n&fmt=jpeg" alt="img" style="zoom:75%;" />



##### 指责划分

- **model**：数据业务模型相关，封装数据**构建逻辑**等功能

- **view**：展示用户看到的视图页面以及部分用户交互相关

- **ViewModel**：封装网络请求、数据转换以及数据本地存储等逻辑。
- **ViewController**：负责 ViewModel 和 View 层的通讯，以及界面生命周期控制和界面控制跳转。



##### 优点

- 是MVC 架构的变种，和 MVC 相比，耦合度更低，类和类之间的结构更清晰。
- 使用双向绑定，简化代码。

##### 缺点

- 对于耦合度高的逻辑难以处理，如果引入 RAC 框架会使得学习成本增加。

