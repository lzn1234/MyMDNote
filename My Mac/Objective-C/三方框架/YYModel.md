#### 框架导入

pod 导入框架

```swift
pod "YYModel"
```

引入头文件

```swift
#import "YYModel.h"
```

#### 框架使用

Model 和 JSON 数据的相互转换

```objective-c
// JSON 转 Model
+ (instancetype)yy_modelWithDictionary:(NSDictionary *)dictionary;
  
// Model 转 JSON
- (id)yy_modelToJSONObject;
```

当 Model 对象中的属性名和 JSON 中的 key 不一致，你需要调用该方法来关联二者

```objective-c
+ (NSDictionary *)modelCustomPropertyMapper {
 		return @{
       @"modelName":@"jsonName"
    }
}

```

当 Model 对象中包含 Model 对象时，使用以下方法返回一个 [属性名: 类] 的字典

```objective-c
+ (NSDictionary *)modelContainerPropertyGenericClass {
    return @{
        @"results" : [ModelClassName class]
    };
}
```

