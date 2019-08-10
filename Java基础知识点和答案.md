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
# 1.3  short s1 = 1; s1 = s1 + 1;有什么错? short s1 = 1; s1 +=1;有什么错?

- 对于short s1=1;s1=s1+1来说，在s1+1运算时会自动提升表达式的类型为int，那么将int赋予给short类型的变量s1会出现类型转换错误。
- 对于short s1=1;s1+=1来说 +=是java语言规定的运算符，java编译器会对它进行特殊处理，因此可以正确编译。

# 1.4 int和Integer的区别

https://www.cnblogs.com/guodongdidi/p/6953217.html

- Integer是int的包装类，int则是java的一种基本数据类型 
- Integer变量必须实例化后才能使用，而int变量不需要 
- Integer实际是对象的引用，当new一个Integer时，实际上是生成一个指针指向此对象；而int则是直接存储数据值 
- Integer的默认值是null，int的默认值是0

延伸： 
关于Integer和int的比较 
1、由于Integer变量实际上是对一个Integer对象的引用，所以两个通过new生成的Integer变量永远是不相等的（因为new生成的是两个对象，其内存地址不同）。
```
Integer i = new Integer(100);
Integer j = new Integer(100);
System.out.print(i == j); //false
``` 
2、Integer变量和int变量比较时，只要两个变量的值是向等的，则结果为true（因为包装类Integer和基本数据类型int比较时，java会自动拆包装为int，然后进行比较，实际上就变为两个int变量的比较）
```
Integer i = new Integer(100);
int j = 100；
System.out.print(i == j); //true
```
3、非new生成的Integer变量和new Integer()生成的变量比较时，结果为false。（因为非new生成的Integer变量指向的是java常量池中的对象，而new Integer()生成的变量指向堆中新建的对象，两者在内存中的地址不同）
```
Integer i = new Integer(100);
Integer j = 100;
System.out.print(i == j); //false
```
4、对于两个非new生成的Integer对象，进行比较时，如果两个变量的值在区间-128到127之间，则比较结果为true，如果两个变量的值不在此区间，则比较结果为false
```
Integer i = 100;
Integer j = 100;
System.out.print(i == j); //true
Integer i = 128;
Integer j = 128;
System.out.print(i == j); //false
```
对于第4条的原因： 
java在编译Integer i = 100 ;时，会翻译成为Integer i = Integer.valueOf(100)；，而java API中对Integer类型的valueOf的定义如下：
```
public static Integer valueOf(int i){
    assert IntegerCache.high >= 127;
    if (i >= IntegerCache.low && i <= IntegerCache.high){
        return IntegerCache.cache[i + (-IntegerCache.low)];
    }
    return new Integer(i);
}
```
java对于-128到127之间的数，会进行缓存，Integer i = 127时，会将127进行缓存，下次再写Integer j = 127时，就会直接从缓存中取，就不会new了
