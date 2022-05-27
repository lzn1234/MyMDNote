#### 在同一个 Target 中

###### Project OC 和 Swfit 相互调用

当你在 OC 项目中建立一个 Scwift 文件时(在 Swift 中创建 OC 文件一样)，系统会弹窗并引导你创建 MainProject-Bridging-Header.h 和 MainProject-Swift.h 文件

- Swift 调用 OC

​	 只需要 MainProject-Bridging-Header.h 引入需要调用的头文件即可

- OC 调用 swift 
   Swift 的属性或者方法如果要被 OC 调用，需要用`@objc`修饰

```swift
class Dog: NSObject {
    
    @objc let legNumber = 4
    var temper = "temper-good"
    @objc var friend = Cat()

    @objc func eat() {
        print("The dog is eating")
    }
}
```

然后在 OC 中导入 MainProject-Swift.h 文件即可

MainProject-Swift.h 在工程中是没有对应的实体文件，Swift 中被 `@objc` 修饰的属性和方法都被转化为对应的 OC 属性和方法存储在该文件中，这就是为什么OC 可以调用 Swift 类