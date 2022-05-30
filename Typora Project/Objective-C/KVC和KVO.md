【第一步】查找三种`setter`方法，查找顺序是`set<Key> --> _set<Key> --> setIs<Key>`

- 如果`包含其中任意一个`，直接设值属性value（`key是指成员变量名`，首字符大小写需要符合KVC的`命名规范`）
- 如果没有，进入【第二步】

【第二步】判断`accessInstanceVariablesDirectly`是否返回`YES`

- 如果返回YES，则查找实例变量进行赋值，查找顺序是

  ```
  _<Key> --> _is<Key> --> <Key> -- > is<Key>
  ```

  - 如果找到任意一个就进行赋值
  - 如果没有找到进入【第三步】

【第三步】如果`setter方法`和`实例变量`都没找到，会执行`setValue：forUndefinedKey:`，默认抛出`NSUndefinedKeyException`异常





### KVO



如何创建一个KVO：

1.为一个对象添加一个Observer监听。

```objective-c
    [person addObserver:self forKeyPath:@"name" options:NSKeyValueObservingOptionNew context:nil];
```

2.重写observe

```objective-c
- (void)observeValueForKeyPath:(NSString *)keyPath ofObject:(id)object change:(NSDictionary<NSKeyValueChangeKey,id> *)change context:(void *)context {
    NSLog(@"change:%@",change);
}
```

3.移除KVO
