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
# 1.5 字节和字符的区别
字节是存储容量的基本单位，字符是数子，字母，汉子以及其他语言的各种符号。1字节=8个二进制单位：一个一个字符由一个字节或多个字节的二进制单位组成。
# 1.6 基本类型和引用类型的区别
基本类型保存原始值，引用类型保存的是引用值（引用值就是指对象在堆中所处的位置/地址）
# 1.7 Java的四个基本特性及多态的理解？
![](http://ww1.sinaimg.cn/large/007s8HJUly1g5w2pliuhij30js0b8n1z.jpg)
# 1.8 重载和重写的区别？
## 1.8.1 重载

https://blog.csdn.net/cey009008/article/details/46331619

 重载（overload），Java中的方法重载发生在同一个类里面两个或者是多个方法的方法名相同但是参数不同的情况。
-1.可以在一个类中也可以在继承关系的类中；  
-2.名相同；  
- 3.参数列表不同（个数，顺序，类型） 和方法的返回值类型无关。
## 1.8.2 重写
重写（override)又名覆盖，方法覆盖是说子类重新定义了父类的方法。方法覆盖必须有相同的方法名，参数列表和返回类型。覆盖者可能不会限制它所覆盖的方法的访问。: 
- 1.不能存在同一个类中，在继承或实现关系的类中；  
- 2.名相同，参数列表相同，方法返回值相同，  
- 3.子类方法的访问修饰符要大于父类的。  
- 4.子类的检查异常类型要小于父类的检查异常。  
# 1.9 Java中是否可以覆盖(override)一个private或者是static的方法？
Java中static方法不能被覆盖，因为方法覆盖是基于运行时动态绑定的，而static方法是编译时静态绑定的。static方法跟类的任何实例都不相关，所以概念上不适用。java中也不可以覆盖private的方法，因为private修饰的变量和方法只能在当前类中使用，如果是其他的类继承当前类是不能访问到private变量或方法的，当然也不能覆盖。
# 1.10 面向对象的六个基本原则
![](http://ww1.sinaimg.cn/large/007s8HJUly1g5w39fm22gj30vw0hy13y.jpg)
# 1.11 Java 创建对象的四种方式
https://www.cnblogs.com/yunche/p/9530927.html
- 1.使用new创建对象
使用new关键字创建对象应该是最常见的一种方式，但我们应该知道，使用new创建对象会增加耦合度。无论使用什么框架，都要减少new的使用以降低耦合度。
- 2.使用反射的机制创建对象
使用Class类的newInstance方法
- 3.采用clone
clone时，需要已经有一个分配了内存的源对象，创建新对象时，首先应该分配一个和源对象一样大的内存空间。要调用clone方法需要实现Cloneable接口
- 4.采用序列化机制
使用序列化时，要实现实现Serializable接口，将一个对象序列化到磁盘上，而采用反序列化可以将磁盘上的对象信息转化到内存中。
# 1.12 String、StringBuffer和StringBuilder的区别
![](http://ww1.sinaimg.cn/large/007s8HJUly1g5w4mh9b0zj30ur06pn0z.jpg)
![](http://ww1.sinaimg.cn/large/007s8HJUly1g5w4mlg6vej30fe016aa8.jpg)
# 1.13 String不可变好处
![](http://ww1.sinaimg.cn/large/007s8HJUly1g5w4oo4m9qj30q60cln0f.jpg)
![](http://ww1.sinaimg.cn/large/007s8HJUly1g5w4osa6aij30fe03pgmi.jpg)

# 1.14 String Pool

https://github.com/gzc426/CS-Notes/edit/master/docs/notes/Java%20%E5%9F%BA%E7%A1%80.md

字符串常量池（String Pool）保存着所有字符串字面量（literal strings），这些字面量在编译时期就确定。不仅如此，还可以使用 String 的 intern() 方法在运行过程中将字符串添加到 String Pool 中。

当一个字符串调用 intern() 方法时，如果 String Pool 中已经存在一个字符串和该字符串值相等（使用 equals() 方法进行确定），那么就会返回 String Pool 中字符串的引用；否则，就会在 String Pool 中添加一个新的字符串，并返回这个新字符串的引用。

下面示例中，s1 和 s2 采用 new String() 的方式新建了两个不同字符串，而 s3 和 s4 是通过 s1.intern() 方法取得一个字符串引用。intern() 首先把 s1 引用的字符串放到 String Pool 中，然后返回这个字符串引用。因此 s3 和 s4 引用的是同一个字符串。

```java
String s1 = new String("aaa");
String s2 = new String("aaa");
System.out.println(s1 == s2);           // false
String s3 = s1.intern();
String s4 = s1.intern();
System.out.println(s3 == s4);           // true
```

如果是采用 "bbb" 这种字面量的形式创建字符串，会自动地将字符串放入 String Pool 中。

```java
String s5 = "bbb";
String s6 = "bbb";
System.out.println(s5 == s6);  // true
```

在 Java 7 之前，String Pool 被放在运行时常量池中，它属于永久代。而在 Java 7，String Pool 被移到堆中。这是因为永久代的空间有限，在大量使用字符串的场景下会导致 OutOfMemoryError 错误。

- [StackOverflow : What is String interning?](https://stackoverflow.com/questions/10578984/what-is-string-interning)
- [深入解析 String#intern](https://tech.meituan.com/in_depth_understanding_string_intern.html)

# 1.15 new String("abc")

使用这种方式一共会创建两个字符串对象（前提是 String Pool 中还没有 "abc" 字符串对象）。

- "abc" 属于字符串字面量，因此编译时期会在 String Pool 中创建一个字符串对象，指向这个 "abc" 字符串字面量；
- 而使用 new 的方式会在堆中创建一个字符串对象。

创建一个测试类，其 main 方法中使用这种方式来创建字符串对象。

```java
public class NewStringTest {
    public static void main(String[] args) {
        String s = new String("abc");
    }
}
```

使用 javap -verbose 进行反编译，得到以下内容：

```java
// ...
Constant pool:
// ...
   #2 = Class              #18            // java/lang/String
   #3 = String             #19            // abc
// ...
  #18 = Utf8               java/lang/String
  #19 = Utf8               abc
// ...

  public static void main(java.lang.String[]);
    descriptor: ([Ljava/lang/String;)V
    flags: ACC_PUBLIC, ACC_STATIC
    Code:
      stack=3, locals=2, args_size=1
         0: new           #2                  // class java/lang/String
         3: dup
         4: ldc           #3                  // String abc
         6: invokespecial #4                  // Method java/lang/String."<init>":(Ljava/lang/String;)V
         9: astore_1
// ...
```

在 Constant Pool 中，#19 存储这字符串字面量 "abc"，#3 是 String Pool 的字符串对象，它指向 #19 这个字符串字面量。在 main 方法中，0: 行使用 new #2 在堆中创建一个字符串对象，并且使用 ldc #3 将 String Pool 中的字符串对象作为 String 构造函数的参数。

以下是 String 构造函数的源码，可以看到，在将一个字符串对象作为另一个字符串对象的构造函数参数时，并不会完全复制 value 数组内容，而是都会指向同一个 value 数组。

```java
public String(String original) {
    this.value = original.value;
    this.hash = original.hash;
}
```
# 1.16 String中的hashcode以及toString
![](http://ww1.sinaimg.cn/large/007s8HJUly1g5w4sq64ymj30xf0bvtfd.jpg)
