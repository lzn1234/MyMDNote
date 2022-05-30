## Masonry中的三大方法

- #### makeConstraints

mas_makeConstraints值负责新增约束，Autolayout不能同时存在两条针对同一对象约束，否则会报错。

**添加约束之前一定要将该视图添加到父视图之上**



- #### remakeConstraints

该方法会清除之前的所有约束，仅保留方法内添加的约束



- #### updateConstraints

更新约束，但只会更新<u>约束对象</u>与原来约束一直的约束，否则会导致约束冲突问题





##### 控件利用Masonry添加约束之后 不能立刻获取到该控件的尺寸

```objective-c
[view layoutIfNeeded];
```

