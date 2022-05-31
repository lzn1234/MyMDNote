使用malloc或calloc需要导入<stdlib.h>库



使用bool类型需要导入<stdbool.h>库



###### 使用calloc函数来创建有默认初始值的数组 <stdlib.h>

C 库函数 **void \*calloc(size_t nitems, size_t size)** ：分配所需的内存空间，并返回一个指向它的指针。**malloc** 和 **calloc** 之间的不同点是，malloc 不会设置内存为零，而 calloc 会设置分配的内存为零。

```C
int *a = (int*)calloc(n, sizeof(int));
```



###### 该函数将其他类型转化为字符串<string.h>

C 库函数 **int sprintf(char \*str, const char \*format, value)** 发送格式化输出到 **str** 所指向的字符串。



###### 拼接字符串<stdlib.h>

C 库函数 **char \*strcat(char \*dest, const char \*src)** 把 **src** 所指向的字符串追加到 **dest** 所指向的字符串的结尾。



###### 把参数 *str* 所指向的字符串转换为一个整数（类型为 int 型）<stdlibh.>

##### int atoi(const char *str)

