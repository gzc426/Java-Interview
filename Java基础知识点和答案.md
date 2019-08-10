# 1.1. Java 8种基本类型有哪些？
Byte  short  int  long float  double  boolean  char

![](https://ws4.sinaimg.cn/large/006Xmmmgly1g5v04dixr0j30d80ck0uu.jpg)

# 1.2 什么是装箱和拆箱？
装箱就是  自动将基本数据类型转换为包装器类型；拆箱就是  自动将包装器类型转换为基本数据类型。
比如：把int转化成Integer，double转化成Double，等等。反之就是自动拆箱。
- 原始类型: boolean，char，byte，short，int，long，float，double
- 封装类型：Boolean，Character，Byte，Short，Integer，Long，Float，Double
- 示例：
```
Integer i = 10;
这个过程中会自动根据数值创建对应的 Integer对象，这就是装箱。
那什么是拆箱呢？顾名思义，跟装箱对应，就是自动将包装器类型转换为基本数据类型：
Integer i = 10;  //装箱
int n = i;   //拆箱
```
