语法更清晰

代码的可读性、可维护性、安全性都比OC强

代码的运行效率更高







swift 的变量在使用前必须被初始化

字面量数字类型可以进行高精度向低精度的转化 Double ->Float->Int

**一个变量或者常量如何确定它的类型，一种是有我们对变量进行类型注解，还有一种是swift 根据赋值的类型 进行类型推断来确定自己的类型**

**swift 是类型安全的语言，它会在代码编译时检查变量或常量的类型，然后把不符合的标记出来**

**swift 没有隐式的类型转换，只能使用提供的方法进行类型强转，并要处理某些可选类型的返回值**

**swift 提供可选类型来明确的处理nil**

swift 使用 ARC（Automatic Reference Counting）来进行内存管理

swift 细化了权限访问控制，open，public，internal（默认），fileprivate，private



//可读性，易维护

swift 比 OC 更加精简，移除了 .h 文件以及头文件的导入，这样也提高了 swift 语言的性能

swift 报错提示更加人性化，直接显示在错误行

变量常量定义更简单，使用 let var

函数式编程

支持代码预览 playground



swift 值类型和引用类型

值类型：值类型一般存储在栈中，进行赋值或者方法传值操作时，它都会进行一个深拷贝，将新开辟的空间用作赋值或者方法传值



引用类型：一般存储在堆上，本质是指针，所以赋值操作进行的是浅拷贝，使得两个指针指向同一个内存空间



C: class 类
T: typedef 通常是枚举类别的定义
E：enum 枚举
Pr：protocol 协议
M：method 方法
V：value 值
P: property 属性
K: 枚举 、常量
G: global全局变量
f: 函数
#: #define指令

