一java基础
==========

1.1java的8种基本数据类型 装箱 拆箱
----------------------------------

*https://blog.csdn.net/daidaineteasy/article/details/51088269*

### 1.1.1．8种基本数据类型

Byte short int long float double boolean char

![](media/image1.png){width="4.957638888888889in"
height="4.707638888888889in"}

###  1.1.2．装箱和拆箱

自动装箱是Java编译器在基本数据类型和对应的对象包装类型之间做的一个转化。比如：把int转化成Integer，double转化成Double，等等。反之就是自动拆箱。

原始类型: boolean，char，byte，short，int，long，float，double

封装类型：Boolean，Character，Byte，Short，Integer，Long，Float，Double

###  1.1.3．String 转出 int型，判断能不能转？如何转？

答：可以转，得处理异常 Integer.parseInt(s)
主要为NumberFormatException：1）当你输入为字母时，也就是内容不是数字时，如abcd
2）当你输入为空时3）当你输入超出int上限时
 Long.parseLong("123")转换为long

### 1.1.4 short s1 = 1; s1 = s1 + 1;有什么错? short s1 = 1; s1 +=1;有什么错?

> 1\) 对于short
> s1=1;s1=s1+1来说，在s1+1运算时会自动提升表达式的类型为int，那么将int赋予给short类型的变量s1会出现类型转换错误。
>
> 2\) 对于short s1=1;s1+=1来说
> +=是java语言规定的运算符，java编译器会对它进行特殊处理，因此可以正确编译。

###  1.1.5．Int与Integer区别

*https://www.cnblogs.com/guodongdidi/p/6953217.html*
![](media/image2.png){width="5.768055555555556in"
height="5.2444444444444445in"}

![](media/image3.png){width="5.761805555555555in"
height="1.7416666666666667in"}

### *1.1.6*．字节字符区别

> 字节是存储容量的基本单位，字符是数子，字母，汉子以及其他语言的各种符号。1字节=8个二进制单位：一个一个字符由一个字节或多个字节的二进制单位组成。

###  1.1.7 java基本类型与引用类型的区别

> 基本类型保存原始值，引用类型保存的是引用值（引用值就是指对象在堆中所处的位置/地址）

1.2重写重载封装继承多态
-----------------------

![](media/image4.png){width="5.768055555555556in"
height="3.2729166666666667in"}

一．继承的好处和坏处

> 好处：1. 子类能自动继承父类的接口
>
> 2\. 创建子类的对象时，无须创建父类的对象
>
> 坏处:1.
> 破坏封装，子类与父类之间紧密耦合，子类依赖于父类的实现，子类缺乏独立性
>
> 2\. 支持扩展，但是往往以增加系统结构的复杂度为代价
>
> 3\. 不支持动态继承。在运行时，子类无法选择不同的父类
>
> 4\. 子类不能改变父类的接口

二．重载、重写

Java中的方法重载发生在同一个类里面两个或者是多个方法的方法名相同但是参数不同的情况。与此相对，方法覆盖是说子类重新定义了父类的方法。方法覆盖必须有相同的方法名，参数列表和返回类型。覆盖者可能不会限制它所覆盖的方法的访问。

![](media/image5.png){width="5.768055555555556in"
height="0.7472222222222222in"}

*https://blog.csdn.net/cey009008/article/details/46331619*

> 重写（override)又名覆盖: \
> 1.不能存在同一个类中，在继承或实现关系的类中； \
> 2. 名相同，参数列表相同，方法返回值相同， \
> 3.子类方法的访问修饰符要大于父类的。 \
> 4.子类的检查异常类型要小于父类的检查异常。 \
>  重载（overload） \
> 1.可以在一个类中也可以在继承关系的类中； \
> 2.名相同； \
> 3.参数列表不同（个数，顺序，类型） 和方法的返回值类型无关。
>
> 三．Java中是否可以覆盖(override)一个private或者是static的方法？

Java中static方法不能被覆盖，因为方法覆盖是基于运行时动态绑定的，而static方法是编译时静态绑定的。static方法跟类的任何实例都不相关，所以概念上不适用。

java中也不可以覆盖private的方法，因为private修饰的变量和方法只能在当前类中使用，如果是其他的类继承当前类是不能访问到private变量或方法的，当然也不能覆盖。

1.3 Stack Queue
---------------

###  1.3.1 PriorityQueue

> PriorityQueue是一个基于优先级堆的无界队列，它的元素是按照自然顺序(natural
> order)排序的。在创建的时候，我们可以给它提供一个负责给元素排序的比较器。PriorityQueue不允许null值，因为他们没有自然顺序，或者说他们没有任何的相关联的比较器。最后，PriorityQueue不是线程安全的，入队和出队的时间复杂度是O(log(n))。

堆树的定义如下：

> （1）堆树是一颗完全二叉树；
>
> （2）堆树中某个节点的值总是不大于或不小于其孩子节点的值；
>
> （3）堆树中每个节点的子树都是堆树。

**1.原理**

*https://www.cnblogs.com/CarpenterLee/p/5488070.html *

孩子节点的下标例如下标2 5 6 （5-1）/2=2 (6-1)/2=2
每个父节点的值都比孩子节点的值要比孩子节点的值要小。

![](media/image6.png){width="5.768055555555556in"
height="4.495833333333334in"}

1.  **添加元素add()和offer()**

> 原理：添加元素位于末尾，同时队列长度加1，然后这个元素与它的父节点进行比较，如果比父节点小那么就与父节点进行交换，然后再与交换后的位置的父节点进行比较，重复这个过程，直到该元素的值大于父节点结束这个过程。
>
> 区别: add(E e)和offer(E
> e)的语义相同，都是向优先队列中插入元素，只是Queue接口规定二者对插入失败时的处理不同，前者在插入失败时抛出异常，后则则会返回false。对于*PriorityQueue*这两个方法其实没什么差
>
> ![](media/image7.png){width="5.768055555555556in"
> height="4.7555555555555555in"}

1.  **寻找队列的头部元素element()和peek()头部元素 时间复杂度为1**

> element()和peek()的语义完全相同，都是获取但不删除队首元素，也就是队列中权值最小的那个元素，二者唯一的区别是当方法失败时前者抛出异常，后者返回null。根据小顶堆的性质，堆顶那个元素就是全局最小的那个；由于堆用数组表示，根据下标关系，0下标处的那个元素既是堆顶元素。所以**直接返回数组0下标处的那个元素即可**。

**4.删除元素 remove() 和poll()**

> 区别:remove()和poll()方法的语义也完全相同，都是获取并删除队首元素，区别是当方法失败时前者抛出异常，后者返回null。由于删除操作会改变队列的结构，为维护小顶堆的性质，需要进行必要的调整。
>
> 原理：该方法的作用是从k指定的位置开始，将x逐层向下与当前点的左右孩子中较小的那个交换，直到x小于或等于左右孩子中的任何一个为止
>
> ![](media/image8.png){width="5.768055555555556in"
> height="4.881944444444445in"}

1.  **最大堆 获取数组中最小的几个数 最小堆 获取数组中最大的几个数**

> ![](media/image9.png){width="5.768055555555556in"
> height="4.627777777777778in"}
>
> 上述代码是构建最大堆，最大堆的栈顶是堆的最大的元素，最大的元素比数组中任意一个元素小，说明了最大堆这些元素是数组中最小的几个元素。
>
> 上述代码为何需要重现写比较器函数compare()???
>
> 答：需要查看优先队列的源码，如下源码所示，添加元素需要比较新的元素与父节点的元素，
>
> 如果比较器比较结果大等于0，那么结束添加过程添加完成，说明在构建最大堆时候，要想使得元素是对父节点的元素小才结束循环，那么必须重新写比较器函数，调换两者的比较顺序即可。
>
> 最小堆，与上述过程相反。
>
> ![](media/image10.png){width="4.968055555555556in"
> height="2.9159722222222224in"}

![](media/image11.png){width="5.768055555555556in"
height="2.107638888888889in"}

 

1.7 Concurrent包
----------------

Concurrent包里的其他东西：ArrayBlockingQueue、CountDownLatch等等

![C:\\Users\\GZC\\AppData\\Roaming\\Tencent\\Users\\990878733\\TIM\\WinTemp\\RichOle\\OWMAWI2DQ\`3F9\]7Z\]WBK3XH.png](media/image12.png){width="5.768055555555556in"
height="0.8298611111111112in"}

![C:\\Users\\GZC\\AppData\\Roaming\\Tencent\\Users\\990878733\\TIM\\WinTemp\\RichOle\\Z\]Q%\])RA\`6XVQV\$R%MM91\`D.png](media/image13.png){width="5.772916666666666in"
height="1.3118055555555554in"}

1.8面向对象
-----------

![](media/image14.png){width="5.768055555555556in"
height="3.245833333333333in"}

![](media/image15.png){width="5.757638888888889in"
height="2.084722222222222in"}

面向对象特点、C++Java面向对象设计的不同、

面向对象的设计规范

对面向对象的认识

面向对象的特征

1.9 String StringBuffer StringBuilder hashcode equal
----------------------------------------------------

一．String StringBuffer StringBuilder的区别

![](media/image16.png){width="5.768055555555556in"
height="1.2555555555555555in"}

![](media/image17.png){width="5.768055555555556in"
height="0.43194444444444446in"}

二．String不可变？

![](media/image18.png){width="5.768055555555556in"
height="2.7736111111111112in"}

![](media/image19.png){width="5.768055555555556in"
height="1.3805555555555555in"}

[]{#_Toc778 .anchor}String中的hashcode以及toString

![](media/image20.png){width="5.768055555555556in"
height="2.047222222222222in"}

![](media/image21.png){width="5.768055555555556in" height="2.08125in"}

使用场景

四．String，是否可以继承，“+”怎样实现，与StringBuffer区别

![](media/image22.png){width="5.768055555555556in"
height="0.37083333333333335in"}

1.10 java 文件读取
------------------

![](media/image23.png){width="5.7625in" height="3.140277777777778in"}

1.11 Java反射
-------------

![](media/image24.png){width="5.767361111111111in"
height="2.9097222222222223in"}

![](media/image25.png){width="5.7659722222222225in"
height="4.322222222222222in"}

Java反射的概念和应用场景

反射机制中可以获取private成员的值吗（没有set和get函数）可以

 反射的所有包，怎实现反射

> 反射的定义
>
> Java.long.reflect 里常用方法

1.12 JDK NDK JRE JNI
--------------------

1.JDK与JRE的区别

Java运行时环境(JRE)。它包括Java虚拟机、Java核心类库和支持文件。它不包含开发工具（JDK）--编译器、调试器和其他工具。

Java开发工具包(JDK)是完整的Java软件开发包，包含了JRE，编译器和其他的工具(比如：JavaDoc，Java调试器)，可以让开发者开发、编译、执行Java应用程序。

2.  版本特性

![](media/image26.png){width="5.759027777777778in"
height="3.1416666666666666in"}

JDK中哪些体现了命令模式

JDK发展

了解**NDK**吗？他和JDK有什么区别呢？

使用过JNI么？NDK技术使用过哪些呢？

1.13 static 和final的区别
-------------------------

![](media/image27.png){width="5.763194444444444in"
height="2.1847222222222222in"}

**final的好处：**

1.  final关键字提高了性能。JVM和Java应用都会缓存final变量。

2.  final变量可以安全的在多线程环境下进行共享，而不需要额外的同步开销。

3.  使用final关键字，JVM会对方法、变量及类进行优化。

<!-- -->

1.  **static方法是否可以覆盖？**

static方法不能被覆盖，因为方法覆盖是基于运行时动态绑定的，而static方法是编译时静态绑定的。static方法跟类的任何实例都不相关，所以概念上不适用。

**二．是否可以在static环境中访问非static变量？**

static修饰的变量并发下怎么保证变量的安全

static修饰的变量什么时候赋值

static什么时候使用

class A {\
private static A *a*=new A();\
static{\
System.*out*.print("static");\
}\
public A(){\
System.*out*.print("A");\
}\
}\
public class B extends A{\
public B(){\
System.*out*.print("B");\
}\
public static void main(String\[\] args) {\
B b=new B();\
}\
}

上述运行结果 AstaticAB

class A {\
private static A *a*=new A();\
static{\
System.*out*.print("static");\
}\
{\
System.*out*.print("A");\
}\
}\
public class B extends A{\
public B(){\
System.*out*.print("B");\
}\
public static void main(String\[\] args) {\
B b=new B();\
}\
}

上述结果也是AstaticAB 匿名构造器
构造器先与静态代码块执行，静态代码块只执行一次

class A {\
public A(){\
System.*out*.print("A gouzhao");\
}\
private static A *a*=new A();\
static{\
System.*out*.print("static");\
}\
{\
System.*out*.print("A1");\
}\
}\
public class B extends A{\
public B(){\
System.*out*.print("B");\
}\
public static void main(String\[\] args) {\
System.*out*.println("0000");\
B b=new B();\
}\
}

运行结果：A1A gouzhaostatic0000

A1A gouzhaoB

**解释：静态变量，静态代码块先于System.out.println(“0000”)执行，静态的东西只执行一次，相当于全局变量。**

1.14 map，list，set区别
-----------------------

有哪些类，这些类有什么区别

1.16 Session和COOKIE
--------------------

1.session和cookie区别

![](media/image28.png){width="5.7625in" height="1.5875in"}

cookie是Web服务器发送给浏览器的一块信息。浏览器会在本地文件中给每一个Web服务器存储cookie。以后浏览器在给特定的Web服务器发请求的时候，同时会发送所有为该服务器存储的cookie。下面列出了session和cookie的区别：\
无论客户端浏览器做怎么样的设置，session都应该能正常工作。客户端可以选择禁用cookie，但是，session仍然是能够工作的，因为客户端无法禁用服务端的session。\
在存储的数据量方面session和cookies也是不一样的。session能够存储任意的Java对象，cookie只能存储String类型的对象。

服务器端Session的保存

Cookie和session区别

session在服务器上以怎样的形式存在session持久化

怎么设置session和cookie的有效时间

> Session的实现原理和应用场景 Session原理;
> 既然Session是存储在服务器内存的,
> 如果服务器的负载量很高内存负荷不住要怎么办?

1.19 IO NIO BIO AIO select epoll
--------------------------------

![](media/image29.png){width="5.768055555555556in"
height="2.047222222222222in"}

![](media/image30.png){width="5.760416666666667in"
height="2.8270833333333334in"}

![](media/image31.png){width="5.760416666666667in"
height="0.5993055555555555in"}

![](media/image32.png){width="5.764583333333333in"
height="1.4270833333333333in"}

![](media/image33.png){width="5.761805555555555in"
height="0.3840277777777778in"}

![](media/image34.png){width="5.7625in" height="0.40902777777777777in"}

什么是阻塞和非阻塞，什么是同步和异步,同步和异步是针对应用程序和内核的交互而言的，同步指的是用户进程触发IO操作并等待或者轮询的去查看IO操作是否就绪，而异步是指用户进程触发IO操作以后便开始做自己的事情，而当IO操作已经完成的时候会得到IO完成的通知。而阻塞和非阻塞是针对于进程在访问数据的时候，根据IO操作的就绪状态来采取的不同方式，说白了是一种读取或者写入操作函数的实现方式，阻塞方式下读取或者写入函数将一直等待，而非阻塞方式下，读取或者写入函数会立即返回一个状态值。

 一般来说I/O模型可以分为：同步阻塞，同步非阻塞，异步阻塞，异步非阻塞IO

同步阻塞IO：在此种方式下，用户进程在发起一个IO操作以后，必须等待IO操作的完成，只有当真正完成了IO操作以后，用户进程才能运行。JAVA传统的IO模型属于此种方式！

同步非阻塞IO:在此种方式下，用户进程发起一个IO操作以后边可返回做其它事情，但是用户进程需要时不时的询问IO操作是否就绪，这就要求用户进程不停的去询问，从而引入不必要的CPU资源浪费。其中目前JAVA的NIO就属于同步非阻塞IO。

异步阻塞IO：此种方式下是指应用发起一个IO操作以后，不等待内核IO操作的完成，等内核完成IO操作以后会通知应用程序，这其实就是同步和异步最关键的区别，同步必须等待或者主动的去询问IO是否完成，那么为什么说是阻塞的呢？因为此时是通过select系统调用来完成的，而select函数本身的实现方式是阻塞的，而采用select函数有个好处就是它可以同时监听多个文件句柄，从而提高系统的并发性！

 异步非阻塞IO:在此种模式下，用户进程只需要发起一个IO操作然后立即返回，等IO操作真正的完成以后，应用程序会得到IO操作完成的通知，此时用户进程只需要对数据进行处理就好了，不需要进行实际的IO读写操作，因为真正的IO读取或者写入操作已经由内核完成了。

[]{#_Toc2158 .anchor}**1.19.1 NIO的原理**

![](media/image35.png){width="5.7625in" height="3.4090277777777778in"}

![](media/image36.png){width="5.7659722222222225in"
height="3.9715277777777778in"}

NIO的DirectByteBuffer和HeapByteBuffer

.IO哪个类可以Byte转String。

 java
NIO的实现原理，我给他将了阻塞非阻塞，同步异步，Buffer与Channel以及Selector的运行机制，然后又问NIO主要解决的是什么问题

1.20 ThreadLocal
----------------

![](media/image37.png){width="5.7625in" height="4.975in"}

当使用ThreadLocal维护变量时，ThreadLocal为每个使用该变量的线程提供独立的变量副本，所以每一个线程都可以独立地改变自己的副本，而不会影响其它线程所对应的副本。

1.22 finalize finalization finally
----------------------------------

1.  **finalize用途**

答：垃圾回收器(garbage
colector)决定回收某对象时，就会运行该对象的finalize()方法
但是在Java中很不幸，如果内存总是充足的，那么垃圾回收可能永远不会进行，也就是说filalize()可能永远不被执行，显然指望它做收尾工作是靠不住的。
那么finalize()究竟是做什么的呢？它最主要的用途是回收特殊渠道申请的内存。Java程序有垃圾回收器，所以一般情况下内存问题不用程序员操心。但有一种JNI(Java
Native
Interface)调用non-Java程序（C或C++），finalize()的工作就是回收这部分的内存。

**二．finally**

![](media/image38.png){width="5.7659722222222225in"
height="0.7923611111111111in"}

finally 一定会被执行，如果 finally 里有 return 语句，则覆盖 try/catch
里的 return ，

比较爱考的是 finally 里没有 return 语句，这时虽然 finally 里对 return
的值进行了修改，但 return 的值并不改变这种情况

> **三．finally代码块和finalize()方法有什么区别？**

无论是否抛出异常，finally代码块都会执行，它主要是用来释放应用占用的资源。finalize()方法是Object类的一个protected方法，它是在对象被垃圾回收之前由Java虚拟机来调用的。

．

1.23 public private default protected
-------------------------------------

访问修饰符作用域

![](media/image39.png){width="5.768055555555556in" height="2.3in"}

不写时默认为default。默认对于同一个包中的其他类相当于公开（public），对于不是同一个包中的其他类相当于私有（private）。受保护（protected）对子类相当于公开，对不是同一包中的没有父子关系的类相当于私有。

不可以覆盖private的方法，因为private修饰的变量和方法只能在当前类中使用，如果是其他的类继承当前类是不能访问到private变量或方法的，当然也不能覆

1.25 Object
-----------

hashcode() equals() toString() getClass()

wait notify() notifyAll()

finalize()

1.26 equls 和 == 的区别
-----------------------

*https://blog.csdn.net/love\_xsq/article/details/43760771*
![](media/image40.png){width="5.768055555555556in"
height="1.0847222222222221in"}

StringBuffer 和StringBuilder特殊，==和equal都是比较地址

1.27 异常
---------

**Java中的两种异常类型是什么？他们有什么区别？**

答：Java中有两种异常：受检查的(checked)异常和不受检查的(unchecked)异常。不受检查的异常不需要在方法或者是构造函数上声明，就算方法或者是构造函数的执行可能会抛出这样的异常，并且不受检查的异常可以传播到方法或者是构造函数的外面。相反，受检查的异常必须要用throws语句在方法或者是构造函数上声明。

**throw和throws有什么区别？**

throw关键字用来在程序中明确的抛出异常，相反，throws语句用来表明方法不能处理的异常。每一个方法都必须要指定哪些异常不能处理，所以方法的调用者才能够确保处理可能发生的异常，多个异常是用逗号分隔的。

java提供了两种异常机制。一种是运行时异常(RuntimeExepction)，一种是检查式异常(checked
execption)。

检查式异常：我们经常遇到的IO异常及sql异常就属于检查式异常。对于这种异常，java编译器要求我们必须对出现的这些异常进行catch
所以 面对这种异常不管我们是否愿意，只能自己去写一堆catch来捕捉这些异常。

运行时异常(未受检）：我们可以不处理。当出现这样的异常时，总是由虚拟机接管。比如：我们从来没有人去处理过NullPointerException异常，它就是运行时异常，并且这种异常还是最常见的异常之一。

![](media/image41.png){width="5.767361111111111in"
height="2.4520833333333334in"}![https://img-blog.csdn.net/20131229102433281?watermark/2/text/aHR0cDovL2Jsb2cuY3Nkbi5uZXQvY2hlbnNzeQ==/font/5a6L5L2T/fontsize/400/fill/I0JBQkFCMA==/dissolve/70/gravity/SouthEast](media/image42.png){width="5.767361111111111in"
height="5.8694444444444445in"}

ClassCastException(类转换异常) \
IndexOutOfBoundsException(数组越界) \
NullPointerException(空指针) \
ArrayStoreException(数据存储异常，操作数组时类型不一致) 

未检查异常和已检查异常

Java的异常处理机制, 说说受检异常和运行时异常的区别并举例

**Java 异常体系描述一下**

1.28 序列化
-----------

![](media/image43.png){width="5.768055555555556in"
height="2.8069444444444445in"}

![](media/image44.png){width="5.768055555555556in" height="1.30625in"}

![](media/image45.png){width="5.760416666666667in"
height="0.6694444444444444in"}

![](media/image46.png){width="5.768055555555556in"
height="3.4618055555555554in"}

![](media/image47.png){width="5.768055555555556in"
height="2.339583333333333in"}

![](media/image48.png){width="5.767361111111111in" height="4.0625in"}

序列化，以及json传输

1.30 comparable接口和comparator接口
-----------------------------------

comparable接口和comparator接口实现比较的区别和用法

**1.定义**

Comparable接口：使用Array或Collection的排序方法时，自定义类需要实现Java提供Comparable接口的compareTo(TOBJ)方法，它被排序方法所使用，应该重写这个方法，如果“this”对象比传递的对象参数更小、相等或更大时，它返回一个负整数、0或正整数。

使用Comparator接口的情景：在大多数实际情况下，我们想根据不同参数进行排序。比如，作为一个CEO，我想对雇员基于薪资进行排序，一个HR想基于年龄对他们进行排序。这就是我们需要使用Comparator接口的情景。因为Comparable.compareTo(Object
o)方法实现只能基于一个字段进行排序，不能根据需要选择对象字段来对对象进行排序。

Comparator接口：可以实现两个对象的特定字段的比较（比如，比较员工这个对象的年龄），该接口的compare(Objecto1,
Object
o2)方法的实现需要传递两个对象参数，若第一个参数小于、等于、大于第二个参数，返回负整数、0、正整数。

**2. comparable接口和comparator接口区别**

> Comparable和Comparator接口被用来对对象集合或者数组进行排序。
>
> Comparable接口被用来提供对象的自然排序，可使用它来提供基于单个逻辑的排序。
>
> Comparator接口被用来提供不同的排序算法，可根据制定字段选择需要使用的Comparator来对指定的对象集合进行排序。

1.33 接口和抽象类
-----------------

1.接口和抽象类的区别 

> 1，抽象类里可以有构造方法，而接口内不能有构造方法。
>
> 2，抽象类中可以有普通成员变量，而接口中不能有普通成员变量。
>
> 3，抽象类中可以包含非抽象的普通方法，而接口中所有的方法必须是抽象的，不能有非抽象的普通方法。
>
> 4，抽象类中的抽象方法的访问类型可以是public
> ，protected和private，但接口中的抽象方法只能是public类型的，并且默认即为public
> abstract类型。
>
> 5，抽象类中可以包含静态方法，接口内不能包含静态方法。
>
> 6，抽象类和接口中都可以包含静态成员变量，抽象类中的静态成员变量的访问类型可以任意，但接口中定义的变量只能是public
> static类型，并且默认为public static final类型。
>
> 7，一个类可以实现多个接口，但只能继承一个抽象类。
>
> 1\. Java抽象类可以有构造函数吗？
>
> 可以有，抽象类可以声明并定义构造函数。因为你不可以创建抽象类的实例，所以构造函数只能通过构造函数链调用（Java中构造函数链指的是从其他构造函数调用一个构造函数），例如，当你创建具体的实现类。现在一些面试官问，如果你不能对抽象类实例化那么构造函数的作用是什么？好吧，它可以用来初始化抽象类内部声明的通用变量，并被各种实现使用。另外，即使你没有提供任何构造函数，编译器将为抽象类添加默认的无参数的构造函数，没有的话你的子类将无法编译，因为在任何构造函数中的第一条语句隐式调用super()，Java中默认超类的构造函数。
>
> 2\. Java抽象类可以实现接口吗？它们需要实现所有的方法吗？
>
> 可以，抽象类可以通过使用关键字implements来实现接口。因为它们是抽象的，所以它们不需要实现所有的方法。好的做法是，提供一个抽象基类以及一个接口来声明类型
> 。这样的例子是，java.util.List接口和相应的java.util.AbstractList抽象类。因为AbstractList实现了所有的通用方法，具体的实现像LinkedList和ArrayList不受实现所有方法的负担，它们可以直接实现List接口。这对两方面都很好，你可以利用接口声明类型的优点和抽象类的灵活性在一个地方实现共同的行为。Effective
> Java有个很好的章节，介绍如何使用Java的抽象类和接口，值得阅读。
>
> 3\. Java抽象类可以是final的吗？
>
> 不可以，Java抽象类不能是final的。将它们声明为final的将会阻止它们被继承，而这正是使用抽象类唯一的方法。它们也是彼此相反的，关键字abstract强制继承类，而关键字final阻止类被扩张。在现实世界中，抽象表示不完备性，而final是用来证明完整性。底线是，你不能让你的Java类既abstract又final，同时使用，是一个编译时错误。
>
> 4\. Java抽象类可以有static方法吗？
>
> 可以，抽象类可以声明并定义static方法，没什么阻止这样做。但是，你必须遵守Java中将方法声明为static的准则，
>
> 5\. 可以创建抽象类的实例吗？
>
> 不可以，你不能创建Java抽象类的实例，它们是不完全的。即使你的抽象类不包含任何抽象方法，你也不能对它实例化。将类声明为abstract的，就等你你告诉编译器，它是不完全的不应该被实例化。当一段代码尝试实例化一个抽象类时Java编译器会抛错误。
>
> 6\. 抽象类必须有抽象方法吗？
>
> 不需要，抽象类有抽象方法不是强制性的。你只需要使用关键字abstract就可以将类声明为抽象类。编译器会强制所有结构的限制来适用于抽象类，例如，现在允许创建一些实例。是否在抽象类中有抽象方法是引起争论的。我的观点是，抽象类应该有抽象方法，因为这是当程序员看到那个类并做假设的第一件事。这也符合最小惊奇原则。
>
> 8\. 何时选用抽象类而不是接口？
>
> 这是对之前抽象类和接口对比问题的后续。如果你知道语法差异，你可以很容易回答这个问题，因为它们可以令你做出抉择。当关心升级时，因为不可能在一个发布的接口中添加一个新方法，用抽象类会更好。类似地，如果你的接口中有很多方法，你对它们的实现感到很头疼，考虑提供一个抽象类作为默认实现。这是Java集合包中的模式，你可以使用提供默认实现List接口的AbstractList。
>
> 9\. Java中的抽象方法是什么？
>
> 抽象方法是一个没有方法体的方法。你仅需要声明一个方法，不需要定义它并使用关键字abstract声明。Java接口中所有方法的声明默认是abstract的。这是抽象方法的例子
>
> public void abstract printVersion();
>
> 现在，为了实现这个方法，你需要继承该抽象类并重载这个方法。
>
> 10\. Java抽象类中可以包含main方法吗？
>
> 是的，抽象类可以包含main方法，它只是一个静态方法，你可以使用main方法执行抽象类，但不可以创建任何实例。

1.34 Socket
-----------

 Socket 通信具体原理

[]{#_Toc25786 .anchor}1.35 Runtime类

Runtime:运行时，是一个封装了JVM的类。每一个JAVA程序实际上都是启动了一个JVM进程，每一个JVM进程都对应一个Runtime实例，此实例是由JVM为其实例化的。所以我们不能实例化一个Runtime对象，应用程序也不能创建自己的
Runtime 类实例，但可以通过 getRuntime
方法获取当前Runtime运行时对象的引用。一旦得到了一个当前的Runtime对象的引用，就可以调用Runtime对象的方法去控制Java虚拟机的状态和行为。

查看官方文档可以看到，Runtime类中没有构造方法，本类的构造方法被私有化了，
所以才会有getRuntime方法返回本来的实例化对象，这与单例设计模式不谋而合

public static Runtime getRuntime()

直接使用此静态方法可以取得Runtime类的实例

1.36 值传递与引用传递
---------------------

值传递是对基本型变量而言的,传递的是该变量的一个副本,改变副本不影响原变量.

引用传递一般是对于对象型变量而言的,传递的是该对象地址的一个副本, 并不是原对象本身 。一般认为,java内的传递都是值传递. java中实例对象的传递是引用传递  

[]{#_Toc12840 .anchor}1.37 泛型 ？与T的区别

*https://blog.csdn.net/woshizisezise/article/details/79374460*

public static **&lt;**T**&gt;** void show1**(**List**&lt;**T**&gt;**
list**){**

**for** **(**Object object **:** list**)** **{**

System**.**out**.**println**(**object**.**toString**());**

**}**

**}**

public static void show2**(**List**&lt;?&gt;** list**)** **{**

**for** **(**Object object **:** list**)** **{**

System**.**out**.**println**(**object**);**

**}**

**}**

public static void test**(){**

List**&lt;**Student**&gt;** list1 **=** **new** ArrayList**&lt;&gt;();**

list1**.**add**(new** Student**(**"zhangsan"**,**18**,**0**));**

list1**.**add**(new** Student**(**"lisi"**,**28**,**0**));**

list1**.**add**(new** Student**(**"wangwu"**,**24**,**1**));**

//这里如果add(new
Teacher(...));就会报错，因为我们已经给List指定了数据类型为Student

show1**(**list1**);**

System**.**out**.**println**(**"\*\*\*\*\*\*\*\*\*\*\*\*分割线\*\*\*\*\*\*\*\*\*\*\*\*\*\*"**);**

//这里我们并没有给List指定具体的数据类型，可以存放多种类型数据

List list2 **=** **new** ArrayList**&lt;&gt;();**

list2**.**add**(new** Student**(**"zhaoliu"**,**22**,**1**));**

list2**.**add**(new** Teacher**(**"sunba"**,**30**,**0**));**

show2**(**list2**);**

**}**

从show2方法可以看出和show1的区别了，list2存放了Student和Teacher两种类型，同样可以输出数据，所以这就是T和?的区别啦

[]{#_Toc14055 .anchor}1.38 枚举类型字节码层面理解Enum

*https://blog.csdn.net/javazejian/article/details/71333103*

![](media/image49.png){width="4.85in" height="2.75in"}

//反编译Day.class

final class Day **extends** Enum

**{**

//编译器为我们添加的静态的values()方法

public static Day**\[\]** values**()**

**{**

**return** **(**Day**\[\])**\$VALUES**.**clone**();**

**}**

//编译器为我们添加的静态的valueOf()方法，注意间接调用了Enum也类的valueOf方法

public static Day valueOf**(**String s**)**

**{**

**return**
**(**Day**)**Enum**.**valueOf**(**com**/**zejian**/**enumdemo**/**Day**,**
s**);**

**}**

//私有构造函数

private Day**(**String s**,** int i**)**

**{**

**super(**s**,** i**);**

**}**

//前面定义的7种枚举实例

public static final Day MONDAY**;**

public static final Day TUESDAY**;**

public static final Day WEDNESDAY**;**

public static final Day THURSDAY**;**

public static final Day FRIDAY**;**

public static final Day SATURDAY**;**

public static final Day SUNDAY**;**

private static final Day \$VALUES**\[\];**

static

**{**

//实例化枚举实例

MONDAY **=** **new** Day**(**"MONDAY"**,** 0**);**

TUESDAY **=** **new** Day**(**"TUESDAY"**,** 1**);**

WEDNESDAY **=** **new** Day**(**"WEDNESDAY"**,** 2**);**

THURSDAY **=** **new** Day**(**"THURSDAY"**,** 3**);**

FRIDAY **=** **new** Day**(**"FRIDAY"**,** 4**);**

SATURDAY **=** **new** Day**(**"SATURDAY"**,** 5**);**

SUNDAY **=** **new** Day**(**"SUNDAY"**,** 6**);**

\$VALUES **=** **(new** Day**\[\]** **{**

MONDAY**,** TUESDAY**,** WEDNESDAY**,** THURSDAY**,** FRIDAY**,**
SATURDAY**,** SUNDAY

**});**

**}**

**}**

[]{#_Toc8577 .anchor}**1.39 java注解类型**

![](media/image50.png){width="5.761805555555555in"
height="3.790277777777778in"}

[]{#_Toc25632 .anchor}1.40 字节流 字符流

*https://www.cnblogs.com/huangliting/p/5746950.html*

![](media/image51.png){width="5.7625in" height="3.9875in"}

![](media/image52.png){width="5.7in" height="4.8in"}

InputStreamReader
类是从字节流到字符流的桥梁：它读入字节，并根据指定的编码方式，将之转换为字符流。

![](media/image53.png){width="5.760416666666667in" height="4.13125in"}

[]{#_Toc3629 .anchor}**1.41 静态内部类 匿名类**

如果你不需要内部类对象与其外围类对象之间有联系，那你可以将内部类声明为static。这通常称为嵌套类（nested
class）。Static Nested
Class是被声明为静态（static）的内部类，它可以不依赖于外部类实例被实例化。而通常的内部类需要在外部类实例化后才能实例化。想要理解static应用于内部类时的含义，你就必须记住，普通的内部类对象隐含地保存了一个引用，指向创建它的外围类对象。然而，当内部类是static的时，就不是这样了。嵌套类意味着： 

1\. 嵌套类的对象，并不需要其外围类的对象。 

2\. 不能从嵌套类的对象中访问非静态的外围类对象。 

如下所示代码为定义一个静态嵌套类

public class StaticTest{\
   private static String name = "woobo";\
   private String num = "X001";\
   static class Person{ // 静态内部类可以用public,protected,private修饰 

       // 静态内部类中可以定义静态或者非静态的成员  \
     private String address = "China";

Private Static String x=“as”;\
     public String mail = "kongbowoo@yahoo.com.cn";//内部类公有成员\
     public void display(){\
       //System.out.println(num);//不能直接访问外部类的非静态成员

// 静态内部类不能访问外部类的非静态成员(包括非静态变量和非静态方法)\
       System.out.println(name);//只能直接访问外部类的静态成员

//静态内部类只能访问外部类的静态成员(包括静态变量和静态方法)\
       System.out.println("Inner " + address);//访问本内部类成员。\
     }\
   }\
   public void printInfo(){\
     Person person = new Person();

// 外部类访问内部类的非静态成员:实例化内部类即可 

person.display();

     //System.out.println(mail);//不可访问\
     //System.out.println(address);//不可访问\
     System.out.println(person.address);//可以访问内部类的私有成员

System.out.println(Person.x);//
外部类访问内部类的静态成员：内部类.静态成员\
     System.out.println(person.mail);//可以访问内部类的公有成员\
   }\
   public static void main(String\[\] args){\
     StaticTest staticTest = new StaticTest();\
     staticTest.printInfo();\
   }\
}\
 

在静态嵌套类内部, 不能访问外部类的非静态成员,
这是由Java语法中"静态方法不能直接访问非静态成员"所限定.注意,
外部类访问内部类的的成员有些特别, 不能直接访问,
但可以通过内部类实例来访问,
这是因为静态嵌套内的所有成员和方法默认为静态的了.同时注意,
内部静态类Person只在类StaticTest 范围内可见, 若在其它类中引用或初始化,
均是错误的.\
一 . 静态内部类可以有静态成员，而非静态内部类则不能有静态成员。 \
二 .
静态内部类的非静态成员可以访问外部类的静态变量，而不可访问外部类的非静态变量；

三 . 非静态内部类的非静态成员可以访问外部类的非静态变量。

四．在非静态内部类中不可以声明静态成员，一般的非静态内部类，可以随意的访问外部类中的成员变量与成员方法。即使这些成员方法被修饰为private(私有的成员变量或者方法)，其非静态内部类都可以随意的访问。则是非静态内部类的特权。不能够从静态内部类的对象中访问外部类的非静态成员(包括成员变量与成员方法)。

   
生成一个静态内部类不需要外部类成员：这是静态内部类和成员内部类的区别。静态内部类的对象可以直接生成：Outer.Inner
in = new
Outer.Inner();而不需要通过生成外部类对象来生成。这样实际上使静态内部类成为了一个顶级类(正常情况下，你不能在接口内部放置任何代码，但嵌套类可以作为接口的一部分，因为它是static
的。只是将嵌套类置于接口的命名空间内，这并不违反接口的规则）

[]{#_Toc3769 .anchor}** 1.41.2 匿名类**

匿名内部类就是没有名字的内部类；

匿名内部类不能定义任何静态成员、方法。

匿名内部类中的方法不能是抽象的；

匿名内部类必须实现接口或抽象父类的所有抽象方法。

匿名内部类访问的外部类成员变量或成员方法必须用static修饰

1、匿名内部类因为没有类名，可知**匿名内部类不能定义构造器**。

2、因为在创建匿名内部类的时候，会立即创建它的实例，可知**匿名内部类不能是抽象类，必须实现接口或抽象父类的所有抽象方法**。

3、匿名内部类会继承一个父类（有且只有一个）或实现一个接口（有且只有一个），实现父类或接口中所有抽象方法，可以改写父类中的方法，添加自定义方法。

5、当匿名内部类和外部类有同名变量（方法）时，默认访问的是匿名内部类的变量（方法），要访问外部类的变量（方法）则需要加上外部类的类名。

Java I/O底层细节，注意是底层细节，而不是怎么用

如何实现分布式缓存

浏览器的缓存机制

JVM tomcat容器启动，jvm加载情况描述

当获取第一个获取锁之后，条件不满足需要释放锁应当怎么做？

HasnMap实现原理，扩容因子过大过小的缺点，扩容过程
采用什么方法能保证每个bucket中的数据更均匀
解决冲突的方式，还有没有其他方式（全域哈希）

Collection集合类中只能在Iterator中删除元素的原因

java地址和值传递的例子

java NIO，java 多线程、线程池，java 网络编程解决并发量，

java的I/O

手写一个线程安全的生产者与消费者。 

ConcurrentHashMap和LinkedHashMap差异和适用情形

ConcurrentHashMap分段锁是如何实现的

ConcurrentHashmap jdk1.8访问的时候是怎么加锁的，插入的时候是怎么加锁的
访问不加锁插入的时候对头结点加锁

ArrayDeque的使用场景

JDBC连接的过程  手写jdbc连接过程

可重入锁,实现原理

Java IO模型(BIO,NIO等) Tomcat用的哪一种模型

ArrayBlockingQueue源码

多进程和多线程的区别

说出三个遇到过的程序报异常的情况

Java无锁原理

hashmap和treemap的区别

rehash过程

网络编程的accept和connect，

HashMap的负载因子

.try catch finally 可不可以没有catch（try return,finally return）

mapreduce流程 如何保证reduce接受的数据没有丢失，数据如何去重
mapreduce原理，partion发生在什么阶段

直接写一个java程序，统计IP地址的次数

讲讲多线程，多线程的同步方法

list,map,set之间的区别

socket是靠什么协议支持的

java io用到什么设计模式

serviable的序列化，其中uuid的作用

什么时候会用到HashMap

什么情景下会用到反射（答注解、Spring配置文件、动态代理）

浅克隆与深克隆有什么区别

如何实现深克隆

常见的线程安全的集合类

Java 8函数式编程

回调函数，函数式编程，面向对象之间区别

Java 8中stream迭代的优势和区别？

同步等于可见性吗？保证了可见性不等于正确同步，因为还有原子性没考虑。

还了解除util其他包下的List吗？CopyOnWriteArrayList

反射能够使用私有的方法属性吗和底层原理？

处理器指令优化有些什么考虑？ 禁止重排序

object对象的常用方法

Stack和ArrayList的区别

statement和prestatement的区别

手写模拟实现一个阻塞队列

怎么使用父类的方法

util包下有哪几种接口

cookie禁用怎么办

Netty

 new 实例化过程

socket实现过程，具体用的方法；怎么实现异步socket.

很常见的 Nullpointerexception ，你是怎么排查的，怎么解决的；

Binder的原理

C++/JAVA/C的区别

java线程安全都体现在哪些方面，如果维护线程安全

如果想实现一个线程安全的队列，可以怎么实现？\
        JUC包里的ArrayBlockingQueue
还有LinkedBlockingQueue啥的又结合源码说了一通。

静态内部类和非静态内部类的区别是什么？怎么创建静态内部类和非静态内部类？

。

 断点续传的原理

Xml 解析方式，原理优缺点

数据缓存处理

四大组件生命周期

Java 和 JavaScript 的区别

信号量

静态变量和全局变量的区别

二．集合类Set
=============

> 说出所有java集合类

2.1 HashMap
-----------

> *https://blog.csdn.net/jiary5201314/article/details/51439982*

(1) []{#_Toc5436 .anchor}hashMap的原理

> ![](media/image54.png){width="5.761805555555555in"
> height="0.4444444444444444in"}
>
> ![](media/image55.png){width="5.760416666666667in"
> height="0.8444444444444444in"}2.hashcode的计算
>
> *https://www.zhihu.com/question/20733617/answer/111577937*
>
> *https://blog.csdn.net/justloveyou\_/article/details/62893086*
>
> Key.hashcode是key的自带的hascode函数是一个int值32位
>
> ![](media/image56.png){width="5.761805555555555in"
> height="1.5756944444444445in"}
>
> ![](media/image57.png){width="5.7652777777777775in"
> height="3.696527777777778in"}(2) hashMap参数以及扩容机制
>
> ![](media/image58.png){width="5.763194444444444in"
> height="1.2340277777777777in"}

3.  []{#_Toc17377 .anchor}get

**因为整个过程都不需要加锁**

> ![](media/image59.png){width="5.763888888888889in"
> height="2.5118055555555556in"}

[]{#_Toc30322 .anchor}（4）HashMap的put方法源码

> 这里HashMap里面用到链式数据结构的一个概念。上面我们提到过Entry类里面有一个next属性，作用是指向下一个Entry。打个比方，
> 第一个键值对A进来，通过计算其key的hash得到的index=0，记做:Entry\[0\] =
> A。一会后又进来一个键值对B，通过计算其index也等于0，现在怎么办？HashMap会这样做:B.next
> = A,Entry\[0\] = B,如果又进来C,index也等于0,那么C.next = B,Entry\[0\]
> =
> C；这样我们发现index=0的地方其实存取了A,B,C三个键值对,他们通过next这个属性链接在一起。所以疑问不用担心。也就是说数组中存储的是最后插入的元素。到这里为止，HashMap的大致实现。
>
> ![](media/image60.png){width="5.763194444444444in"
> height="4.506944444444445in"}

[]{#_Toc5681 .anchor}（5）HashMap问题 jdk1.8优化

（1）HashMap如果有很多相同key，后面的链很长的话，你会怎么优化？或者你会用什么数据结构来存储？针对HashMap中某个Entry链太长，查找的时间复杂度可能达到O(n)，怎么优化？

![](media/image61.png){width="5.767361111111111in"
height="1.3354166666666667in"}

![](media/image62.png){width="5.763888888888889in"
height="1.9951388888888888in"}

HashMap为什么可以插入空值？

![](media/image63.png){width="5.761805555555555in"
height="1.0166666666666666in"}

![](media/image64.png){width="5.760416666666667in"
height="1.1826388888888888in"}
6.Hashmap为什么线程不安全（hash碰撞和扩容导致）

HashMap扩容的的时候可能会形成环形链表，造成死循环。

![](media/image65.png){width="5.7625in" height="2.73125in"}

要想实现线程安全，那么需要调用collections类的静态方法synchronizeMap（）实现

[]{#_Toc30674 .anchor}7.Hashmap中的key可以为任意对象或数据类型吗？

![](media/image66.png){width="5.768055555555556in"
height="0.2611111111111111in"}

![](media/image67.png){width="5.768055555555556in"
height="0.5458333333333333in"}

2.2 CurrentHashMap
------------------

> *http://www.importnew.com/21781.html*
>
> *https://blog.csdn.net/dingji\_ping/article/details/51005799*
>
> *https://www.cnblogs.com/chengxiao/p/6842045.html*
>
> *http://ifeve.com/hashmap-concurrenthashmap-%E7%9B%B8%E4%BF%A1%E7%9C%8B%E5%AE%8C%E8%BF%99%E7%AF%87%E6%B2%A1%E4%BA%BA%E8%83%BD%E9%9A%BE%E4%BD%8F%E4%BD%A0%EF%BC%81/*
>
> ![](media/image68.png){width="5.7659722222222225in"
> height="3.54375in"}
>
> 一个ConcurrentHashMap维护一个Segment数组，一个Segment维护一个HashEntry数组。

0.  []{#_Toc31542 .anchor}JDK1.7 ConCurrentHashMap原理

> 其中 Segment 继承于 ReentrantLock
>
> ![](media/image69.png){width="5.7652777777777775in"
> height="0.7215277777777778in"}
>
> ![](media/image70.png){width="5.763888888888889in"
> height="0.5993055555555555in"}
>
> Segment继承了ReentrantLock，表明每个segment都可以当做一个锁。这样对每个segment中的数据需要同步操作的话都是使用每个segment容器对象自身的锁来实现。只有对全局需要改变时锁定的是所有的segment。
>
> ![](media/image71.png){width="5.768055555555556in"
> height="2.265277777777778in"}
>
> 2.ConCurrentHashMap Segment内部Get PUT REMOVE

1.  []{#_Toc23558 .anchor}JDK1.7 Get

> ![](media/image72.png){width="5.759722222222222in"
> height="3.298611111111111in"}
>
> CurrentHashMap是否使用了锁？？？
>
> 它也没有使用锁来同步，只是判断获取的entry的value是否为null，为null时才使用加锁的方式再次去获取。
> 这里可以看出并没有使用锁，但是value的值为null时候才是使用了加锁！！！
>
> Get原理：
>
> 第一步，先判断一下 count !=
> 0；count变量表示segment中存在entry的个数。如果为0就不用找了。假设这个时候恰好另一个线程put或者remove了这个segment中的一个entry，会不会导致两个线程看到的count值不一致呢？看一下count变量的定义： transient
> volatile int count;\
> 它使用了volatile来修改。我们前文说过，Java5之后，JMM实现了对volatile的保证：对volatile域的写入操作happens-before于每一个后续对同一个域的读写操作。所以，每次判断count变量的时候，即使恰好其他线程改变了segment也会体现出来
>
> ![](media/image73.png){width="5.763194444444444in"
> height="2.2604166666666665in"}

1)  **在get代码的①和②之间，另一个线程新增了一个entry**\
    > 如果另一个线程新增的这个entry又恰好是我们要get的，这事儿就比较微妙了。下图大致描述了put
    > 一个新的entry的过程。

> ![](media/image74.png){width="5.767361111111111in"
> height="2.3868055555555556in"}
>
> 因为每个HashEntry中的next也是final的，没法对链表最后一个元素增加一个后续entry所以新增一个entry的实现方式只能通过头结点来插入了。newEntry对象是通过 new
> HashEntry(K k , V v, HashEntry next) 来创建的。如果另一个线程刚好new
> 这个对象时，当前线程来get它。因为没有同步，就可能会出现当前线程得到的newEntry对象是一个没有完全构造好的对象引用。
> 如果在这个new的对象的后面，则完全不影响，如果刚好是这个new的对象，那么当刚好这个对象没有完全构造好，也就是说这个对象的value值为null,就出现了如下所示的代码，需要重新加锁再次读取这个值！

![](media/image75.png){width="5.763194444444444in"
height="0.5305555555555556in"}

1)  **在get代码的①和②之间，另一个线程修改了一个entry的value**

> value是用volitale修饰的，可以保证读取时获取到的是修改后的值。

1)  **在get代码的①之后，另一个线程删除了一个entry**

> 假设我们的链表元素是：e1-&gt; e2 -&gt; e3 -&gt; e4 我们要删除
> e3这个entry，因为HashEntry中next的不可变，所以我们无法直接把e2的next指向e4，而是将要删除的节点之前的节点复制一份，形成新的链表。它的实现大致如下图所示：

![](media/image76.png){width="5.760416666666667in"
height="2.672222222222222in"}

> 如果我们get的也恰巧是e3，可能我们顺着链表刚找到e1，这时另一个线程就执行了删除e3的操作，而我们线程还会继续沿着旧的链表找到e3返回。这里没有办法实时保证了，也就是说没办法看到最新的。
>
> 我们第①处就判断了count变量，它保障了在
> ①处能看到其他线程修改后的。①之后到②之间，如果再次发生了其他线程再删除了entry节点，就没法保证看到最新的了，这时候的get的实际上是未更新过的！！！。
>
> 不过这也没什么关系，即使我们返回e3的时候，它被其他线程删除了，暴漏出去的e3也不会对我们新的链表造成影响。

1.  []{#_Toc22826 .anchor}JDK1.7 PUT

<!-- -->

1.  将当前 Segment 中的 table 通过 key 的 hashcode 定位到 HashEntry。

2.  遍历该 HashEntry，如果不为空则判断传入的 key 和当前遍历的 key
    > 是否相等，相等则覆盖旧的 value。

3.  不为空则需要新建一个 HashEntry 并加入到 Segment
    > 中，同时会先判断是否需要扩容。

4.  最后会解除在 1 中所获取当前 Segment 的锁。

> 可以说是首先找到segment，确定是哪一个segment,然后在这个segment中遍历查找
> key值是要查找的key值得entry,如果找到，那么就修改该key,如果没找到，那么就在头部新加一个entry.
>
> ![](media/image77.png){width="5.761111111111111in"
> height="3.204861111111111in"}
>
> ![](media/image78.png){width="5.7625in" height="2.676388888888889in"}
>
> ![](media/image79.png){width="5.767361111111111in"
> height="3.053472222222222in"}

1.  []{#_Toc20593 .anchor}JDK1.7 Remove

> ![](media/image80.png){width="5.7659722222222225in"
> height="3.365972222222222in"}
>
> ![](media/image81.png){width="5.7625in" height="2.9493055555555556in"}
>
> ![](media/image82.png){width="5.760416666666667in"
> height="1.9986111111111111in"}

[]{#_Toc30262 .anchor}**4.JDK1.7 & JDK1.8 size()**

![](media/image83.png){width="5.768055555555556in"
height="0.31319444444444444in"}

public int size() {\
long n = sumCount();\
return ((n &lt; 0L) ? 0 :\
(n &gt; (long)Integer.*MAX\_VALUE*) ? Integer.*MAX\_VALUE* :\
(int)n);\
}

volatile 保证内存可见，最大是65535.

[]{#_Toc6922 .anchor}**5.JDK 1.8**

![](media/image84.png){width="5.6in" height="3.1666666666666665in"}

1.  **其中抛弃了原有的 Segment 分段锁，而采用了 CAS +
    synchronized 来保证并发安全性。**

2.  **大于8的时候才去红黑树链表转红黑树的阀值，当table\[i\]下面的链表长度大于8时就转化为红黑树结构。**

[]{#_Toc32596 .anchor}**6.JDK1.8 put**

-   根据 key 计算出 hashcode 。

-   判断是否需要进行初始化。

-   f 即为当前 key 定位出的 Node，如果为空表示当前位置可以写入数据，利用
    CAS 尝试写入，失败则自旋保证成功。

-   如果当前位置的 hashcode == MOVED == -1,则需要进行扩容。

-   如果都不满足，则利用 synchronized
    锁写入数据(分为链表写入和红黑树写入）。

-   如果数量大于 TREEIFY\_THRESHOLD 则要转换为红黑树。

![IMG\_256](media/image85.jpeg){width="8.884027777777778in"
height="9.969444444444445in"}

7.  []{#_Toc23190 .anchor}**JDK1.8 get方法**

![IMG\_256](media/image86.jpeg){width="9.041666666666666in"
height="3.5520833333333335in"}

-   根据计算出来的 hashcode 寻址，如果就在桶上那么直接返回值。

-   如果是红黑树那就按照树的方式获取值。

-   就不满足那就按照链表的方式遍历获取值。

7.  []{#_Toc28447 .anchor}rehash过程

Redis rehash ：dictRehash每次增量rehash
n个元素，由于在自动调整大小时已设置好了ht\[1\]的大小，因此rehash的主要过程就是遍历ht\[0\]，取得key，然后将该key按ht\[1\]的
桶的大小重新rehash，并在rehash完后将ht\[0\]指向ht\[1\],然后将ht\[0\]清空。在这个过程中**rehashidx**非常重要，它表示上次rehash时在ht\[0\]的下标位置。

可以看到，redis对dict的rehash是分批进行的，这样不会阻塞请求，设计的比较优雅。

但是在调用dictFind的时候，可能需要对两张dict表做查询。唯一的优化判断是，当key在ht\[0\]不存在且不在rehashing状态时，可以速度返回空。如果在rehashing状态，当在ht\[0\]没值的时候，还需要在ht\[1\]里查找。

dictAdd的时候，如果状态是rehashing，则把值插入到ht\[1\]，否则ht\[0\]

2.3 . Hashtable
---------------

*https://blog.csdn.net/ns\_code/article/details/36191279*

[]{#_Toc18823 .anchor}0.参数

（1）table是一个Entry\[\]数组类型，而Entry实际上就是一个单向链表。哈希表的"key-value键值对"都是存储在Entry数组中的。 

（2）count是Hashtable的大小，它是Hashtable保存的键值对的数量。 

（3）threshold是Hashtable的阈值，用于判断是否需要调整Hashtable的容量。threshold的值="容量\*加载因子"。

（4）loadFactor就是加载因子。

（5）modCount是用来实现fail-fast机制的

[]{#_Toc21592 .anchor}1.put

从下面的代码中我们可以看出，Hashtable中的key和value是不允许为空的，当我们想要想Hashtable中添加元素的时候，首先计算key的hash值，然

后通过hash值确定在table数组中的索引位置，最后将value值替换或者插入新的元素，如果容器的数量达到阈值，就会进行扩充。

![](media/image87.png){width="5.768055555555556in"
height="5.519444444444445in"}

[]{#_Toc10760 .anchor}2.get

> ![](media/image88.png){width="5.768055555555556in"
> height="2.1993055555555556in"}

[]{#_Toc1406 .anchor}3.Remove

在下面代码中，如果prev为null了，那么说明第一个元素就是要删除的元素，那么就直接指向第一个元素的下一个即可。

> ![](media/image89.png){width="5.768055555555556in"
> height="4.313888888888889in"}
>
> []{#_Toc24760 .anchor}**4.扩容**
>
> 默认初始容量为11

　　　　线程安全，但是速度慢，不允许key/value为null

　　　　加载因子为0.75：即当 元素个数 超过 容量长度的0.75倍 时，进行扩容

　　　　　扩容增量：2\*原数组长度+1

　　　　　　如 HashTable的容量为11，一次扩容后是容量为23

2.4 hashtable和hashmap的区别
----------------------------

![](media/image90.png){width="5.768055555555556in"
height="2.095138888888889in"}

2.5 HashMap和ConCurrentHashMap区别
----------------------------------

![](media/image91.png){width="5.768055555555556in" height="1.025in"}

2.6 ConcurrentHashMap和HashTable区别
------------------------------------

ConcurrentHashMap仅仅锁定map的某个部分，而Hashtable则会锁定整个map。

hashtable(同一把锁):使用synchronized来保证线程安全，但效率非常低下。当一个线程访问同步方法时，其他线程也访问同步方法，可能会进入阻塞或轮询状态，如使用put添加元素，另一个线程不能使用put添加元素，也不能使用get，竞争会越来越激烈效率越低。\
concurrenthashmap(分段锁):(锁分段技术)每一把锁只锁容器其中一部分数据，多线程访问容器里不同数据段的数据，就不会存在锁竞争，提高并发访问率。首先将数据分为一段一段的存储，然后给每一段数据配一把锁，当一个线程占用锁访问其中一个段数据时，其他段的数据也能被其他线程访问。concurrenthashmap是由Segment数组结构和HahEntry数组结构组成。Segment是一种可重入锁ReentrantLock，扮演锁的角色。HashEntry用于存储键值对数据。一个concurrenthashmap里包含一个Segment数组。Segment的结构和Hashmap类似，是一种数组和链表结构，一个Segment包含一个HashEntry数组，每个HashEntry是一个链表结构的元素，每个Segment守护着一个HashEntry数组里的元素，当对HashEntry数组的数据进行修改时，必须首先获得对应的Segment。

2.7 linkedHashMap
-----------------

*https://blog.csdn.net/justloveyou\_/article/details/71713781*

![](media/image92.png){width="5.768055555555556in"
height="3.6506944444444445in"}

2.8 Linkedhashmap与 hashmap的区别
---------------------------------

1.  LinkedHashMap是HashMap的子类

2.  LinkedHashMap中的Entry增加了两个指针 **before** 和 **after**，它们分别用于维护双向链接列表。

3.  在put操作上，虽然LinkedHashMap完全继承了HashMap的put操作，但是在细节上还是做了一定的调整，比如，在LinkedHashMap中向哈希表中插入新Entry的同时，还会通过Entry的addBefore方法将其链入到双向链表中。

4.  在扩容操作上，虽然LinkedHashMap完全继承了HashMap的resize操作，但是鉴于性能和LinkedHashMap自身特点的考量，LinkedHashMap对其中的重哈希过程(transfer方法)进行了重写

5.  在读取操作上，LinkedHashMap中重写了HashMap中的get方法，通过HashMap中的getEntry方法获取Entry对象。在此基础上，进一步获取指定键对应的值。

2.9 HashSet
-----------

对于HashSet而言，它是基于HashMap实现的

Hashset源码 *http://zhangshixi.iteye.com/blog/673143*

Hashset 如何保证集合的没有重复元素？

可以看出hashset底层是hashmap但是存储的是一个对象，hashset实际将该元素e作为key放入hashmap,当key值(该元素e)相同时，只是进行更新value，并不会新增加，所以set中的元素不会进行改变。

![](media/image93.png){width="3.0409722222222224in"
height="0.6347222222222222in"}

![](media/image94.png){width="5.768055555555556in"
height="3.308333333333333in"}

2.10 hashmap与hashset区别
-------------------------

![](media/image95.png){width="5.768055555555556in" height="2.3625in"}

2.11 Collections.sort 内部原理
------------------------------

![](media/image96.png){width="5.764583333333333in"
height="2.589583333333333in"}

重写 Collections.sort()

import java.util.\*;\
class xd{\
int a;\
int b;\
xd(int a,int b){\
this.a = a;\
this.b = b;\
}\
}\
public class Main {\
public static void main(String\[\] arg) {\
xd a = new xd(2,3);\
xd b = new xd(4,1);\
xd c = new xd(1,2);\
ArrayList&lt;xd&gt; array = new ArrayList&lt;&gt;();\
array.add(a);\
array.add(b);\
array.add(c);\
Collections.*sort*(array, new Comparator&lt;xd&gt;() {\
@Override\
public int compare(xd o1, xd o2) {\
if(o1.a &gt; o2.a)\
return 1;\
else if(o1.a &lt; o2.a)\
return -1;\
return 0;\
}\
});\
for(int i=0;i&lt;array.size();i++)\
System.*out*.println(array.get(i).a);\
for(int i=0;i&lt;array.size();i++)\
System.*out*.println(array.get(i).b);\
}\
\
\
\
}

2.12 hash算法
-------------

![](media/image97.png){width="5.753472222222222in"
height="1.5715277777777779in"}

java map底层实现，最好看源码，还有各种集合类的区别

4.  TreeMap和TreeSet区别和实现原理

5.  集合和有序集合有什么区别

6.  Set是无序的，那怎么保证它有序？有什么办法吗？提到了TreeSet，那说一下TreeSet为什么能够保证有序？

7.  java中hashMap结构，处理冲突方法，还有啥方法，各个方法优缺点

> .Collections.sort()  的原理

集合框架的理解 对Java的集合框架有什么样的了解, 用过哪些集合类,
各自的效率以及适用场景

cas的实现原理，以及aba问题

> List/Set/Queue 接口及其实现类
>
> HashSet/TreeSet/HashMap/TreeMap/hashTable 这些类的底层实现。
>
> 常问： hashSet 和 HashMap 有什么区别
> 。各自的底层实现是基于什么的。这里紧接着的问题通常是：我们来聊聊多线程（微笑脸），或者我们来聊聊红黑树。

2.13 迭代器 Iterator Enumeration
--------------------------------

**1. Iterator和ListIterator的区别是什么？**

答：Iterator可用来遍历Set和List集合，但是ListIterator只能用来遍历List。Iterator对集合只能是前向遍历，ListIterator既可以前向也可以后向。

ListIterator实现了Iterator接口，并包含其他的功能，比如：增加元素，替换元素，获取前一个和后一个元素的索引，等等。

1.  **快速失败(fail-fast)和安全失败(fail-safe)的区别是什么？**

答：Iterator的安全失败是基于对底层集合做拷贝，因此，它不受源集合上修改的影响。java.util包下面的所有的集合类都是快速失败的，而java.util.concurrent包下面的所有的类都是安全失败的。快速失败的迭代器会抛出ConcurrentModificationException异常，而安全失败的迭代器永远不会抛出这样的异常。

1.  **Enumeration接口和Iterator接口的区别有哪些？**

> 答：Enumeration速度是Iterator的2倍，同时占用更少的内存。但是，Iterator远远比Enumeration安全，因为其他线程不能够修改正在被iterator遍历的集合里面的对象。同时，Iterator允许调用者删除底层集合里面的元素，这对Enumeration来说是不可能的。

2.14 LIST ArrayList，LinkedList和Vector的区别和实现原理
-------------------------------------------------------

Vector : *https://blog.csdn.net/chenssy/article/details/37520981*

一．ArrayList与LinkedList区别

ArrayList和LinkedList都实现了List接口，他们有以下的不同点：\
ArrayList是基于索引的数据接口，它的底层是数组。它可以以O(1)时间复杂度对元素进行随机访问。与此对应，LinkedList是以元素列表的形式存储它的数据，每一个元素都和它的前一个和后一个元素链接在一起，在这种情况下，查找某个元素的时间复杂度是O(n)。\
相对于ArrayList，LinkedList的插入，添加，删除操作速度更快，因为当元素被添加到集合任意位置的时候，不需要像数组那样重新计算大小或者是更新索引。\
LinkedList比ArrayList更占内存，因为LinkedList为每一个节点存储了两个引用，一个指向前一个元素，一个指向下一个元素。

二．Vetor arraylist Linkedlist 区别

ArrayList
就是动态数组，是Array的复杂版本，动态的增加和减少元素.当更多的元素加入到ArrayList中时,其大小将会动态地增长。它的元素可以通过get/set方法直接访问，因为ArrayList本质上是一个数组。初始容量为10。1.插入元素的时候可能扩容，删除元素时不会缩小容量。2.扩容增长为Arraylist增长原来的0.5倍
3. 而Arraylist 没有设置增长空间的方法。4.线程不同步

Vector 和ArrayList类似,
区别在于Vector是同步类(synchronized).因此,开销就比ArrayList要大。初始容量为10。实现了随机访问接口，可以随机访问。Vector是内部是以动态数组的形式来存储数据的。1.Vector还可以设置增长的空间大小，2. 及Vector增长原来的1倍3.vector
线程同步

LinkedList
是一个双链表,在添加和删除元素时具有比ArrayList更好的性能.但在get与set方面弱于ArrayList.当然,这些对比都是指数据量很大或者操作很频繁的情况下的对比。它还实现了
Queue 接口,该接口比List提供了更多的方法,包括 offer(),peek(),poll()等.

ArrayList和LinkedList的使用场景，其中add方法的实现ArrayList,LinkedList的实现以及插入，查找，删除的过程

Arraylist如何实现排序

**三．使用ArrayList的迭代器会出现什么问题？单线程和多线程环境下；**

答：常用的迭代器设计模式，iterator方法返回一个父类实现的迭代器。\
1、迭代器的hasNext方法的作用是判断当前位置是否是数组最后一个位置，相等为false，否则为true。\
2、迭代器next方法用于返回当前的元素，并把指针指向下一个元素，值得注意的是，每次使用next方法的时候，都会判断创建迭代器获取的这个容器的计数器modCount是否与此时的不相等，不相等说明集合的大小被修改过，如果是会抛出ConcurrentModificationException异常，如果相等调用get方法返回元素即可。

**四．数组(Array)和列表(ArrayList)有什么区别？什么时候应该使用Array而不是ArrayList？**

答：不同点：定义上：Array可以包含基本类型和对象类型，ArrayList只能包含对象类型。容量上：Array大小固定，ArrayList的大小是动态变化的。操作上：ArrayList提供更多的方法和特性，如：addAll()，removeAll()，iterator()等等。使用基本数据类型或者知道数据元素数量的时候可以考虑Array;ArrayList处理固定数量的基本类型数据类型时会自动装箱来减少编码工作量，但是相对较慢。

五．**ArrayList和Vector有何异同点？**

相同点：

（1）两者都是基于索引的，都是基于数组的。

（2）两者都维护插入顺序，我们可以根据插入顺序来获取元素。

（3）ArrayList和Vector的迭代器实现都是fail-fast的。

（4）ArrayList和Vector两者允许null值，也可以使用索引值对元素进行随机访问。

不同点：

（1）Vector是同步，线程安全，而ArrayList非同步，线程不安全。对于ArrayList，如果迭代时改变列表，应该使用CopyOnWriteArrayList。

（2）但是，ArrayList比Vector要快，它因为有同步，不会过载。

（3）在使用上，ArrayList更加通用，因为Collections工具类容易获取同步列表和只读列表。

2.15 快速失败(fail-fast)和安全失败(fail-safe)
---------------------------------------------

一：快速失败（fail—fast）

         
在用迭代器遍历一个集合对象时，如果遍历过程中对集合对象的内容进行了修改（增加、删除、修改），则会抛出Concurrent
Modification Exception。

          原理：迭代器在遍历时直接访问集合中的内容，并且在遍历过程中使用一个
modCount
变量。集合在被遍历期间如果内容发生变化，就会改变modCount的值。每当迭代器使用hashNext()/next()遍历下一个元素之前，都会检测modCount变量是否为expectedmodCount值，是的话就返回遍历；否则抛出异常，终止遍历。

      注意：这里异常的抛出条件是检测到 modCount！=expectedmodCount
这个条件。如果集合发生变化时修改modCount值刚好又设置为了expectedmodCount值，则异常不会抛出。因此，不能依赖于这个异常是否抛出而进行并发操作的编程，这个异常只建议用于检测并发修改的bug。

     
场景：java.util包下的集合类都是快速失败的，不能在多线程下发生并发修改（迭代过程中被修改）。

    二：安全失败（fail—safe）

     
采用安全失败机制的集合容器，在遍历时不是直接在集合内容上访问的，而是先复制原有集合内容，在拷贝的集合上进行遍历。

     
原理：由于迭代时是对原集合的拷贝进行遍历，所以在遍历过程中对原集合所作的修改并不能被迭代器检测到，所以不会触发Concurrent
Modification Exception。

      缺点：基于拷贝内容的优点是避免了Concurrent Modification
Exception，但同样地，迭代器并不能访问到修改后的内容，即：迭代器遍历的是开始遍历那一刻拿到的集合拷贝，在遍历期间原集合发生的修改迭代器是不知道的。

         
场景：java.util.concurrent包下的容器都是安全失败，可以在多线程下并发使用，并发修改。

快速失败和安全失败是对迭代器而言的。
快速失败：当在迭代一个集合的时候，如果有另外一个线程在修改这个集合，就会抛出ConcurrentModification异常，java.util下都是快速失败。
安全失败：在迭代时候会在集合二层做一个拷贝，所以在修改集合上层元素不会影响下层。在java.util.concurrent下都是安全失败

三 锁 volatile synchronized Lock ReentrantLock AQS CAS
======================================================

3.1 .volatile 和 synchronized 
------------------------------

**1.volatile 和 synchronized实现原理**

![](media/image98.png){width="5.75625in" height="3.777083333333333in"}

![](media/image99.png){width="5.7652777777777775in"
height="6.511805555555555in"}

![](media/image100.png){width="5.767361111111111in"
height="2.759027777777778in"}

[]{#_Toc17768 .anchor}**3.1.1 Volatile 与 synchronized 区别**

> ![](media/image101.png){width="5.7659722222222225in"
> height="2.9131944444444446in"}

[]{#_Toc25751 .anchor}**3.1.2 Volatile**

> ![](media/image102.png){width="5.761111111111111in"
> height="3.063888888888889in"}

[]{#_Toc10039 .anchor}**3.1.3 Synchronized原理**

> ***https://blog.csdn.net/javazejian/article/details/72828483***
>
> ***https://blog.csdn.net/chen77716/article/details/6618779***
>
> Synchronized是可重入的
>
> Jvm对象都有对象头，对象头是实现synchronized的基础，对象头都有如下结构
>
> ![](media/image103.png){width="5.768055555555556in"
> height="0.8493055555555555in"}
>
> 而Mark Word的结构（不固定）如下所示
>
> ![](media/image104.png){width="5.768055555555556in"
> height="0.5513888888888889in"}
>
> ![](media/image105.png){width="5.415972222222222in"
> height="2.3430555555555554in"}
>
> 从上图可以看到Mark
> Word包括重量级锁，重量级锁的指针指向monitor对象（监视器锁）所以每一个对象都与一个monitor关联，当一个
> monitor
> 被某个线程持有后，它便处于锁定状态。谈及monitor来看一下monitord的实现，monitor是由ObjectMonitor实现的，其主要数据结构如下
>
> ![](media/image106.png){width="5.768055555555556in"
> height="2.9715277777777778in"}

当多个线程同时请求某个对象监视器时，对象监视器会设置几种状态用来区分请求的线程：

-   Contention List：所有请求锁的线程将被首先放置到该竞争队列

-   Entry List：Contention List中那些有资格成为候选人的线程被移到Entry
    > List

-   Wait Set：那些调用wait方法被阻塞的线程被放置到Wait Set

-   OnDeck：任何时刻最多只能有一个线程正在竞争锁，该线程称为OnDeck

-   Owner：获得锁的线程称为Owner

-   !Owner：释放锁的线程

![](media/image107.png){width="5.768055555555556in"
height="2.560416666666667in"}

![](media/image108.png){width="5.768055555555556in"
height="2.6326388888888888in"}

synchronizated 和lock差别
Lock多出的三大优势（尝试非阻塞加锁，尝试超时加锁，尝试可相应中断加锁）

Lock内部实现

synchronized可以替代读写锁吗

ReentrantLock源码

volatile理解，这个问题很常见，答出要点： 可见性、防止指令重排即可

java锁机制

java中的同步机制，，锁（重入锁）机制，其他解决同步的方volatile关键字ThreadLocal类的实现原理要懂。

要减小锁粒度呢（用Java提供的原子类，比如AtomicInteger），
AtomicInteger怎么实现原子修改的（核心方法是compareAndSwap方法，俗
称CAS，源代码没有公开），CAS方法的主要功能是什么？

**Java编程写一个会导致死锁的程序**

3.2 CAS
-------

***https://www.jianshu.com/p/fb6e91b013cc***

CAS的思想很简单：三个参数，一个当前内存值V、旧的预期值A、即将更新的值B，当且仅当预期值A和内存值V相同时，将内存值修改为B并返回true，否则什么都不做，并返回false。

实现原理：CAS中有Unsafe类中的compareAndSwapInt方法，Unsafe类中的compareAndSwapInt，是一个本地方法，该方法的实现位于unsafe.cpp中

Unsafe.cpp:

先想办法拿到变量value在内存中的地址。

通过Atomic::cmpxchg实现比较替换，其中参数x是即将更新的值，参数e是原内存的值。

其中Atomic::cmpxchg中对此指令加lock前缀，而lock前缀有两个特性1，禁止该指令与前面和后面的读写指令重排序2，把写缓冲区的所有数据刷新到内存中

这两点保证了内存屏障效果，保证了CAS同时具有volatile读和volatile写的内存语义。

**CAS解读示例: **

![](media/image109.png){width="5.768055555555556in"
height="3.1534722222222222in"}

3.3 可重入锁 ReentrantLock
--------------------------

*https://www.cnblogs.com/xrq730/p/4979021.html*

### 1.5.3乐观锁和悲观锁 阻塞锁，自旋锁，偏向锁，轻量锁，重量锁。公平锁 非公平锁

自旋锁引入背景：那些处于ContetionList、EntryList、WaitSet中的线程均处于阻塞状态，阻塞操作由操作系统完成（在Linxu下通过pthread\_mutex\_lock函数）。线程被阻塞后便进入内核（Linux）调度状态，这个会导致系统在用户态与内核态之间来回切换，严重影响锁的性能

偏向锁引入背景：避免重入锁的CAS操作

*https://www.tuicool.com/articles/YVrQFj*

1.  公平锁与非公平锁

> 公平锁和非公平锁，顾名思义，公平锁就是获得锁的顺序按照先到先得的原则，从实现上说，要求当一个线程竞争某个对象锁时，只要这个锁的等待队列非空，就必须把这个线程阻塞并塞入队尾（插入队尾一般通过一个CAS保持插入过程中没有锁释放）。相对的，非公平锁场景下，每个线程都先要竞争锁，在竞争失败或当前已被加锁的前提下才会被塞入等待队列，在这种实现下，后到的线程有可能无需进入等待队列直接竞争到锁。
>
> ![](media/image110.png){width="5.768055555555556in"
> height="0.6055555555555555in"}

[]{#_Toc22907 .anchor}**3.3 ReentrantLock 和 synchronized 区别**

![](media/image111.png){width="5.760416666666667in"
height="2.3305555555555557in"}

synchronized原语和ReentrantLock在一般情况下没有什么区别，但是在非常复杂的同步应用中，请考虑使用ReentrantLock，特别是遇到下面2种需求的时候。\
 \
1.某个线程在等待一个锁的控制权的这段时间需要中断\
2.需要分开处理一些wait-notify，ReentrantLock里面的Condition应用，能够控制notify哪个线程\
3.具有公平锁功能，每个到来的线程都将排队等候

1.  ReentrantLock可中断
    可超时尝试非阻塞加锁，尝试超时加锁，尝试可相应中断加锁

2.  ReentrantLock

lock()：获取锁，如果锁被暂用则一直等待

unlock():释放锁

tryLock():
注意返回类型是boolean，如果获取锁的时候锁被占用就返回false，否则返回true

tryLock(long time, TimeUnit
unit)：比起tryLock()就是给了一个时间期限，保证等待参数时间

lockInterruptibly()：用该锁的获得方式，如果线程在获取锁的阶段进入了等待，那么可以中断此线程，先去做别的事

### 1.5.3 重入锁、对象锁、类锁的关系

四 java多线程；
===============

*https://blog.csdn.net/evankaka/article/details/44153709\#t3*

*https://www.cnblogs.com/gaopeng527/p/4234211.html*

*https://www.cnblogs.com/lixuan1998/p/6937986.html*

*https://www.cnblogs.com/felixzh/p/6036074.html*

4.1 ．如何创建线程？哪种好？
----------------------------

有4种方式可以用来创建线程：1.继承Thread类2.实现Runnable接口3.应用程序可以使用Executor框架来创建线程池4.
实现Callable接口

> 实现Runnable接口比继承Thread类所具有的优势：1）：适合多个相同的程序代码的线程去处理同一个资源2）：可以避免java中的单继承的限制3）：增加程序的健壮性，代码可以被多个线程共享，代码和数据独立4）：线程池只能放入实现Runable或callable类线程，不能直接放入继承Thread的类5）runnable实现线程可以对线程进行复用，因为runnable是轻量级的对象，重复new不会耗费太大资源，而Thread则不然，它是重量级对象，而且线程执行完就完了，无法再次利用

4.2．线程状态
-------------

![https://img-blog.csdn.net/20150309140927553](media/image112.jpeg){width="5.767361111111111in"
height="3.5548611111111112in"}

1、新建状态（New）：新创建了一个线程对象。

2、就绪状态（Runnable）：线程对象创建后，其他线程调用了该对象的start()方法。该状态的线程位于可运行线程池中，变得可运行，等待获取CPU的使用权。

3、运行状态（Running）：就绪状态的线程获取了CPU，执行程序代码。

4、阻塞状态（Blocked）：阻塞状态是线程因为某种原因放弃CPU使用权，暂时停止运行。直到线程进入就绪状态，才有机会转到运行状态。阻塞的情况分三种：

（一）、等待阻塞：运行的线程执行wait()方法，JVM会把该线程放入等待池中。(wait会释放持有的锁)

（二）、同步阻塞：运行的线程在获取对象的同步锁时，若该同步锁被别的线程占用，则JVM会把该线程放入锁池中。

（三）、其他阻塞：运行的线程执行sleep()或join()方法，或者发出了I/O请求时，JVM会把该线程置为阻塞状态。当sleep()状态超时、join()等待线程终止或者超时、或者I/O处理完毕时，线程重新转入就绪状态。（注意,sleep是不会释放持有的锁）

5、死亡状态（Dead）：线程执行完了或者因异常退出了run()方法，该线程结束生命周期。

4.3．一般线程和守护线程的区别
-----------------------------

所谓守护线程是指在程序运行的时候在后台提供一种通用服务的线程，比如垃圾回收线程就是一个很称职的守护者，并且这种线程并不属于程序中不可或缺的部分。因
此，当所有的非守护线程结束时，程序也就终止了，同时会杀死进程中的所有守护线程。反过来说，只要任何非守护线程还在运行，程序就不会终止。

区别：唯一的区别是判断虚拟机(JVM)何时离开，Daemon是为其他线程提供服务，如果全部的User
Thread已经撤离，Daemon
没有可服务的线程，JVM撤离。也可以理解为守护线程是JVM自动创建的线程（但不一定），用户线程是程序创建的线程；比如JVM的垃圾回收线程是一个守护线程，当所有线程已经撤离，不再产生垃圾，守护线程自然就没事可干了，当垃圾回收线程是Java虚拟机上仅剩的线程时，Java虚拟机会自动离开。

在使用守护线程时需要注意一下几点：

(1)
thread.setDaemon(true)必须在thread.start()之前设置，否则会跑出一个IllegalThreadStateException异常。你不能把正在运行的常规线程设置为守护线程。

\(2) 在Daemon线程中产生的新线程也是Daemon的。

(3)
守护线程应该永远不去访问固有资源，如文件、数据库，因为它会在任何时候甚至在一个操作的中间发生中断。

4.4．sleep  wait yield notify notifyAll join
--------------------------------------------

一．Sleep与wait区别

1. sleep 是线程类（Thread）的方法，导致此线程暂停执行指定时间，给执行机会给其他线程，但是监控状态依然保持，到时后会自动恢复。调用sleep 不会释放对象锁。  sleep()使当前线程进入阻塞状态，在指定时间内不会执行。  

2. wait 是Object 类的方法，对此对象调用wait 方法导致本线程放弃对象锁，进入等待此对象的等待锁定池，只有针对此对象发出notify 方法（或notifyAll）后本线程才进入对象锁定池准备获得对象锁进入运行状态。  

区别比较：  

1、这两个方法来自不同的类分别是Thread和Object  

2、最主要是sleep方法没有释放锁，而wait方法释放了锁，使得其他线程可以使用同步控制块或者方法。  

3、wait，notify和notifyAll只能在同步控制方法或者同步控制块里面使用，而sleep可以在任何地方使用(使用范围)  

4、sleep必须捕获异常，而wait，notify和notifyAll不需要捕获异常  

  (1) sleep方法属于Thread类中方法，表示让一个线程进入睡眠状态，等待一定的时间之后，自动醒来进入到可运行状态，不会马上进入运行状态，因为线程调度机制恢复线程的运行也需要时间，一个线程对象调用了sleep方法之后，并不会释放他所持有的所有对象锁，所以也就不会影响其他进程对象的运行。但在sleep的过程中过程中有可能被其他对象调用它的interrupt(),产生InterruptedException异常，如果你的程序不捕获这个异常，线程就会异常终止，进入TERMINATED状态，如果你的程序捕获了这个异常，那么程序就会继续执行catch语句块(可能还有finally语句块)以及以后的代码。  

  注意sleep()方法是一个静态方法，也就是说他只对当前对象有效，通过t.sleep()让t对象进入sleep，这样的做法是错误的，它只会是使当前线程被sleep 而不是t线程  

  (2) wait属于Object的成员方法，一旦一个对象调用了wait方法，必须要采用notify()和notifyAll()方法唤醒该进程;如果线程拥有某个或某些对象的同步锁，那么在调用了wait()后，这个线程就会释放它持有的所有同步资源，而不限于这个被调用了wait()方法的对象。wait()方法也同样会在wait的过程中有可能被其他对象调用interrupt()方法而产生  

> 二 yield join notify notifyAll

yield()方法是停止当前线程，让同等优先权的线程或更高优先级的线程有执行的机会。如果没有的话，那么yield()方法将不会起作用，并且由可执行状态后马上又被执行。   

join方法是用于在某一个线程的执行过程中调用另一个线程执行，等到被调用的线程执行结束后，再继续执行当前线程。如：t.join();//主要用于等待t线程运行结束，若无此句，main则会执行完毕，导致结果不可预测。  

notify方法只唤醒一个等待（对象的）线程并使该线程开始执行。所以如果有多个线程等待一个对象，这个方法只会唤醒其中一个线程，选择哪个线程取决于操作系统对多线程管理的实现。

notifyAll
会唤醒所有等待(对象的)线程，尽管哪一个线程将会第一个处理取决于操作系统的实现

4.5中断线程
-----------

中断线程有很多方法：（1）使用退出标志，使线程正常退出，也就是当run方法完成后线程终止。（2）通过return退出run方法（3）通过对有些状态中断抛异常退出
thread.interrupt() 中断。（4）使用stop方法强行终止线程（过期）

中断线程可能出现的问题：

使用：Thread.interrupt()并不能使得线程被中断，线程还是会执行。最靠谱的方法就是设置一个全局的标记位，然后再Thread中去检查这个标记位，发现标记位改变则中断线程。

![](media/image113.png){width="5.764583333333333in"
height="4.730555555555555in"}

4.6 多线程如何避免死锁
----------------------

> **什么是死锁？**

所谓死锁是指多个进
程因竞争资源而造成的一种僵局（互相等待），若无外力作用，这些进程都将无法向前推进。死锁产生的4个必要条件：

-   互斥条件：进程要求对所分配的资源（如打印机）进行排他性控制，即在一段时间内某
    资源仅为一个进程所占有。此时若有其他进程请求该资源，则请求进程只能等待。

-   不剥夺条件：进程所获得的资源在未使用完毕之前，不能被其他进程强行夺走，即只能
    由获得该资源的进程自己来释放（只能是主动释放)。

-   请求和保持条件：进程已经保持了至少一个资源，但又提出了新的资源请求，而该资源
    已被其他进程占有，此时请求进程被阻塞，但对自己已获得的资源保持不放。

-   循环等待条件：存在一种进程资源的循环等待链，链中每一个进程已获得的资源同时被
    链中下一个进程所请求。

> **如何确保N个线程可以访问N个资源同时又不导致死锁？**
>
> 使用多线程的时候，一种非常简单的避免死锁的方式就是：指定获取锁的顺序，并强制线程按照指定的顺序获取锁。因此，如果所有的线程都是以同样的顺序加锁和释放锁，就不会出现死锁了。
>
> *https://blog.csdn.net/ls5718/article/details/51896159*
>
> 1.加锁顺序（线程按照一定的顺序加锁）
>
> 2.加锁时限（线程尝试获取锁的时候加上一定的时限，超过时限则放弃对该锁的请求，并释放自己占有的锁）
>
> 3.死锁检测

4,7 多线程的好处以及问题
------------------------

> （1）发挥多核CPU的优势
>
> （2）防止阻塞
>
> （3）便于建模
>
> 这是另外一个没有这么明显的优点了。假设有一个大的任务A，单线程编程，那么就要考虑很多，建立整个程序模型比较麻烦。但是如果把这个大的任务A分解成几个小任务，任务B、任务C、任务D，分别建立程序模型，并通过多线程分别运行这几个任务，那就简单很多了。
>
> 问题：线程安全问题

4.8 多线程共用一个数据变量注意什么？
------------------------------------

![](media/image114.png){width="5.768055555555556in"
height="1.4743055555555555in"}

![](media/image115.png){width="5.763888888888889in"
height="0.5763888888888888in"}

4.9 线程通信方式
----------------

1.  同步

同步是指多个线程通过synchronized关键字这种方式来实现线程间的通信。

2.**wait/notify机制**

4.10 线程池
-----------

![](media/image116.png){width="5.768055555555556in"
height="3.123611111111111in"}

![](media/image117.png){width="5.768055555555556in"
height="0.6826388888888889in"}

![](media/image118.png){width="5.768055555555556in"
height="0.5284722222222222in"}

![](media/image119.png){width="5.757638888888889in"
height="3.2104166666666667in"}

[]{#_Toc24671 .anchor}4.11.线程中抛出异常怎么办

> 当单线程的程序发生一个未捕获的异常时我们可以采用try....catch进行异常的捕获，但是在多线程环境中，线程抛出的异常是不能用try....catch捕获的，这样就有可能导致一些问题的出现，比如异常的时候无法回收一些系统资源，或者没有关闭当前的连接等等。

![](media/image120.png){width="5.763194444444444in"
height="4.101388888888889in"}

> 简单的说，如果异常没有被捕获该线程将会停止执行。Thread.UncaughtExceptionHandler是用于处理未捕获异常造成线程突然中断情况的一个内嵌接口。当一个未捕获异常将造成线程中断的时候JVM会使用Thread.getUncaughtExceptionHandler()来查询线程的UncaughtExceptionHandler并将线程和异常作为参数传递给handler的uncaughtException()方法进行处理。

java线程池达到提交上限的具体情况

线程池用法。

Java多线程，线程池有哪几类，每一类的差别
.要你设计的话，如何实现一个线程池
线程池的类型，固定大小的线程池内部是如何实现的，等待队列是用了哪一个队列实现

线程池种类和工作流程（重点讲newcached线程池）

线程池工作原理

比如corePoolSize和maxPoolSize这两个参数该怎么调

线程池使用了什么设计模式

线程池使用时一般要考虑哪些问题

线程池的配置 Excutor 以及Connector的配置、

AysncTask每来一个任务都会创建一个线程来执行吗？(否，线程池的方式实现的)

介绍下AsyncTask的实现原理；

五．Java进阶ssh/ssm框架
=======================

2.1Spring 
----------

> []{#_Toc11581 .anchor}**2.1.0 什么是Spring 以及优点**

**1. 什么是spring?**

Spring 是个java企业级应用的开源开发框架。Spring主要用来开发Java应用，但是有些扩展是针对构建J2EE平台的web应用。Spring 框架目标是简化Java企业级应用开发，并通过POJO为基础的编程模型促进良好的编程习惯。

 

**2. 使用Spring框架的好处是什么？**

-   **轻量：**Spring 是轻量的，基本的版本大约2MB。

-   **控制反转：**Spring通过控制反转实现了松散耦合，对象们给出它们的依赖，而不是创建或查找依赖的对象们。

-   **面向切面的编程(AOP)：**Spring支持面向切面的编程，并且把应用业务逻辑和系统服务分开。

-   **容器：**Spring 包含并管理应用中对象的生命周期和配置。

-   **MVC框架**：Spring的WEB框架是个精心设计的框架，是Web框架的一个很好的替代品。

-   **事务管理：**Spring 提供一个持续的事务管理接口，可以扩展到上至本地事务下至全局事务（JTA）。

-   **异常处理：**Spring 提供方便的API把具体技术相关的异常（比如由JDBC，Hibernate or JDO抛出的）转化为一致的unchecked 异常。

    1.  []{#_Toc9641 .anchor}**ApplicationContext 和 beanfactory的区别**

1.  利用MessageSource进行国际化  \
    >  
    > BeanFactory是不支持国际化功能的，因为BeanFactory没有扩展Spring中MessageResource接口。相反，由于ApplicationContext扩展了MessageResource接口，因而具有消息处理的能力(i18N)，具体spring如何使用国际化，以后章节会详细描述。 \
    > 2.强大的事件机制(Event)  \
    >  
    > 基本上牵涉到事件(Event)方面的设计，就离不开观察者模式。不明白观察者模式的朋友，最好上网了解下。因为，这种模式在java开发中是比较常用的，又是比较重要的。 \
    > ApplicationContext的事件机制主要通过ApplicationEvent和ApplicationListener这两个接口来提供的，和java
    > swing中的事件机制一样。即当ApplicationContext中发布一个事件的时，所有扩展了ApplicationListener的Bean都将会接受到这个事件，并进行相应的处理。 \
    > 3.底层资源的访问  \
    >  
    > ApplicationContext扩展了ResourceLoader(资源加载器)接口，从而可以用来加载多个Resource，而BeanFactory是没有扩展ResourceLoader 

> 4. 
> .BeanFactroy采用的是延迟加载形式来注入Bean的，即只有在使用到某个Bean时(调用getBean())，才对该Bean进行加载实例化，这样，我们就不能发现一些存在的Spring的配置问题。而ApplicationContext则相反，它是在容器启动时，一次性创建了所有的Bean。这样，在容器启动时，我们就可以发现Spring中存在的配置错误。 

[]{#_Toc1582 .anchor}**2.1.2 Spring Bean生命周期**

 Spring上下文中的Bean也类似，如下

    1、实例化一个Bean－－也就是我们常说的new；

    2、按照Spring上下文对实例化的Bean进行配置－－也就是IOC注入；

    3、如果这个Bean已经实现了BeanNameAware接口，会调用它实现的setBeanName(String)方法，此处传递的就是Spring配置文件中Bean的id值

    4、如果这个Bean已经实现了BeanFactoryAware接口，会调用它实现的setBeanFactory(setBeanFactory(BeanFactory)传递的是Spring工厂自身（可以用这个方式来获取其它Bean，只需在Spring配置文件中配置一个普通的Bean就可以）；

    5、如果这个Bean已经实现了ApplicationContextAware接口，会调用setApplicationContext(ApplicationContext)方法，传入Spring上下文（同样这个方式也可以实现步骤4的内容，但比4更好，因为ApplicationContext是BeanFactory的子接口，有更多的实现方法）；

    6、如果这个Bean关联了BeanPostProcessor接口，将会调用postProcessBeforeInitialization(Object
obj, String
s)方法，BeanPostProcessor经常被用作是Bean内容的更改，并且由于这个是在Bean初始化结束时调用那个的方法，也可以被应用于内存或缓存技术；

    7、如果Bean在Spring配置文件中配置了init-method属性会自动调用其配置的初始化方法。

    8、如果这个Bean关联了BeanPostProcessor接口，将会调用postProcessAfterInitialization(Object
obj, String s)方法、；

    注：以上工作完成以后就可以应用这个Bean了，那这个Bean是一个Singleton的，所以一般情况下我们调用同一个id的Bean会是在内容地址相同的实例，当然在Spring配置文件中也可以配置非Singleton，这里我们不做赘述。

    9、当Bean不再需要时，会经过清理阶段，如果Bean实现了DisposableBean这个接口，会调用那个其实现的destroy()方法；

10、最后，如果这个Bean的Spring配置中配置了destroy-method属性，会自动调用其配置的销毁方法。

### 2.1.3 spring中bean的作用域

**默认是单例**

  ------------ ----------- --------------------------
  **作用域**   **字符**    **描述**
  单例         singleton   整个应用中只创建一个实例
  原型         prototype   每次注入时都新建一个实例
  会话         session     为每个会话创建一个实例
  请求         request     为每个请求创建一个实例
  ------------ ----------- --------------------------

[]{#_Toc4747 .anchor}2.1.4 Spring IOC

*https://blog.csdn.net/it\_man/article/details/4402245*

IOC:，IOC利用java反射机制，AOP利用代理模式。所谓控制反转是指，本来被调用者的实例是有调用者来创建的，这样的缺点是耦合性太强，IOC则是统一交给spring来管理创建，将对象交给容器管理，你只需要在spring配置文件总配置相应的bean，以及设置相关的属性，让spring容器来生成类的实例对象以及管理对象。在spring容器启动的时候，spring会把你在配置文件中配置的bean都初始化好，然后在你需要调用的时候，就把它已经初始化好的那些bean分配给你需要调用这些bean的类。 

IoC的一个重点是在系统运行中，动态的向某个对象提供它所需要的其他对象。这一点是通过DI（Dependency
Injection，依赖注入）来实现的。比如对象A需要操作数据库，以前我们总是要在A中自己编写代码来获得一个Connection对象，有了 spring我们就只需要告诉spring，A中需要一个Connection，至于这个Connection怎么构造，何时构造，A不需要知道。在系统运行时，spring会在适当的时候制造一个Connection，然后像打针一样，注射到A当中，这样就完成了对各个对象之间关系的控制。A需要依赖 Connection才能正常运行，而这个Connection是由spring注入到A中的，依赖注入的名字就这么来的。那么DI是如何实现的呢？ Java
1.3之后一个重要特征是反射（reflection），它允许程序在运行的时候动态的生成对象、执行对象的方法、改变对象的属性，spring就是通过反射来实现注入的。

[]{#_Toc15410 .anchor}2.1.5 Spring AOP

2.5.1.1.什么是AOP

AOP技术利用一种称为“横切”的技术，剖解开封装的对象内部，并将那些影响了多个类的公共行为封装到一个可重用模块，并将其名为“Aspect”，即方面。所谓“方面”，简单地说，就是将那些与业务无关，却为业务模块所共同调用的逻辑或责任封装起来，便于减少系统的重复代码，降低模块间的耦合度，并有利于未来的可操作性和可维护性。使用“横切”技术，AOP把软件系统分为两个部分：核心关注点和横切关注点。业务处理的主要流程是核心关注点，与之关系不大的部分是横切关注点。横切关注点的一个特点是，他们经常发生在核心关注点的多处，而各处都基本相似。比如权限认证、日志、事务处理。Aop
的作用在于分离系统中的各种关注点，将核心关注点和横切关注点分离开来。

2.AOP原理

基于动态代理

*https://www.cnblogs.com/CHENJIAO120/p/7080790.html*

![](media/image121.png){width="5.45in" height="4.383333333333334in"}

它们之间的调用先后次序反映在上图的序号中：

调用者Bean尝试调用目标方法，但是被生成的代理截了胡

代理根据Advice的种类(本例中是@Before Advice)，对Advice首先进行调用

代理调用目标方法

返回调用结果给调用者Bean(由代理返回，没有体现在图中)

2.1.5.2基于接口的动态代理

*http://www.cnblogs.com/xiaoluo501395377/p/3383130.html*

在java的动态代理机制中，有两个重要的类或接口，一个是
InvocationHandler(Interface)、另一个则是
Proxy(Class)，这一个类和接口是实现我们动态代理所必须用到的。首先我们先来看看java的API帮助文档是怎么样对这两个类进行描述的：

1.InvocationHandler:

每一个动态代理类都必须要实现InvocationHandler这个接口，并且每个代理类的实例都关联到了一个handler，当我们通过代理对象调用一个方法的时候，这个方法的调用就会被转发为由InvocationHandler这个接口的
invoke
方法来进行调用。我们来看看InvocationHandler这个接口的唯一一个方法 invoke 方法

Object invoke(Object proxy, Method method, Object\[\] args) throws
Throwable

**proxy**:　　**指代我们所代理的那个真实对象**

**method**:　　**指代的是我们所要调用真实对象的某个方法的Method对象**

**args**:　　**指代的是调用真实对象某个方法时接受的参数**

> **2.Proxy**
>
> Proxy这个类的作用就是用来动态创建一个代理对象的类，它提供了许多的方法，但是我们用的最多的就是 newProxyInstance 这个方法：

public static Object newProxyInstance(ClassLoader loader,
Class&lt;?&gt;\[\] interfaces, InvocationHandler h) throws
IllegalArgumentException

**2.5.2.4 实现子类的动态代理**

CGlib动态代理是通过继承业务类，生成的动态代理类是业务类的子类，通过重写业务方法进行代理；

![](media/image122.png){width="5.7652777777777775in"
height="1.2083333333333333in"}

![](media/image123.png){width="5.763194444444444in"
height="0.8736111111111111in"}

[]{#_Toc14194 .anchor}**2.1.6 事务 **

**2.1.6.1 事务的实现方式**

（1）编程式事务管理对基于 POJO
的应用来说是唯一选择。我们需要在代码中调用beginTransaction()、commit()、rollback()等事务管理相关的方法，这就是编程式事务管理。

（2）基于 TransactionProxyFactoryBean的声明式事务管理

（3）基于 @Transactional 的声明式事务管理

（4）基于Aspectj AOP配置事务

根据代理机制的不同，Spring事务的配置又有几种不同的方式：

**第一种方式：每个Bean都有一个代理**

**第二种方式：所有Bean共享一个代理基类**

**第三种方式：使用拦截器**

**第四种方式：使用tx标签配置的拦截器**

**第五种方式：全注解**

**2.1.6.2 事务的传播级别**

1）
PROPAGATION\_REQUIRED ，默认的spring事务传播级别，使用该级别的特点是，如果上下文中已经存在事务，那么就加入到事务中执行，如果当前上下文中不存在事务，则新建事务执行。所以这个级别通常能满足处理大多数的业务场景。

2）PROPAGATION\_SUPPORTS ，从字面意思就知道，supports，支持，该传播级别的特点是，如果上下文存在事务，则支持事务加入事务，如果没有事务，则使用非事务的方式执行。所以说，并非所有的包在transactionTemplate.execute中的代码都会有事务支持。这个通常是用来处理那些并非原子性的非核心业务逻辑操作。应用场景较少。

3）PROPAGATION\_MANDATORY ，
该级别的事务要求上下文中必须要存在事务，否则就会抛出异常！配置该方式的传播级别是有效的控制上下文调用代码遗漏添加事务控制的保证手段。比如一段代码不能单独被调用执行，但是一旦被调用，就必须有事务包含的情况，就可以使用这个传播级别。

4）PROPAGATION\_REQUIRES\_NEW ，从字面即可知道，new，每次都要一个新事务，该传播级别的特点是，每次都会新建一个事务，并且同时将上下文中的事务挂起，执行当前新建事务完成以后，上下文事务恢复再执行。

这是一个很有用的传播级别，举一个应用场景：现在有一个发送100个红包的操作，在发送之前，要做一些系统的初始化、验证、数据记录操作，然后发送100封红包，然后再记录发送日志，发送日志要求100%的准确，如果日志不准确，那么整个父事务逻辑需要回滚。\
怎么处理整个业务需求呢？就是通过这个PROPAGATION\_REQUIRES\_NEW
级别的事务传播控制就可以完成。发送红包的子事务不会直接影响到父事务的提交和回滚。

5）PROPAGATION\_NOT\_SUPPORTED ，这个也可以从字面得知，not supported
，不支持，当前级别的特点就是上下文中存在事务，则挂起事务，执行当前逻辑，结束后恢复上下文的事务。

这个级别有什么好处？可以帮助你将事务极可能的缩小。我们知道一个事务越大，它存在的风险也就越多。所以在处理事务的过程中，要保证尽可能的缩小范围。比如一段代码，是每次逻辑操作都必须调用的，比如循环1000次的某个非核心业务逻辑操作。这样的代码如果包在事务中，势必造成事务太大，导致出现一些难以考虑周全的异常情况。所以这个事务这个级别的传播级别就派上用场了。用当前级别的事务模板抱起来就可以了。

6）PROPAGATION\_NEVER ，该事务更严格，上面一个事务传播级别只是不支持而已，有事务就挂起，而PROPAGATION\_NEVER传播级别要求上下文中不能存在事务，一旦有事务，就抛出runtime异常，强制停止执行！这个级别上辈子跟事务有仇。

7）PROPAGATION\_NESTED ，字面也可知道，nested，嵌套级别事务。该传播级别特征是，如果上下文中存在事务，则嵌套事务执行，如果不存在事务，则新建事务。

> **2.1.6.3 事务的嵌套失效**

那么什么是嵌套事务呢？很多人都不理解，我看过一些博客，都是有些理解偏差。

嵌套是子事务套在父事务中执行，子事务是父事务的一部分，在进入子事务之前，父事务建立一个回滚点，叫save
point，然后执行子事务，这个子事务的执行也算是父事务的一部分，然后子事务执行结束，父事务继续执行。重点就在于那个save
point。看几个问题就明了了：

如果子事务回滚，会发生什么？

父事务会回滚到进入子事务前建立的save
point，然后尝试其他的事务或者其他的业务逻辑，父事务之前的操作不会受到影响，更不会自动回滚。

如果父事务回滚，会发生什么？

父事务回滚，子事务也会跟着回滚！为什么呢，因为父事务结束之前，子事务是不会提交的，我们说子事务是父事务的一部分，正是这个道理。那么：

事务的提交，是什么情况？

是父事务先提交，然后子事务提交，还是子事务先提交，父事务再提交？答案是第二种情况，还是那句话，子事务是父事务的一部分，由父事务统一提交。

[]{#_Toc9543 .anchor}2.1.7 Spring MVC

**2.1.7.0 什么是Spring MVC**

Spring MVC是一个基于MVC架构的用来简化web应用程序开发的应用开发框架，它是Spring的一个模块,无需中间整合层来整合 ，它和Struts2一样都属于表现层的框架。在web模型中，MVC是一种很流行的框架，通过把Model，View，Controller分离，把较为复杂的web应用分成逻辑清晰的几部分，简化开发，减少出错，方便组内开发人员之间的配合。

**2.1.7.1 Spring MVC执行流程（工作原理）**

答：1.用户发送请求至前端控制器DispatcherServlet

2.DispatcherServlet收到请求调用HandlerMapping处理器映射器。

3.处理器映射器根据请求url找到具体的处理器，生成处理器对象及处理器拦截器(如果有则生成)一并返回给DispatcherServlet。

4.DispatcherServlet通过HandlerAdapter处理器适配器调用处理器

5.执行处理器(Controller，也叫后端控制器)。

6.Controller执行完成返回ModelAndView

7.HandlerAdapter将controller执行结果ModelAndView返回给DispatcherServlet

8.DispatcherServlet将ModelAndView传给ViewReslover视图解析器

9.ViewReslover解析后返回具体View

10.DispatcherServlet对View进行渲染视图（即将模型数据填充至视图中）。

11.DispatcherServlet响应用

2.1.7.2 SpringMVC 加载流程

springmvc加载流程\
1.Servlet加载（监听器之后即执行）Servlet的init()\
2.加载配置文件\
3.从ServletContext拿到spring初始化springmvc相关对象\
4.放入ServletContext

2.1.7.2 **springMVC和struts2的区别**

（1）springmvc的入口是一个servlet即前端控制器（DispatchServlet），而struts2入口是一个filter过虑器（StrutsPrepareAndExecuteFilter）。

（2）springmvc是基于方法开发(一个url对应一个方法)，请求参数传递到方法的形参，可以设计为单例或多例(建议单例)，struts2是基于类开发，传递参数是通过类的属性，只能设计为多例。

（3）Struts采用值栈存储请求和响应的数据，通过OGNL存取数据，springmvc通过参数解析器是将request请求内容解析，并给方法形参赋值，将数据和视图封装成ModelAndView对象，最后又将ModelAndView中的模型数据通过reques域传输到页面。Jsp视图解析器默认使用jstl。

[]{#_Toc9341 .anchor}**2.1.8 Spring中设计模式**

*https://www.cnblogs.com/jifeng/p/7398852.html*

**第一种：简单工厂**\
\
又叫做静态工厂方法（StaticFactory
Method）模式，但不属于23种GOF设计模式之一。 \
简单工厂模式的实质是由一个工厂类根据传入的参数，动态决定应该创建哪一个产品类。 \
spring中的BeanFactory就是简单工厂模式的体现，根据传入一个唯一的标识来获得bean对象，但是否是在传入参数后创建还是传入参数前创建这个要根据具体情况来定。如下配置，就是在
HelloItxxz 类中创建一个 itxxzBean。

**第三种：单例模式（Singleton）**\
\
保证一个类仅有一个实例，并提供一个访问它的全局访问点。 \
spring中的单例模式完成了后半句话，即提供了全局的访问点BeanFactory。但没有从构造器级别去控制单例，这是因为spring管理的是是任意的java对象。 \
核心提示点：Spring下默认的bean均为singleton，可以通过singleton=“true|false”
或者 scope=“？”来指定

**第四种：适配器（Adapter）**\
\
在Spring的Aop中，使用的Advice（通知）来增强被代理类的功能。Spring实现这一AOP功能的原理就使用代理模式（1、JDK动态代理。2、CGLib字节码生成技术代理。）对类进行方法级别的切面增强，即，生成被代理类的代理类，
并在代理类的方法前，设置拦截器，通过执行拦截器重的内容增强了代理方法的功能，实现的面向切面编程。

**第六种：代理（Proxy）**\
\
为其他对象提供一种代理以控制对这个对象的访问。 
从结构上来看和Decorator模式类似，但Proxy是控制，更像是一种对功能的限制，而Decorator是增加职责。 \
spring的Proxy模式在aop中有体现，比如JdkDynamicAopProxy和Cglib2AopProxy。 \
\
**第七种：观察者（Observer）**\
\
定义对象间的一种一对多的依赖关系，当一个对象的状态发生改变时，所有依赖于它的对象都得到通知并被自动更新。\
spring中Observer模式常用的地方是listener的实现。如ApplicationListener。 \
\
**第八种：策略（Strategy）**\
\
定义一系列的算法，把它们一个个封装起来，并且使它们可相互替换。本模式使得算法可独立于使用它的客户而变化。 \
spring中在实例化对象的时候用到Strategy模式\
在SimpleInstantiationStrategy中有如下代码说明了策略模式的使用情况： 

**第九种：模板方法（Template Method）**\
\
定义一个操作中的算法的骨架，而将一些步骤延迟到子类中。Template
Method使得子类可以不改变一个算法的结构即可重定义该算法的某些特定步骤。\
Template Method模式一般是需要继承的。这里想要探讨另一种对Template
Method的理解。spring中的JdbcTemplate，在用这个类时并不想去继承这个类，因为这个类的方法太多，但是我们还是想用到JdbcTemplate已有的稳定的、公用的数据库连接，那么我们怎么办呢？我们可以把变化的东西抽出来作为一个参数传入JdbcTemplate的方法中。但是变化的东西是一段代码，而且这段代码会用到JdbcTemplate中的变量。怎么办？那我们就用回调对象吧。在这个回调对象中定义一个操纵JdbcTemplate中变量的方法，我们去实现这个方法，就把变化的东西集中到这里了。然后我们再传入这个回调对象到JdbcTemplate，从而完成了调用。这可能是Template
Method不需要继承的另一种实现方式吧。 

以下是一个具体的例子： \
JdbcTemplate中的execute方法 

Spring的加载流程，Spring的源码中Bean的构造的流程

Spring事务源码，IOC源码，AOP源码

spring的作用及理解

事务怎么配置

Spring的annotation如何实现

SpringMVC工作原

了解SpringMVC与Struct2区别

了解SpringMVC请求流程

springMVC和spring是什么关系

项目中Spring的IOC和AOP具体怎么使用的

spring mvc 底层实现原理

动态代理的原理

如果使用spring mvc，那post请求跟put请求有什么区别啊；

然后开始问springmvc：描述从tomcat开始到springmvc返回到前端显示的整个流程...

接着问springmvc中的handlerMapping的内部实现；

.然后又问spring中从载入xml文件到getbean整个流程，描述一遍

2.2 Servlet
-----------

[]{#_Toc21750 .anchor}**2.2.1 Servlet 生命周期**

1.创建Servlet对象，通过服务器反射机制创建Servlet对象，第一次请

求时才会创建。（默认）

2，调用Servlet对象的init()方法，初始化Servlet的信息，init()方法只会在创建后被调用一次；

3，响应请求，调用service()或者是doGet()，doPost()方法来处理请求，这些方法是运行的在多线程状态下的。

4， 
在长时间没有被调用或者是服务器关闭时，会调用destroy()方法来销毁Servlet对象。

2.2.2 servlet是什么

 
Servlet定义：Servlet是基于Java技术的Web组件，由容器管理并产生动态的内容。Servlet引擎作为WEB服务器

的扩展提供支持Servlet的功能。Servlet与客户端通过Servlet容器实现的请求/响应模型进行交互

Servlet知道是做什么的吗？和JSP有什么联系？JSP的运行原理？JSP属于Java中的吗？

Servlet是线程安全

scala写的大型框架吗  spark

如何确保分布式环境下异步消息处理的顺序性？

 servlet是单例

servlet和filter的区别。

servlet流程

1.  []{#_Toc29589 .anchor}**Struts**

[]{#_Toc837 .anchor}**2.2.1 Struts工作流程**

![](media/image124.png){width="5.767361111111111in"
height="1.8701388888888888in"}

[]{#_Toc8767 .anchor}**2.2.2 Struts 工作原理**

> ![](media/image125.png){width="5.7652777777777775in"
> height="1.2833333333333334in"}
>
> ![](media/image126.png){width="5.766666666666667in"
> height="2.9819444444444443in"}

[]{#_Toc26912 .anchor}**2.2.3 do Fliter**

> ![](media/image127.png){width="5.768055555555556in"
> height="0.46805555555555556in"}
>
> ![](media/image128.png){width="5.767361111111111in"
> height="5.500694444444444in"}
>
> ![](media/image129.png){width="5.764583333333333in"
> height="1.4604166666666667in"}

[]{#_Toc16189 .anchor}**2.2.4 拦截器与过滤器的区别**

![](media/image130.png){width="5.7625in" height="2.19375in"}

[]{#_Toc14868 .anchor}**2.2.5 Struts中为什么不用考虑线程安全**

![](media/image131.png){width="5.763888888888889in"
height="1.3034722222222221in"}

![](media/image132.png){width="5.761805555555555in"
height="0.5604166666666667in"}

[]{#_Toc6582 .anchor}**2.2.6 Struts2 和 Struts1 区别**

![](media/image133.png){width="5.7625in" height="3.888888888888889in"}

2.3 Hibernate
-------------

Hibernate的生成策略，主要说了native 、uuid

Hibernate与Mybatis区别

2.4 Redis
---------

Redis数据结构 Redis持久化机制

Redis的一致性哈希算法

redis了解多少redis五种数据类型，当散列类型的value值非常大的时候怎么进行压缩，
用redis怎么实现摇一摇与附近的人功能，redis主从复制过程，

Redis如何解决key冲突

redis的五种数据结构

redis是怎么存储数据的

redis使用场景

2.5 Tomcat
----------

Tomcat的结构

tomcat均衡方式 ，netty

2.6 netty
---------

netty源码

2.7 Hadoop 
-----------

2.8 Volley
----------

Volley 的原理及使用

springMVC和spring是什么关系

一些java的常用框架的架构

.Servlet的Filter用的什么设计模式

Spring读过哪些源码吗

利用Bean的初始化可以做什么事情

排行榜可以使用redis哪种数据结构

RESTful架构

Hibernate、Mybatis与JDBC区别

springmvc的流程 一个请求来了之后如何处理（handler链）

框架封装jdbc受检异常的考虑和原因？

zookeeper的常用功能，自己用它来做什么

hadoop/spark/impala/lucene/RocksDB/redis这些框架的技术点

ibatis跟hibernate的区别

ibatis是怎么实现映射的，它的映射原理是什么

redis的操作是不是原子操作

秒杀业务场景设计

WebSocket长连接问题

如何设计淘宝秒杀系统（重点关注架构，比如数据一致性，数据库集群一致性哈希，缓存，分库分表等等）？

 List接口去实例化一个它的实现类（ArrayList）以及直接用ArrayList去new一个该类的对象，这两种方式有什么区别，为什么大多数情况下会用到

Tomcat关注哪些参数

Mapreduce

Spring 配置过滤器 和 Struts的拦截器配置与使用。

对后台的优化有了解吗？比如负载均衡。我给面试官说了
Ngix+Tomcat负载均衡，异步处理（消息缓冲服务器），缓存(Redis，          
  Memcache)，NoSQL，数据库优化，存储索引优化

开源项目

Netty框架源码看过吗

MapReduce

Volley机制讲完之后问我Volley的缺点是什么，怎么改进

对 Restful 了解

Restful 的认识，优点，以及和 soap 的区别

lrucache 的基本原理

service 中启动方式有哪些区别是？

六．Java 内存模型 和 垃圾回收
=============================

[]{#_Toc25584
.anchor}**3.0什么是JMM内存模型？（JMM和内存区域划分不是一回事）**

> *https://blog.csdn.net/javazejian/article/details/72772461*
>
> 大体：JMM就是一组规则，这组规则意在解决在并发编程可能出现的线程安全问题，JMM (Java
> Memory
> Model)是Java内存模型,JMM定义了程序中各个共享变量的访问规则,即在虚拟机中将变量存储到内存和从内存读取变量这样的底层细节.并提供了内置解决方案（happen-before原则）及其外部可使用的同步手段(synchronized/volatile等)，确保了程序执行在多线程环境中的应有的**原子性，可视性及其有序性**。
>
> **2.JMM规定了所有的变量都存储在主内存（Main
> Memory）中。每个线程还有自己的工作内存（Working
> Memory）,线程的工作内存中保存了该线程使用到的变量的主内存的副本拷贝，线程对变量的所有操作（读取、赋值等）都必须在工作内存中进行，而不能直接读写主内存中的变量（volatile变量仍然有工作内存的拷贝，但是由于它特殊的操作顺序性规定，所以看起来如同直接在主内存中读写访问一般）。不同的线程之间也无法直接访问对方工作内存中的变量，线程之间值的传递都需要通过主内存来完成。**

[]{#_Toc12973 .anchor}3.0.1 JMM中的happens-before原则

happens-before 原则内容如下

程序顺序原则，即在一个线程内必须保证语义串行性，也就是说按照代码顺序执行。

锁规则
解锁(unlock)操作必然发生在后续的同一个锁的加锁(lock)之前，也就是说，如果对于一个锁解锁后，再加锁，那么加锁的动作必须在解锁动作之后(同一个锁)。

volatile规则
volatile变量的写，先发生于读，这保证了volatile变量的可见性，简单的理解就是，volatile变量在每次被线程访问时，都强迫从主内存中读该变量的值，而当该变量发生变化时，又会强迫将最新的值刷新到主内存，任何时刻，不同的线程总是能够看到该变量的最新值。

线程启动规则
线程的start()方法先于它的每一个动作，即如果线程A在执行线程B的start方法之前修改了共享变量的值，那么当线程B执行start方法时，线程A对共享变量的修改对线程B可见

传递性 A先于B ，B先于C 那么A必然先于C

线程终止规则
线程的所有操作先于线程的终结，Thread.join()方法的作用是等待当前执行的线程终止。假设在线程B终止之前，修改了共享变量，线程A从线程B的join方法成功返回后，线程B对共享变量的修改将对线程A可见。

线程中断规则 对线程
interrupt()方法的调用先行发生于被中断线程的代码检测到中断事件的发生，可以通过Thread.interrupted()方法检测线程是否中断。

对象终结规则 对象的构造函数执行，结束先于finalize()方法

![](media/image134.png){width="5.767361111111111in"
height="1.4381944444444446in"}

![](media/image135.png){width="5.7652777777777775in"
height="2.839583333333333in"}

3.1 内存分区
------------

![](media/image136.png){width="5.228472222222222in"
height="4.082638888888889in"}

![](media/image137.png){width="5.766666666666667in"
height="3.941666666666667in"}

![](media/image138.png){width="4.561805555555556in"
height="1.8333333333333333in"}

什么是堆中的永久代？

> 答：永久代是用于存放静态文件，如Java类、方法等。持久代对垃圾回收没有显著影响，但是有些应用可能动态生成或者调用一些class，例如Hibernate
> 等，在这种时候需要设置一个比较大的持久代空间来存放这些运行过程中新增的类，永久代中一般包含：
>
> 类的方法(字节码...)
>
> 类名(Sring对象)
>
> .class文件读到的常量信息
>
> class对象相关的对象列表和类型列表 (e.g., 方法对象的array).
>
> JVM创建的内部对象
>
> JIT编译器优化用的信息

![](media/image139.png){width="5.763888888888889in"
height="3.3645833333333335in"}

3.2 GC算法（YGC and FGC）
-------------------------

![](media/image140.png){width="5.7625in" height="5.534722222222222in"}

![](media/image141.png){width="5.761805555555555in"
height="0.7506944444444444in"}

![](media/image142.png){width="5.7659722222222225in"
height="0.9847222222222223in"}

![](media/image143.png){width="5.763194444444444in"
height="0.9888888888888889in"}

**其中永久代如何内存不足也会触发fullGC**

![](media/image144.png){width="5.7659722222222225in"
height="1.1201388888888888in"}

[]{#_Toc11848 .anchor}3.2.1 YGC

答：说白了就是复制算法，对象只会存在于Eden区和名为“From”的Survivor区，Survivor区“To”是空的。紧接着进行GC，Eden区中所有存活的对象都会被复制到“To”，而在“From”区中，仍存活的对象会根据他们的年龄值来决定去向。年龄达到一定值(年龄阈值，可以通过-XX:MaxTenuringThreshold来设置)的对象会被移动到年老代中，没有达到阈值的对象会被复制到“To”区域。经过这次GC后，Eden区和From区已经被清空。这个时候，“From”和“To”会交换他们的角色，也就是新的“To”就是上次GC前的“From”，新的“From”就是上次GC前的“To”。不管怎样，都会保证名为To的Survivor区域是空的。Minor
GC会一直重复这样的过程，直到“To”区被填满，“To”区被填满之后，会将所有对象移动到年老代中。

其中如果发生晋升失败的情况，那么说明老年代的内存空间不够用了，需要进行一次FullGC

[]{#_Toc26811 .anchor}3.2.2 FGC

答:FGC 就是标记整理或者是标记清除算法来清除老年代。

3.3 垃圾收集器 CMS
------------------

![](media/image145.png){width="5.763194444444444in"
height="2.5993055555555555in"}

![](media/image146.png){width="5.754861111111111in" height="3.33125in"}

![](media/image147.png){width="5.768055555555556in"
height="0.8645833333333334in"}

![](media/image148.png){width="5.761111111111111in"
height="0.30972222222222223in"}

![](media/image149.png){width="5.764583333333333in"
height="3.0076388888888888in"}

3.4 java类加载机制 双亲委派
---------------------------

> *https://blog.csdn.net/ns\_code/article/details/17881581*
>
> []{#_Toc9746 .anchor}*3.4.1 java类加载的过程*
>
> ![](media/image150.png){width="5.763194444444444in"
> height="2.238888888888889in"}

类加载过程

加载

1.  通过一个类的全限名来获取定义此类的二进制节流。（实现这个代码模块就是类加载器）

2.  将这个字节流所代表的静态存储结构转化为方法区的运行时数据结构。

3.  在内存中生成一个代表这个类的java.lang.Class对象,作为方法区这个类的各种数据的访问入口。

验证

文件格式验证\
– \[x\] 是否以魔数0xCAFEBABE开头\
– \[x\] 主次版本号是否在当前虚拟机处理范围之内\
– \[x\] 常量池中的常量是否有不被支持的常量类型\
– \[x\] 指向常量的各种索引值中是否有指向不存在的常量或不符合类型的常量\
– \[x\] CONSTANTUtf8info型的常量中是否有不符合UTF8编码的数据\
– \[x\] Class文件中各个部分及文件本身是否有被删除的或附加的其他信息\
– \[x\] 等等

元数据验证\
– \[x\] 这个类是否有父类\
– \[x\] 这个类的父类是否继承了不准许被继承的类\
– \[x\]
如果这个类不是抽象类,是否实现了其父类或者接口之中要求实现的所有方法\
– \[x\] 类中的字段方法是否与父类产生矛盾\
–\
字节码验证\
– \[x\] 保证任意时刻操作数栈的数据类型与指令代码序列都能配合工作\
– \[x\] 保证跳转指令不会跳转到方法体以外的字节码指令上\
– \[x\] 保证方法体重的类型转换是有效的

符号引用验证\
– \[x\] 符号引用中通过字符串描述的全限定名是否找到相应的类\
– \[x\]
在指定的类中是否存在符合方法的字段描述符以及简单名称说描述的方法和字段\
– \[x\] 符号引用中的类、字段、方法的访问性是否被当前类访问

准备

准备阶段是正式为类变量分配内存并设置类变量初始值(被static修饰的变量)的阶段,这些变量所使用的内存都将在方法区中进行分配

解析

解析阶段就是虚拟机将常量池内的符号引用替换为直接引用的过程

初始化

初始化就是执行类构造器方法的过程

[]{#_Toc32405 .anchor}*3.4.2 双亲委派机制*

> ![](media/image151.png){width="5.761805555555555in"
> height="2.290277777777778in"}
>
> ![](media/image152.png){width="5.7652777777777775in"
> height="3.1479166666666667in"}

[]{#_Toc17496 .anchor}3.4.3 破坏双亲委派模型

1.在JDK1.2之前，用户去继承java.lang.ClassLoader的唯一目的就是为了重写loadClass方法，由于用户自己重写了loadClass，那么也就是用户自己去自定义加载类，故事破坏

2.JDBC,JDNI等的SPI的加载都是父类的加载器去请求子类的加载器去加载累；

3.OSGI的热部署就是自定义类加载器机制的实现；

3.5 内存泄露
------------

![](media/image153.png){width="5.7652777777777775in" height="4.98125in"}

6.  检查内存泄露的工具

![](media/image154.png){width="5.759722222222222in"
height="0.8541666666666666in"}

3.6 .内存泄露的案例分析 jvm调优
-------------------------------

*https://www.cnblogs.com/csniper/p/5592593.html*

*https://mp.weixin.qq.com/s/ydkEkh\_Uc1paftJLKIsm0w*

[]{#_Toc30165 .anchor}3.6.1 jvm调优目的

1.将转移到老年代的对象数量降低到最小；

2.减少fullGC的执行时间

[]{#_Toc26334 .anchor}3.6.2 案例分析

1.案例1（修改NewRatio 可以说有时候访问访问着就会发生卡顿）

（http://www.360doc.com/content/13/0305/10/15643\_269388816.shtml）

一个服务系统，**经常出现卡顿，分析原因，发现Full GC时间太长**：

jstat -gcutil:

S0     S1    E     O       P        YGC YGCT FGC FGCT  GCT

12.16 0.00 5.18 63.78 20.32  54   2.047 5     6.946  8.993 

分析上面的数据，发现Young GC执行了54次，耗时2.047秒，每次Young
GC耗时37ms，在正常范围，**而Full
GC执行了5次，耗时6.946秒，每次平均1.389s，数据显示出来的问题是：Full
GC耗时较长**，分析该系统的是指发现，NewRatio=9，也就是说，新生代和老生代大小之比为1:9，这就是问题的原因：

1，新生代太小，导致对象提前进入老年代，触发老年代发生Full GC；

2，老年代较大，进行Full GC时耗时较大；

优化的方法是调整NewRatio的值，调整到4，发现Full GC没有再发生，只有Young
GC在执行。这就是把对象控制在新生代就清理掉，没有进入老年代（这种做法对一些应用是很有用的，但并不是对所有应用都要这么做）

> 2.案例2（与案例1重复）
>
> ![](media/image155.png){width="5.761805555555555in"
> height="4.60625in"}
>
> ![](media/image156.png){width="5.761111111111111in"
> height="5.623611111111111in"}
>
> ![](media/image157.png){width="5.764583333333333in"
> height="1.836111111111111in"}

3.案例3 (MinorGC时间过长 可以这样说 人物关系提取模块
需要业务上每30分钟加载一个80MB的数据文件到内存进行数据分析（人名字和政党），这些数据会在内存中形成超过100w个HashMap&lt;String,String&gt;
Entry，这段时间会造成1000ms左右的minorGC的停顿）

![](media/image158.png){width="5.766666666666667in"
height="4.718055555555556in"}

![](media/image159.png){width="5.761805555555555in"
height="0.5965277777777778in"}

[]{#_Toc2935 .anchor}3.7 jstat jmap jps jinfo jconsole

[]{#_Toc14398 .anchor}3.7.1 jstat

![](media/image160.png){width="5.759722222222222in"
height="1.9034722222222222in"}

![](media/image161.png){width="5.763194444444444in"
height="3.7319444444444443in"}

[]{#_Toc7460 .anchor}3.7.2 jmap

![](media/image162.png){width="5.759722222222222in"
height="0.5868055555555556in"}

3.7 JVM 参数设置
----------------

**参数说明\
**-Xmx3550m：设置JVM最大堆内存为3550M。**\
**-Xms3550m：设置JVM初始堆内存为3550M。此值可以设置与-Xmx相同，以避免每次垃圾回收完成后JVM重新分配内存。**\
**-Xss128k：设置每个线程的栈大小。JDK5.0以后每个线程栈大小为1M，之前每个线程栈大小为256K。应当根据应用的线程所需内存大小进行调整。在相同物理内存下，减小这个值能生成更多的线程。但是操作系统对一个进程内的线程数还是有限制的，不能无限生成，经验值在3000\~5000左右。需要注意的是：当这个值被设置的较大（例如&gt;2MB）时将会在很大程度上降低系统的性能。**\
**-Xmn2g：设置年轻代大小为2G。在整个堆内存大小确定的情况下，增大年轻代将会减小年老代，反之亦然。此值关系到JVM垃圾回收，对系统性能影响较大，官方推荐配置为整个堆大小的3/8。**\
**-XX:NewSize=1024m：设置年轻代初始值为1024M。**\
**-XX:MaxNewSize=1024m：设置年轻代最大值为1024M。**\
**-XX:PermSize=256m：设置持久代初始值为256M。**\
**-XX:MaxPermSize=256m：设置持久代最大值为256M。**\
**-XX:NewRatio=4：设置年轻代（包括1个Eden和2个Survivor区）与年老代的比值。表示年轻代比年老代为1:4。**\
**-XX:SurvivorRatio=4：设置年轻代中Eden区与Survivor区的比值。表示2个Survivor区（JVM堆内存年轻代中默认有2个大小相等的Survivor区）与1个Eden区的比值为2:4，即1个Survivor区占整个年轻代大小的1/6。**\
**-XX:MaxTenuringThreshold=7：表示一个对象如果在Survivor区（救助空间）移动了7次还没有被垃圾回收就进入年老代。如果设置为0的话，则年轻代对象不经过Survivor区，直接进入年老代，对于需要大量常驻内存的应用，这样做可以提高效率。如果将此值设置为一个较大值，则年轻代对象会在Survivor区进行多次复制，这样可以增加对象在年轻代存活时间，增加对象在年轻代被垃圾回收的概率，减少Full
GC的频率，这样做可以在某种程度上提高服务稳定性。

-XX:PretenureSizeThreshold
直接晋升到老年代的对象大小，设置这个参数后，大于这个参数的对象将直接在老年代分配。

-XX：MaxTenuringThreshold
每次minorGC就增加一次，超过这个值，在from中的对象直接进入到老年代

![](media/image163.png){width="5.761805555555555in" height="3.83125in"}

![](media/image164.png){width="5.766666666666667in"
height="1.8993055555555556in"}

[]{#_Toc2417 .anchor}3.8 内存分配与回收策略

1.对象优先在Eden分配

2.大对象直接进入老年代

![](media/image165.png){width="5.763888888888889in"
height="0.7131944444444445in"}

3.长期存活的对象将进入老年代

![](media/image166.png){width="5.763888888888889in"
height="1.5409722222222222in"}

4.动态对象年龄判定

如果在Survivor空间中相同年龄所有对象大小总和大于Survivor空间的一半，（比如说Survivor空间大小为1M，而有两个年龄为1的对象大小和是大于512K的），那么年龄大于等于该年龄的对象都可以直接进入到老年代。

5.空间分配担保

在进行MinorGC前，虚拟机会查看HandlePromotionFailure设置值是否为True,那么说明允许担保失败（会检查虚拟机老年代剩余空间的大小与平均晋升到老年代空间的大小，如果大于说明“可能”是安全的），为True那么进行一次MinorGC，如果此时刻发现进入到老年代的新对象的大小是大于老年代的剩余空间，说明担保失败了，只能进行一次FullGC清除老年代的剩余空间。

[]{#_Toc11239 .anchor}**3.9 面试问题**

[]{#_Toc18850 .anchor}**3.9.1一般Java堆是如何实现的**？

我：在HotSpot虚拟机实现中，Java堆分成了新生代和老年代，我当时看的是1.7的实现，所有还有永久代，新生代中又分为了eden区和survivor区，survivor区又分成了S0和S1，或则是from和to，（这个时候，我要求纸和笔，因为我觉得这个话题可以聊蛮长时间，又是我比较熟悉的...一边画图，一边描述），其中eden，from和to的内存大小默认是8:1:1（各种细节都要说出来...），此时，我已经在纸上画出了新生代和老年代代表的区域

### 3.9.2 对象在内存中的初始化过程

参考：1.https://blog.csdn.net/WantFlyDaCheng/article/details/81808064 \
2.《深入理解java虚拟机》 

原文：https://blog.csdn.net/WantFlyDaCheng/article/details/81808244\
Student s = new Student() 为例 \
1.首先查看类的符号引用，看是否已经在常量池中，在说明已经加载过了，不在的话需要进行类的加载，验证，准备，解析，初始化的过程。 \
2.上诉过程执行完毕以后，又将Student加载进内存，也就是存储Student.class的字段信息和方法信息，存储到方法区中 \
字段信息：存放类中声明的每一个字段的信息，包括字段的名、类型、修饰符。 \
方法信息：类中声明的每一个方法的信息，包括方法名、返回值类型、参数类型、修饰符、异常、方法的字节码。 \
3。然后在自己的线程私有的虚拟机栈中，存储该引用，然后在每个线程的私有空间里面去分配空间存储new
Student(),如果空间不足在eden区域进行分配空间 \
4，对类中的成员变量进行默认初始化 \
5，对类中的成员变量进行显示初始化 \
6，有构造代码块就先执行构造代码块，如果没有，则省略(此步上文未体现) \
7，执行构造方法，通过构造方法对对对象数据进行初始化 \
8，堆内存中的数据初始化完毕，把内存值复制给 s 变量

[]{#_Toc5956 .anchor}3.9.3 **对象的强、软、弱和虚引用**

**⑴强引用（StrongReference）**\
强引用是使用最普遍的引用。如果一个对象具有强引用，那垃圾回收器绝不会回收它。

**⑵软引用（SoftReference）**\
如果一个对象只具有软引用，则内存空间足够，垃圾回收器就不会回收它；如果内存空间不足了，就会回收这些对象的内存

**⑶弱引用（WeakReference）**\
弱引用与软引用的区别在于：只具有弱引用的对象拥有更短暂的生命周期。在垃圾回收器线程扫描它所管辖的内存区域的过程中，一旦发现了只具有弱引用的对象，不管当前内存空间足够与否，都会回收它的内存

**⑷虚引用（PhantomReference）**\
“虚引用”顾名思义，就是形同虚设，与其他几种引用都不同，虚引用并不会决定对象的生命周期。如果一个对象仅持有虚引用，那么它就和没有任何引用一样，在任何时候都可能被垃圾回收器回收。

[]{#_Toc21561 .anchor}3.9.4 如何减少GC的次数

1.对象不用时最好显示置为NULL

   
一般而言，为NULL的对象都会被作为垃圾处理，所以将不用的对象置为NULL，有利于GC收集器判定垃圾，从而提高了GC的效率。

2.尽量少使用System,gc()

    此函数建议JVM进行主GC，会增加主GC的频率，增加了间接性停顿的次数。

3.尽量少使用静态变量

    静态变量属于全局变量，不会被GC回收，他们会一直占用内存

4.尽量使用StringBuffer,而不使用String来累加字符串

5.分散对象创建或删除的时间

   
集中在短时间内大量创建新对象，特别是大对象，会导致突然需要大量内存，JVM在这种

    情况下只能进行主GC以回收内存，从而增加主GC的频率。

6.尽量少用finaliza函数

    它会加大GC的工作量。

7.如果有需要使用经常用到的图片，可以使用软引用类型，将图片保存在内存中，而不引起outofmemory

8.能用基本类型入INT就不用对象Integer

9.增大-Xmx的值

[]{#_Toc16265 .anchor}3.9.5 新生代 老年代 永久代

**年轻代：**

　　事实上，在上一节，已经介绍了新生代的主要垃圾回收方法，在新生代中，使用“停止-复制”算法进行清理，将新生代内存分为2部分，1部分
Eden区较大，1部分Survivor比较小，并被划分为两个等量的部分。每次进行清理时，将Eden区和一个Survivor中仍然存活的对象拷贝到
另一个Survivor中，然后清理掉Eden和刚才的Survivor。

　　这里也可以发现，停止复制算法中，用来复制的两部分并不总是相等的（传统的停止复制算法两部分内存相等，但新生代中使用1个大的Eden区和2个小的Survivor区来避免这个问题）

　　由于绝大部分的对象都是短命的，甚至存活不到Survivor中，所以，Eden区与Survivor的比例较大，HotSpot默认是
8:1，即分别占新生代的80%，10%，10%。如果一次回收中，Survivor+Eden中存活下来的内存超过了10%，则需要将一部分对象分配到
老年代。用-XX:SurvivorRatio参数来配置Eden区域Survivor区的容量比值，默认是8，代表Eden：Survivor1：Survivor2=8:1:1.

　　**老年代：**

　　老年代存储的对象比年轻代多得多，而且不乏大对象，对老年代进行内存清理时，如果使用停止-复制算法，则相当低效。一般，老年代用的算法是标记-整理算法，即：标记出仍然存活的对象（存在引用的），将所有存活的对象向一端移动，以保证内存的连续。

     在发生Minor
GC时，虚拟机会检查每次晋升进入老年代的大小是否大于老年代的剩余空间大小，如果大于，则直接触发一次Full
GC，否则，就查看是否设置了-XX:+HandlePromotionFailure（允许担保失败），如果允许，则只会进行MinorGC，此时可以容忍内存分配失败；如果不允许，则仍然进行Full
GC（这代表着如果设置-XX:+Handle
PromotionFailure，则触发MinorGC就会同时触发Full
GC，哪怕老年代还有很多内存，所以，最好不要这样做）。

　　**方法区（永久代）：**

　　永久代的回收有两种：常量池中的常量，无用的类信息，常量的回收很简单，没有引用了就可以被回收。对于无用的类进行回收，必须保证3点：

1.  类的所有实例都已经被回收

2.  加载类的ClassLoader已经被回收

3.  类对象的Class对象没有被引用（即没有通过反射引用该类的地方）

   
 永久代的回收并不是必须的，可以通过参数来设置是否对类进行回收。HotSpot提供-Xnoclassgc进行控制

   
 使用-verbose，-XX:+TraceClassLoading、-XX:+TraceClassUnLoading可以查看类加载和卸载信息

     -verbose、-XX:+TraceClassLoading可以在Product版HotSpot中使用；

     -XX:+TraceClassUnLoading需要fastdebug版HotSpot支持

如何加快gc的速度 快速判断对象生死

垃圾收机制简述，堆，栈，如何判断对象已死，有环root链如何找到了？

线程安全 java里面的实现方式

如果我们一个项目，理论上需要1.5G的内存就足够，但是项目上线后发现隔了几个星期，占用内存到了2.5G，这时候你会考虑是什么问题？怎么解决？

可能造成内存泄漏的原因有哪些？检查内存泄漏的工具有哪些？你平时是怎么检查内存泄漏的？\
jvm 多态原理。invokestatic  invokeinterface 等指令。常量池中的符号引用
找到直接引用。在堆中找到实例对象，获取到偏移量，由偏移量在方法表中指出调用的具体方法。接口是在方法表中进行扫描）等等扯了半天 

7.  []{#_Toc21570 .anchor}**juc包**

    ***https://blog.csdn.net/china\_wanglong/article/details/38828407***

    []{#_Toc6800 .anchor}**7.0 juc概况**

    ![](media/image167.png){width="5.75in"
    height="3.9166666666666665in"}

    []{#_Toc24807 .anchor}**7.1 Tools**

    []{#_Toc3597 .anchor}7.1.1 CountDownLatch

    这个类是一个同步计数器，主要用于线程间的控制，当CountDownLatch的count计数&gt;0时，await()会造成阻塞，直到count变为0，await()结束阻塞，使用countDown()会让count减1。CountDownLatch的构造函数可以设置count值，当count=1时，它的作用类似于wait()和notify()的作用。如果我想让其他线程执行完指定程序，其他所有程序都执行结束后我再执行，这时可以用CountDownLatch，但计数无法被重置，如果需要重置计数，请考虑使用
    CyclicBarrier 。

    []{#_Toc25167 .anchor}7.1.2 CyclicBarrier

    该类从字面理解为循环屏障，它可以协同多个线程，让多个线程在这个屏障前等到，直到所有线程都到达了这个屏障时，再一起执行后面的操作。假如每个线程各有一个await，任何一个线程运行到await方法时就阻塞，直到最后一个线程运行到await时才同时返回。和之前的CountDownLatch相比，它只有await方法，而CountDownLatch是使用countDown()方法将计数器减到0，它创建的参数就是countDown的数量；CyclicBarrier创建时的int参数是await的数量。

    []{#_Toc32219 .anchor}7.1.3 Semaphore

    该类用于控制信号量的个数，构造时传入个数。总数就是控制并发的数量。假如是5，程序执行前用acquire()方法获得信号，则可用信号变为4，程序执行完通过release()方法归还信号量，可用信号又变为5.如果可用信号为0，acquire就会造成阻塞，等待release释放信号。acquire和release方法可以不在同一个线程使用。Semaphore实现的功能就类似厕所有5个坑，假如有10个人要上厕所，那么同时只能有多少个人去上厕所呢？同时只能有5个人能够占用，当5个人中
    的任何一个人让开后，其中等待的另外5个人中又有一个人可以占用了。另外等待的5个人中可以是随机获得优先机会，也可以是按照先来后到的顺序获得机会，这取决于构造Semaphore对象时传入的参数选项。单个信号量的Semaphore对象可以实现互斥锁的功能，并且可以是由一个线程获得了“锁”，再由另一个线程释放“锁”，这可应用于死锁恢复的一些场合。

    []{#_Toc8174 .anchor}7.1.4 Exchanger

    这个类用于交换数据，只能用于两个线程。当一个线程运行到exchange()方法时会阻塞，另一个线程运行到exchange()时，二者交换数据，然后执行后面的程序。

    []{#_Toc25222 .anchor}7.2 List Set

    CopyOnWriteArrayList, CopyOnWriteArraySet和ConcurrentSkipListSet

    []{#_Toc19323 .anchor}**7.3 Map**

    ConcurrentHashMap和ConcurrentSkipListMap

    []{#_Toc15573 .anchor}7.4 Queue

     ArrayBlockingQueue, LinkedBlockingQueue, LinkedBlockingDeque, ConcurrentLinkedQueue和ConcurrentLinkedDeque

### **7.4.1 ArrayBlockingQueue**

1.基于数组实现，保证并发的安全性是基于ReetrantLock和Condition实现的。其中有两个重要的成员变量putindex和takeindex,这两个需要搞懂，putindex就是指向数组中上一个添加完元素的位置的下一个地方，比如刚在index=1的位置添加完，那么putindex就是2，**其中有一点特别注意的就是当index=数组的长度减一的时候，意味着数组已经到了满了，那么需要将putindex置位0**，原因是数组在被消费的也就是取出操作的时候，是从数组的开始位置取得，所以最开始的位置容易是空的，所以把要添加的位置置位0；takeindex也是一样的，当takeindex到了数组的长度减一的时候，也需要将takeindex置为0。 \
2.**add offer put** \
add调用了offer方法 add方法数组满了则抛出异常 \
offer方法：**用ReetracLock加锁**，首先判断数组是否满了，数组满了则返回false，数组不满的话直接入队，也就是将putindex索引处的值置为新要加入的数，如果加入以后发现putindex++
=
数组的长度，那么说明后面的全部已经填满了，因此putindex置为0，因为前面的可能出队的过程空出来了，所以变为0，最后一步就是执行notEmpty.signal去唤醒消费的执行了take的线程，只有可能是执行了take的方法的线程，因为执行了其它方法remove,poll不会产生线程的挂起操作。 \
put:首先是ReetrantLock加锁，然后判断是否满了，队列满了，则执行notFull.await()操作挂起，等待notFull.signal(）唤醒。没满，则直接进行入队，入队和offer操作一样，也就是将putindex索引处的值置为新要加入的数，如果加入以后发现putindex++
=
数组的长度，那么说明后面的全部已经填满了，因此putindex置为0，因为前面的可能出队的过程空出来了，所以变为0，最后一步就是执行notEmpty()去唤醒消费的执行了take的线程 \
3.**remove,poll,take** \
poll 首先加锁ReetranLock
,然后判断队列是否为空，不为空，则将putindex出的值用副本copy,然后置位null,然后去执行唤醒notFull()操作，也就是唤醒调用了put操作的线程，唤醒操作并不一定总是发生。 \
take操作，先加锁，然后如果队列空则notEmpty.await()方法，不为空，则执行和poll一样的出队操作：则将putindex出的值用副本copy,然后置位null,然后去执行唤醒notFull()操作

### **7.4.2** **LinkedBlockingQueue**

1.基于链表实现，有takelock和putlock，也就是说可以同时在首尾两端进行操作，因此吞吐量比ArrayBlockingQueue大，同时由于首尾两端都可以进行操作，所以当在进行添加的操作的过程可以一直去添加，直到没有被阻塞的添加线程为止，然后才去执行消费的线程。 \
**1.add,offer,put** \
add调用offer,满了抛出异常 \
offer方法 **putlock锁**，然后不满则加入，同时获取一个c值，c值代表本次队列增加前的队列的数目（一开始长度2，增加1，现在长度是3，那么c就是2），然后判断如果不满则继续去唤醒notFull.signl，去唤醒添加线程去添加（添加过程是直接last节点指向下一个，简单的节点后增加一个节点，然后last指向最后一个节点），上述过程结束，然后去判断
c==0(c代表了之前的队列长度，如果添加之前队列长度是0那么说明可能有挂起的消费线程，需要从队列取元素，但队列长度为0没有元素；判断c&gt;0没有意义，因为添加之前队列不为空，说明不存在挂起的消费线程，挂起的原因是因为队列为空，所以不存在因此源码是判断c==0）
，c如果等于0那么去唤醒阻塞的notEmpty上的条件等待线程。 \
put
操作就是满了则挂起，不满则执行，同时添加完一个后，发现没满继续去唤醒挂起的添加线程 \
**2.poll take** \
反之，一样的逻辑 \
poll
则获取**takelcok** 然后不为空则出队一个元素，也就是链表的删除头结点操作，通过是如果队列不为空，那么继续去唤醒被挂起的消费线程（消费线程就是执行了队列的take操作的线程），直到没有消费线程或者队列为空，结束，然后如果c（也是队列消费一个头节点的元素后，没消费之前的长度，没发生删除的时候队列的长度），如果c的长度已经是队列的长度，则去唤醒被挂起的执行了put方法的线程，然后释放takelock锁 \
take方法一样的道理，为空则挂起，不为空一直消费，唤起消费线程一直消费，直到条件不满足，那么去尝试判断c的值，c是队列长度减一，那么去唤醒执行了put方法的被挂起的线程。 \
以下内容来自 深入剖析java并发之阻塞队列LinkedBlockingQueue与ArrayBlockingQueu

[]{#_Toc8510 .anchor}**7.4.3 LinkedBlockingQueue 和ArrayBlockingQueue
迥异**

通过上述的分析，对于LinkedBlockingQueue和ArrayBlockingQueue的基本使用以及内部实现原理我们已较为熟悉了，这里我们就对它们两间的区别来个小结

1.队列大小有所不同，ArrayBlockingQueue是有界的初始化必须指定大小，而LinkedBlockingQueue可以是有界的也可以是无界的(Integer.MAX\_VALUE)，对于后者而言，当添加速度大于移除速度时，在无界的情况下，可能会造成内存溢出等问题。

2.数据存储容器不同，ArrayBlockingQueue采用的是数组作为数据存储容器，而LinkedBlockingQueue采用的则是以Node节点作为连接对象的链表。

3.由于ArrayBlockingQueue采用的是数组的存储容器，因此在插入或删除元素时不会产生或销毁任何额外的对象实例，而LinkedBlockingQueue则会生成一个额外的Node对象。这可能在长时间内需要高效并发地处理大批量数据的时，对于GC可能存在较大影响。

4.两者的实现队列添加或移除的锁不一样，ArrayBlockingQueue实现的队列中的锁是没有分离的，即添加操作和移除操作采用的同一个ReenterLock锁，而LinkedBlockingQueue实现的队列中的锁是分离的，其添加采用的是putLock，移除采用的则是takeLock，这样能大大提高队列的吞吐量，也意味着在高并发的情况下生产者和消费者可以并行地操作队列中的数据，以此来提高整个队列的并发性能。

[]{#_Toc1504 .anchor}7.5 线程池

### **1.线程池工作原理**

线程池中的核心线程数，当提交一个任务时，线程池创建一个新线程执行任务，直到当前线程数等于corePoolSize；如果当前线程数为corePoolSize，继续提交的任务被保存到阻塞队列中，等待被执行；如果阻塞队列满了，那就创建新的线程执行当前任务；直到线程池中的线程数达到maxPoolSize,这时再有任务来，只能执行reject()处理该任务； 

### **2.线程池分类**

4种类型的线程池： \
newFixedThreadPool() \
说明：初始化一个指定线程数的线程池，其中corePoolSize ==
maxiPoolSize，使用LinkedBlockingQuene作为阻塞队列 \
特点：即使当线程池没有可执行任务时，也不会释放线程。 \
newCachedThreadPool() \
说明：初始化一个可以缓存线程的线程池，默认缓存60s，线程池的线程数可达到Integer.MAX\_VALUE，即2147483647，内部使用SynchronousQueue作为阻塞队列； \
特点：在没有任务执行时，当线程的空闲时间超过keepAliveTime，会自动释放线程资源；当提交新任务时，如果没有空闲线程，则创建新线程执行任务，会导致一定的系统开销； \
因此，使用时要注意控制并发的任务数，防止因创建大量的线程导致而降低性能。 \
newSingleThreadExecutor() \
说明：初始化只有一个线程的线程池，内部使用LinkedBlockingQueue作为阻塞队列。 \
特点：如果该线程异常结束，会重新创建一个新的线程继续执行任务，唯一的线程可以保证所提交任务的顺序执行 \
newScheduledThreadPool() \
特定：初始化的线程池可以在指定的时间内周期性的执行所提交的任务，在实际的业务场景中可以使用该线程池定期的同步数据。

总结：除了newScheduledThreadPool的内部实现特殊一点之外，其它线程池内部都是基于ThreadPoolExecutor类（Executor的子类）实现的。

### **3.线程池底层实现类ThreadPoolExecutor类**

**ThreadPoolExecutor（corePoolSize,maxPoolSize,keepAliveTime,timeUnit,workQueue,threadFactory,handle); **\
**corePoolSize** \
线程池中的核心线程数，当提交一个任务时，线程池创建一个新线程执行任务，直到当前线程数等于corePoolSize；如果当前线程数为corePoolSize，继续提交的任务被保存到阻塞队列中，等待被执行；如果执行了线程池的prestartAllCoreThreads()方法，线程池会提前创建并启动所有核心线程。

**maximumPoolSize** \
线程池中允许的最大线程数。如果当前阻塞队列满了，且继续提交任务，则创建新的线程执行任务，前提是当前线程数小于maximumPoolSize；

**keepAliveTime** \
线程空闲时的存活时间，即当线程没有任务执行时，继续存活的时间；默认情况下，该参数只在线程数大于corePoolSize时才有用；

**unit** \
keepAliveTime的单位；

**workQueue** \
用来保存等待被执行的任务的阻塞队列，且任务必须实现Runable接口，在JDK中提供了如下阻塞队列： \
1、ArrayBlockingQueue：基于数组结构的有界阻塞队列，按FIFO排序任务； \
2、LinkedBlockingQuene：基于链表结构的阻塞队列，按FIFO排序任务，吞吐量通常要高于ArrayBlockingQuene； \
3、SynchronousQuene：一个不存储元素的阻塞队列，每个插入操作必须等到另一个线程调用移除操作，否则插入操作一直处于阻塞状态，吞吐量通常要高于LinkedBlockingQuene； \
4、priorityBlockingQuene：具有优先级的无界阻塞队列；

threadFactory \
创建线程的工厂，通过自定义的线程工厂可以给每个新建的线程设置一个具有识别度的线程名。 \
**handler** \
线程池的饱和策略，**当阻塞队列满了，且没有空闲的工作线程**，如果继续提交任务，必须采取一种策略处理该任务，线程池提供了4种策略： \
1、AbortPolicy：直接抛出异常，默认策略； \
2、CallerRunsPolicy：用调用者所在的线程来执行任务； \
3、DiscardOldestPolicy：丢弃阻塞队列中靠最前的任务，并执行当前任务； \
4、DiscardPolicy：直接丢弃任务； \
当然也可以根据应用场景实现**RejectedExecutionHandler**接口，自定义饱和策略，如记录日志或持久化存储不能处理的任务。

### **4.线程池状态**

RUNNING 自然是运行状态，指可以接受任务执行队列里的任务 \
SHUTDOWN 指调用了 shutdown()
方法，不再接受新任务了，但是队列里的任务得执行完毕。 \
STOP 指调用了 shutdownNow()
方法，不再接受新任务，同时抛弃阻塞队列里的所有任务并中断所有正在执行任务。 \
TIDYING 所有任务都执行完毕，在调用 shutdown()/shutdownNow()
中都会尝试更新为这个状态。 \
TERMINATED 终止状态，当执行 terminated() 后会更新为这个状态 

四.设计模式
===========

[]{#_Toc14847 .anchor}4.0 什么是设计模式

> 在软件工程中，设计模式（design
> pattern）是对软件设计中普遍存在（反复出现）的各种问题，所提出的解决方案。

[]{#_Toc22112 .anchor}4.1.常见的设计模式及其JDK中案例：

> []{#_Toc10990 .anchor}4.1.1 适配器模式
>
> ![](media/image169.png){width="5.010416666666667in"
> height="1.0729166666666667in"}
>
> java.util.Arrays\#asList()
>
> java.io.InputStreamReader(InputStream)
>
> java.io.OutputStreamWriter(OutputStream)
>
> []{#_Toc10717 .anchor}4.1.2 迭代器模式
>
> ![](media/image170.png){width="5.010416666666667in"
> height="0.5520833333333334in"}
>
> 提供一个一致的方法来顺序访问集合中的对象，这个方法与底层的集合的具体实现无关。
>
> JDK中：
>
> java.util.Iterator
>
> java.util.Enumeration
>
> []{#_Toc2618 .anchor}4.1.3 代理模式
>
> 代理（proxy）模式：指目标对象给定代理对象，并由代理对象代替真实对象控制客户端对真实对象的访问。\
> 代理模式模式有以下角色：\
> 抽象主题（subject）角色：声明真实主题和代理主题的共同接口。\
> 真实主题（real subject）角色：定义代理对象需要代理的真实对象。\
> 代理主题（proxy
> subject）角色：代替真实对象来控制对真实对象的访问，代理对象持有真实对象的应用，从而可以随时控制客户端对真实对象的访问。
>
> 实例：大话设计模式：
>
> ![](media/image171.png){width="5.197916666666667in"
> height="2.6354166666666665in"}
>
> ![](media/image172.png){width="5.572916666666667in"
> height="2.7916666666666665in"}
>
> JDK：java.lang.reflect.Proxy RMI
>
> []{#_Toc6362 .anchor}4.1.4 观察者模式
>
> ![](media/image173.png){width="5.7659722222222225in"
> height="4.797916666666667in"}
>
> Jdk : java.util.EventListener
>
> javax.servlet.http.HttpSessionBindingListener
>
> javax.servlet.http.HttpSessionAttributeListener
>
> javax.faces.event.PhaseListener
>
> []{#_Toc18499 .anchor}4.1.5 装饰器模式
>
> 动态的给一个对象附加额外的功能，这也是子类的一种替代方式。可以看到，在创建一个类型的时候，同时也传入同一类型的对象。这在JDK里随处可见，你会发现它无处不在，所以下面这个列表只是一小部分。
>
> 装饰原有对象、在不改变原有对象的情况下扩展增强新功能/新特征.。当不能采用继承的方式对系统进行扩展或者采用继承不利于系统扩展和维护时可以使用装饰模式。
>
> Jdk
> :装饰者模式通过包含一个原有的Inputstream对象，并且将InputStream原有的方法或直接暴露，或进行装饰后暴露，又或者添加了新的特性，如DataInputStream中的readInt()，BufferedInputStream中的缓存功能。(这些新的功能就是装饰后新添加的）
>
> java.io.BufferedInputStream(InputStream)
>
> java.io.DataInputStream(InputStream)
>
> java.io.BufferedOutputStream(OutputStream)
>
> java.util.zip.ZipOutputStream(OutputStream)
>
> java.util.Collections\#checkedList|Map|Set|SortedSet|SortedMap

[]{#_Toc10460 .anchor}4.1.6 工厂模式

> ![](media/image174.png){width="5.761805555555555in"
> height="0.9847222222222223in"}
>
> 简单工厂：把对象的创建放到一个工厂类中，通过参数来创建不同的对象。 \
> 工厂方法：每种产品由一种工厂来创建。（不这样会有什么问题？） \
> 抽象工厂：感觉只是工厂方法的复杂化，产品系列复杂化的工厂方法。
>
> 工厂方法模式：就是一个返回具体对象的方法。
>
> java.lang.Proxy\#newProxyInstance()
>
> java.lang.Object\#toString()
>
> java.lang.Class\#newInstance()
>
> java.lang.reflect.Array\#newInstance()
>
> java.lang.reflect.Constructor\#newInstance()
>
> java.lang.Boolean\#valueOf(String)
>
> java.lang.Class\#forName()
>
> 抽象工厂模式

抽象工厂模式提供了一个协议来生成一系列的相关或者独立的对象，而不用指定具体对象的类型。它使得应用程序能够和使用的框架的具体实现进行解耦。这在JDK或者许多框架比如Spring中都随处可见。它们也很容易识别，一个创建新对象的方法，返回的却是接口或者抽象类的，就是抽象工厂模式了。

java.util.Calendar\#getInstance()

java.util.Arrays\#asList()

java.util.ResourceBundle\#getBundle()

java.sql.DriverManager\#getConnection()

java.sql.Connection\#createStatement()

java.sql.Statement\#executeQuery()

java.text.NumberFormat\#getInstance()

javax.xml.transform.TransformerFactory\#newInstance()

[]{#_Toc30845 .anchor}4.1.7 建造者模式

 
定义了一个新的类来构建另一个类的实例，以简化复杂对象的创建。建造模式通常也使用方法链接来实现。

java.lang.StringBuilder\#append()

java.lang.StringBuffer\#append()

java.sql.PreparedStatement

javax.swing.GroupLayout.Group\#addComponent()

例如StringBuilder就是定义了一个新类StringBuilder 来完成“aa”+ “bb”的创建

System.Text.StringBuilder sb = new StringBuilder();

 sb.Append("aa");//添加的子对象部分(**这就是创建 子对象的部分**)

 sb.Append("bb");(**这个就对应 GetResult()**)

 string str=  sb.ToString();//**最终 都演变成 最后一种形式**

[]{#_Toc15239 .anchor}4.1.8 命令模式

![](media/image175.png){width="5.767361111111111in"
height="4.146527777777778in"}

[]{#_Toc2580 .anchor}4.1.9 责任链模式

通过把请求从一个对象传递到链条中下一个对象的方式，直到请求被处理完毕，以实现对象间的解耦。

 

java.util.logging.Logger\#log()

javax.servlet.Filter\#doFilter()

[]{#_Toc3870 .anchor}4.1.10 享元模式

![](media/image176.png){width="4.666666666666667in"
height="0.5729166666666666in"}

Flyweight 享元模式：

使用缓存来加速大量小对象的访问时间。

java.lang.Integer\#valueOf(int)

java.lang.Boolean\#valueOf(boolean)

java.lang.Byte\#valueOf(byte)

java.lang.Character\#valueOf(char)

[]{#_Toc18140 .anchor}4.1.11 中介者模式

中介者模式

通过使用一个中间对象来进行消息分发以及减少类之间的直接依赖。 

java.util.Timer

java.util.concurrent.Executor\#execute()

java.util.concurrent.ExecutorService\#submit()

java.lang.reflect.Method\#invoke()

[]{#_Toc16449 .anchor}4.1.12 备忘录模式

生成对象状态的一个快照，以便对象可以恢复原始状态而不用暴露自身的内容。Date对象通过自身内部的一个long值来实现备忘录模式。

java.util.Date

java.io.Serializable

[]{#_Toc21162 .anchor}4.1.13 组合模式

Composite 组合模式：

又叫做部分-整体模式，使得客户端看来单个对象和对象的组合是同等的。换句话说，某个类型的方法同时也接受自身类型作为参数。

avax.swing.JComponent\#add(Component)

java.util.Map\#putAll(Map)

java.util.List\#addAll(Collection)

java.util.Set\#addAll(Collection)

[]{#_Toc15959 .anchor}4.1.14 模板方法模式

模板方法模式

让子类可以重写方法的一部分，而不是整个重写，你可以控制子类需要重写那些操作。

 

java.util.Collections\#sort()

java.io.InputStream\#skip()

java.io.InputStream\#read()

java.util.AbstractList\#indexOf()

[]{#_Toc30341 .anchor}4.1.15 单例模式

这种模式涉及到一个单一的类，该类负责创建自己的对象，同时确保只有单个对象被创建。这个类提供了一种访问其唯一的对象的方式，可以直接访问，不需要实例化该类的对象。

*https://www.cnblogs.com/cielosun/p/6582333.html*

*https://blog.csdn.net/u014590757/article/details/79818702*

[]{#_Toc28807 .anchor}1.非线程安全懒汉模式

public class SingletonDemo {

private static SingletonDemo instance;

private SingletonDemo(){

}

public static SingletonDemo getInstance(){

if(instance==null){

instance=new SingletonDemo();

}

return instance;

}

}

2.  []{#_Toc7764 .anchor}线程安全懒汉模式

public class SingletonDemo {

private static SingletonDemo instance;

private SingletonDemo(){

}

public static synchronized SingletonDemo getInstance(){

if(instance==null){

instance=new SingletonDemo();

}

return instance;

}

}

[]{#_Toc30504 .anchor}3.饿汉模式

直接在运行这个类的时候进行一次loading，之后直接访问。显然，这种方法没有起到lazy
loading的效果，考虑到前面提到的和静态类的对比，这种方法只比静态类多了一个内存常驻而已。

public class SingletonDemo {

private static SingletonDemo instance=new SingletonDemo();

private SingletonDemo(){

}

public static SingletonDemo getInstance(){

return instance;

}

}

> []{#_Toc25834 .anchor}4. 静态类内部加载
>
> 使用内部类的好处是，静态内部类不会在单例加载时就加载，而是在调用getInstance()方法时才进行加载，达到了类似懒汉模式的效果，而这种方法又是线程安全的。

public class SingletonDemo {

private static class SingletonHolder{

private static SingletonDemo instance=new SingletonDemo();

}

private SingletonDemo(){

System.out.println("Singleton has loaded");

}

public static SingletonDemo getInstance(){

return SingletonHolder.instance;

}

}

> []{#_Toc5653 .anchor}5.双重锁校验模式

public class SingletonDemo {

private **volatile** static SingletonDemo instance;

private SingletonDemo(){

System.out.println("Singleton has loaded");

}

public static SingletonDemo getInstance(){

if(instance==null){

synchronized (SingletonDemo.class){

if(instance==null){

instance=new SingletonDemo();

}

}

}

return instance;

}

}

接下来我解释一下在并发时，双重校验锁法会有怎样的情景：

STEP 1.
线程A访问getInstance()方法，因为单例还没有实例化，所以进入了锁定块。

STEP 2.
线程B访问getInstance()方法，因为单例还没有实例化，得以访问接下来代码块，而接下来代码块已经被线程1锁定。

STEP 3.
线程A进入下一判断，因为单例还没有实例化，所以进行单例实例化，成功实例化后退出代码块，解除锁定。

STEP 4.
线程B进入接下来代码块，锁定线程，进入下一判断，因为已经实例化，退出代码块，解除锁定。

STEP 5.
线程A初始化并获取到了单例实例并返回，线程B获取了在线程A中初始化的单例。

理论上双重校验锁法是线程安全的，并且，这种方法实现了lazyloading。

6.  []{#_Toc10670 .anchor}懒汉模式与饿汉模式区别

> 饿汉模式是最简单的一种实现方式，饿汉模式在类加载的时候就对实例进行创建，实例在整个程序周期都存在。它的好处是只在类加载的时候创建一次实例，不会存在多个线程创建多个实例的情况，避免了多线程同步的问题。**它的缺点也很明显，即使这个单例没有用到也会被创建，而且在类加载之后就被创建，内存就被浪费了。**

6.  []{#_Toc30284 .anchor}**双重校验锁方法与线程安全的懒汉模式区别**

>  
>   可以看到上面在同步代码块外多了一层instance为空的判断。由于单例对象只需要创建一次，如果后面再次调用getInstance()只需要直接返回单例对象。因此，**大部分情况下，调用getInstance()都不会执行到同步代码块，**从而提高了程序性能。不过还需要考虑一种情况，假如两个线程A、B，A执行了if
> (instance ==
> null)语句，它会认为单例对象没有创建，此时线程切到B也执行了同样的语句，B也认为单例对象没有创建，然后**两个线程依次执行同步代码块，并分别创建了一个单例对象。**为了解决这个问题，还需要在同步代码块中增加if(instance
> == null)语句，也就是上面看到的代码2。

6.  **单例模式与静态变量区别**

> 首先解决引用的唯一实例可能被重新赋值的问题，单例模式中的getInstance()静态方法实现时，1.采用懒汉式创建一个对象（当然这只是创建方式的一种），规避了这一风险，无则创建，有则跳过创建。2.其次，getInstance()静态方法定义在该类的内部，获取该类对象的引用位置非常明确，无需额外的沟通商定，团队成员拿起即用。最后一个区别并不是很明显，声明一个静态变量，4.实际上，我们会直接对其进行初始化赋值，这样，在内存占用上，所占用的内存为该初始化赋值对象实际的内存。而单例模式可以通过懒汉创建法延迟该内存的占用，要知道，当一个静态变量只进行声明，而不进行初始化时，实际的内存占用只有4个字节

[]{#_Toc17443 .anchor}4.2 设计模式六大原则

*https://www.cnblogs.com/dolphin0520/p/3919839.html*

1.**单一职责原则(Single Responsibility Principle,
SRP)：一个类只负责一个功能领域中的相应职责，或者可以定义为：就一个类而言，应该只有一个引起它变化的原因。**

**2.开闭原则(Open-Closed Principle,
OCP)：一个软件实体应当对扩展开放，对修改关闭。即软件实体应尽量在不修改原有代码的情况下进行扩展。**

**3.里氏代换原则(Liskov Substitution Principle,
LSP)：所有引用基类（父类）的地方必须能透明地使用其子类的对象。**

**4.依赖倒转原则(Dependency Inversion  Principle,
DIP)：抽象不应该依赖于细节，细节应当依赖于抽象。换言之，要针对接口编程，而不是针对实现编程**

**5.接口隔离原则(Interface  Segregation Principle,
ISP)：使用多个专门的接口，而不使用单一的总接口，即客户端不应该依赖那些它不需要的接口。**

**6.迪米特法则(Law of  Demeter,
LoD)：一个软件实体应当尽可能少地与其他实体发生相互作用**

[]{#_Toc8631 .anchor}4.3 java动态代理

*http://www.cnblogs.com/xiaoluo501395377/p/3383130.html*

在java的动态代理机制中，有两个重要的类或接口，一个是
InvocationHandler(Interface)、另一个则是
Proxy(Class)，这一个类和接口是实现我们动态代理所必须用到的。首先我们先来看看java的API帮助文档是怎么样对这两个类进行描述的：

1.InvocationHandler:

每一个动态代理类都必须要实现InvocationHandler这个接口，并且每个代理类的实例都关联到了一个handler，当我们通过代理对象调用一个方法的时候，这个方法的调用就会被转发为由InvocationHandler这个接口的
invoke
方法来进行调用。我们来看看InvocationHandler这个接口的唯一一个方法 invoke 方法

Object invoke(Object proxy, Method method, Object\[\] args) throws
Throwable

**proxy**:　　**指代我们所代理的那个真实对象**

**method**:　　**指代的是我们所要调用真实对象的某个方法的Method对象**

**args**:　　**指代的是调用真实对象某个方法时接受的参数**

> **2.Proxy**
>
> Proxy这个类的作用就是用来动态创建一个代理对象的类，它提供了许多的方法，但是我们用的最多的就是 newProxyInstance 这个方法：

public static Object newProxyInstance(ClassLoader loader,
Class&lt;?&gt;\[\] interfaces, InvocationHandler h) throws
IllegalArgumentException

loader:　　一个ClassLoader对象，定义了由哪个ClassLoader对象来对生成的代理对象进行加载

interfaces:　　一个Interface对象的数组，表示的是我将要给我需要代理的对象提供一组什么接口，如果我提供了一组接口给它，那么这个代理对象就宣称实现了该接口(多态)，这样我就能调用这组接口中的方法了

h:　　一个InvocationHandler对象，表示的是当我这个动态代理对象在调用方法的时候，会关联到哪一个InvocationHandler对象上

个人理解：就是说通过Proxy的ProxyInstance类创建出一个代理类，这个代理类执行的关于它代理的对象（真正的对象）的方法（代理类可以自己定义自己的方法，要区别），通过一个
InvocationHandler，InvocationHandler是一个接口，接口中有invoke方法，invoke方法关联到一个真正的对象，然后去执行真正对象的方法，来实现代理。

![](media/image177.png){width="5.759722222222222in" height="3.0875in"}

![](media/image178.png){width="5.75625in" height="0.2534722222222222in"}

![](media/image179.png){width="5.768055555555556in"
height="4.271527777777778in"}

![](media/image180.png){width="5.768055555555556in"
height="0.5972222222222222in"}

![](media/image181.png){width="5.768055555555556in" height="5.1125in"}

![](media/image182.png){width="5.768055555555556in"
height="0.9333333333333333in"}

单例模式（双检锁模式）、简单工厂、观察者模式、适配器模式、职责链模式等等

享元模式模式 选两个画下UML图

手写单例

写的是静态内部类的单例，然后他问我这个地方为什么用private，这儿为啥用static,这就考察你的基本功啦

静态类与单例模式的区别

单例模式 double check

单例模式都有什么，都是否线程安全，怎么改进（从synchronized  到
双重检验锁 到 枚举 Enum）

1、  基本的设计模式及其核心思想

2、  来，我们写一个单例模式的实现。这里有一个深坑，详情请见《 JVM 》第
370 页

3、  剩下的什么的就随缘吧。适配器类图什么的我也画过啊。

4、  基本的设计原则。如果有人问你接口里的属性为什么都是 final static
的，记得和他聊一聊设计原则。

**设计模式了解哪些 \
 jdk中哪些类用了哪些设计模式 **

算法
====

1.最小堆；

2.大数据归并排序、遗传算法 sqrt（）是实现，归并排序实现，mapreduce排序

3.快速排序和堆排序的优缺点，为什么？

4.一个是链表相加，思路就是反转 然后求和，另一个是多个有序数组
归并，用优先队列就好

5.最后一个算法题，是一个装水的问题，问在装多少，我用的双指针

6.LintCode -最小子串覆盖

7.查找数组中的最小元素 二分

8.第二题是算两个没有公共字母的字符串的最大长度积

9.LintCode - 反转二叉树

10.LintCode - 翻转字符串

11.单链表的快速排序

12.LintCode - 接雨水 III，写具体的方法和算法

13.整数去重问题

14.找出增序排列中一个数字第一次和最后一次出现的数组下标

15.海量数据去重

16.找出海量数据中前10个最大的数（数据有重复）

17.数组先升序在降序，找出最大数

18.正整数数组，拼出一个最大的正数

19.一个正整数数组，给其中一个数字加1，使得所有数乘积最大，找出加1的那个数字

20.手写快排、堆排 二分查找

21.单词接龙的程序

22.括号匹配；

23.一个数组存着负数与正数，将正数放在前年，负数放在后面

24.母鸡、公鸡和小鸡问题：公鸡五块一只，母鸡三块一只，小鸡一块三只，用100元买100只鸡的

-   25.各种排序算法的时间复杂度和空间复杂度

26.Dijkstra(求最短路径)

27.旋转数组找某个数

28.哲学家问题

29.最大连续子序列和

30.最左前缀匹配

31.单链表反转并输出

32.找到非排序数组中未出现的第一个正整数

33.在0到n这n+1个数中取n个数，如何找到缺少的那个。

34.链表中如何判断有环路

35.一个二维矩阵n\*n中，n对应表示各个节点，每个节点之间有连线就在相应位置上标识1，如何在其中判断出是不是一个图

（任一节点开始遍历，深度遍历，每遍历一个点进行一个标记，当深度遍历到自己访问过的点时，代表存在环，即是个图）

36.二叉树中找出从根到叶子节点中和最大的那条路径

37.实现二叉树的广度优先遍历

38.手写直接插入排序

39.在一个字符串中找出第一个字符出现的位置，保证高效

40.N级楼梯，一次一步或两步

41.深度优先遍历，广度优先遍历算法 在什么地方可以应用

42.杨辉三角形的算法，第N行的数的计算

43.给定两个全都是大写的字符串a,b
a的长度大于b的长度，问如何判断b中的所有字符都在a中（首先a,b排序，然后再两列比较）

44.一致性哈希算法

45.手写双向链表删除倒数第二个结点并分析

46.找到数组第三大数，没有则返回最大数

47.如何找到一条单链表的中间结点

48.从10亿个数中找不重复的数\
将10亿个数排序后存在不同子文件中，每个子文件在内存中用HashMap来进行判断，比如放入map中是（int和boolean它们封装类的键值对），第一次放进去时候boolean为false，当map中有这个数之后再放进去时，将false改为true。最后遍历map找出为false的数就是不重复的。

49.判断二叉树是否为平衡二叉树。

50.0G文件的淘宝商品编号，只有512M内存，怎么判断究竟是不是合法编号（即编号是否存在）

51.假如淘宝存着一个包含10w个敏感词的词库，紧接着需要从多个商品标题中随机抽查3个有没有包含敏感词的商品

52\. 查找中间链表元素

53\. 图算法

54平衡树的旋转·

55.一道算法题，在一个整形数组中，有正数有负数，找出和最大的子串

56\. 动态规划的思想

57\. 给出一个字符数组，找出第一个出现次数最多的字符，注意是第一个

58.一个无序数组找第K大的元素

59.找出数组两个数的和等于给定的数

60. 无序数组找中位数（时间复杂度为logN），

61.两个有序数组找中位数（时间复杂度为logN）

62.写大数加法代码

63.输出二叉树从左边看过去能看到的所有节点

64.算法题：给定一个翻转过的有序数组，找出翻转点的下标，如：原数组1，2，3，5，6，7，8，翻转后的数组5，6，7，8，1，2，3，翻转点下标是5

65.给定一个整数数组，数组中元素无重复。和一个整数limit，求数组元素全排列，要求相邻两个数字和小于limit

66.算法题：行列都有序二维数组，找出指定元素的位置，扩展到三维数组呢

67.输入指定个数的字符串,按照字符串长度进行排序,然后重新从短到长输出,排序算法要自己写不能用自带的

68.求二叉树深度,比较坑的是,牛客网没有提供二叉树构造的输入样例,所以还要自己写个构造二叉树的算法

69.二叉树的几种遍历方式

70.对整数分解质因数，90=2\*3\*3\*5

71.二叉树非递归后续遍历

72.实现三个线程轮流打印ABC十次

73.列举集合的所有子集

74.给单链表排序，时间复杂度O(nlogn),空间复杂度O(1)

75.判断一个字符串能否被字典完全分词(dp)

76.找出只出现一次的数字…链表的中间节点，链表的第n/m个节点
找出链表的中间节点，找出链表的三分之一节点，五分之一节点...

77.打印杨辉三角

78、手写栈实现队列

79.给定一个2叉树，打印每一层最右边的结点

80.给定一个数组，里面只有一个数出现了一次，其他都出现了两次。怎么得到这个出现了一次的数？

81.在6基础上，如果有两个不同数的出现了一次，其他出现了两次，怎么得到这两个数？

82.查找有序数组和为S的数

83.如有个公司有10000名员工，要求按照年龄来排序要求时间复杂度O(N)

83.两个innt32整数m和n的二进制表达有多少位不同

84\. 全排列的算法思路

![IMG\_256](media/image183.jpeg){width="9.241666666666667in"
height="5.704166666666667in"}

84. 字符串反转

85. 拓扑排序

86. .树的中序遍历，除了递归和栈还有什么实现方式
    中序遍历的非递归做法？引出BFS和DFS的区别

87. 拓扑排序思想

88.  给定n个数，寻找第k小的数

89. 写了一个小程序，给定一段字符串，主要为赋值型的字符串，让把它们对应到map里面

90. 1000以内的素数

91. 手写希尔排序

92. 利用数组，实现一个循环队列类

93. 写一个汉诺塔问题，打印出转移路径，接着写一个二叉树前序遍历的代码，最后让写一个多叉树实现，并层次遍历的代码，连写四个代码

94. 。第一道题是一个字母组成的字符串，对该字符串字母序进行排序，大写在小写前面，时间复杂度O(n)，如AaB是有序的，ABa是无序的。第二道题计算f(x,n)=x+x\^2+.....+x\^n,要求乘法次数最少。

95. 拓扑排序思想

96.一个字符串数组，现给定一个string去进行找出对应的数组中字符串的下标
 （可以有容错，但两字符串长度必须一致，容错为2）

> 例如： \["hello","hj","abc"\]    key=“hellg"  返回下角标0

97\. 图的 prime 算法   kruskal 算法  dijkstra算法  解决什么问题？
分别写一下 伪代码

98\. 从一堆字符串中，去除重复的字符，并输出

99\. 手写 Kmp 算法

100.
对一个基本有序的数组应该采用什么方式进行排序，对一个乱序的数组应该采用什么方式排序能快速找到前 n 个数？为什么？

101\. 给定一个数组, 里面放置任意数量的随机数,
如何快速统计出数组中重复的数字以及出现次数

102\. 给定字母集合(a-z), 求出由集合中这些字母组成的所有非空子集

103.
第一道题是用5行代码实现字符个数统计；第二题是反转单链表；第三题快速排序

104\. 接着推导快速排序的时间复杂度为什么是O(nlogn)?

105\. 并发场景下的多线程代码水题

106\. **算法题 一个数组里的数据只有一个是3个相同的，其他都是两个相同 
怎么找出这个数  围绕上一题优化 **

**107. 字符转int型，考虑负数，异常等问题 **

**108. 跳表**

**109. 给定n个左括号以及n个右括号，打印出所有合法的括号组合**

**110. 给定四个点如何判断是否为矩形**

海量数据
========

海量URL数据，低内存情况下找重复次数最高的那一个

10亿个数求100个最大的

大文件排序

给定三个大于10G的文件（每行一个数字）和100M内存的主机，找到在三个文件都出现且次数最多的10个字符串

求两个int数组的并集、交集

1t query 统计前k个热门的

对10G个数进行排序，限制内存为1G
大数问题，但是这10G个数可能是整数，字符串以及中文改如何排序，

假如有100万个玩家，需要对这100W个玩家的积分中前100名的积分，按照顺序显示在网站中，要求是实时更新的。积分可能由做的任务和获得的金钱决定。问如何对着100万个玩家前100名的积分进行实时更新？

我跟他讨论了什么分治啊、Hash啊，但后来他都说我的方法都是从全局的数据进行考虑的，这样空间和时间要求太多，并且不现实。后来我跟他一顿讨论，最后他给出了解决方法，就是利用缓存机制，缓存---tomcat---DB，层级计算，能不用到DB层就别用，因为每进一层，实现起来都会更复杂和更慢。解决的思路就是，考虑出了前100名的后100W-100名玩家的积分，让变化的积分跟第100名比较，如果比第100名高，那就替换的原则。

10亿条短信，找出前一万条重复率高的

对一万条数据排序，你认为最好的方式是什么

一个大文件，里面是很多字符串，用最优的方式计算出一个字符串是否存在

QQ每天都会产生大量的在线日志记录, 假设每天的在线日志记录有十亿条,
请设计一个算法快速找出今天的在线人数

有4个文件，每个文件大小为10G，每一行是一个单词，最后统计出Top10的单词

七．数据结构与算法
==================

[]{#_Toc13408 .anchor}**7.1排序**

*https://blog.csdn.net/whuslei/article/details/6442755*

![](media/image184.png){width="5.691666666666666in"
height="4.116666666666666in"}

1.  []{#_Toc12720 .anchor}直接插入排序

![](media/image185.png){width="5.766666666666667in" height="2.9125in"}

![](media/image186.png){width="5.761111111111111in"
height="1.4180555555555556in"}

public class Solution {\
public void sortIntegers2(int\[\] A) {\
InsertSort(A);\
}\
public void InsertSort(int\[\] A)\
{\
int i,j,k;\
for(i=1;i&lt;A.length;i++)\
{\
for(j=i-1;j&gt;=0;j--)\
{\
if(A\[j\] &lt;=
A\[i\])//寻找第一个小于A\[i\]的位置,也就是\[i\]该插入的地方\
break;\
}\
if(j != i-1)
//这个判断的意思是如果是刚好A\[i-1\]这个地方小于A\[i\],那么不需要操作\
{\
int temp = A\[i\];\
for(k=i-1;k&gt;j;k--)\
A\[k+1\] = A\[k\];\
A\[k+1\] = temp;//循环结束k=j,故需要k+1放在该放的位置上\
}\
}\
}\
}

1.  []{#_Toc3099 .anchor}希尔排序

![](media/image187.png){width="5.764583333333333in"
height="3.0548611111111112in"}

![](media/image188.png){width="5.7659722222222225in"
height="1.9805555555555556in"}

1.  []{#_Toc30136 .anchor}冒泡排序

![](media/image189.png){width="5.761111111111111in"
height="2.0416666666666665in"}

1.  []{#_Toc15990 .anchor}快速排序

![](media/image190.png){width="5.766666666666667in"
height="2.796527777777778in"}

public class Solution {\
\
public void sortIntegers2(int\[\] A) {\
// write your code here\
quicksort(A,0,A.length-1);\
}\
public void quicksort(int\[\] A,int begin,int end)\
{\
int i = begin;\
int j = end;\
if(i &gt;= j)\
{\
return;\
}\
int keng = A\[i\];\
while(i &lt; j)\
{\
while(i&lt;j && A\[j\] &gt; keng)\
{\
j--;\
}\
if(i&lt;j && A\[j\] &lt;= keng)\
{\
A\[i\] = A\[j\];\
i++;\
}\
while(i&lt;j && A\[i\] &lt; keng)\
{\
i++;\
}\
if(i&lt;j && A\[i\] &gt;= keng)\
{\
A\[j\] = A\[i\];\
j--;\
}\
}\
A\[i\] = keng;\
quicksort(A,begin,i-1);\
quicksort(A,i+1,end);\
}\
}

import java.util.\*;\
public class Solution {\
*/\*\*\
\* **@param** A: an integer array\
\* **@return:** nothing\
\*/\
*public void sortIntegers2(int\[\] A) {\
quicksort(A,0,A.length-1);\
}\
public int partion(int\[\] A,int low,int high)\
{\
int hole = A\[low\];\
int i = low;\
int j = high;\
if(low &lt; high)\
{\
\
while(i &lt; j)\
{\
while(i &lt; j && A\[j\] &gt;= hole)\
j--;\
if(i &lt; j && A\[j\] &lt; hole)\
{\
A\[i\] = A\[j\];\
i++;\
}\
while(i &lt; j && A\[i\] &lt;= hole)\
i++;\
if(i &lt; j && A\[i\] &gt; hole)\
{\
A\[j\] = A\[i\];\
j--;\
}\
}\
A\[i\] = hole;\
return i;\
}\
return -1;\
}\
public void quicksort(int\[\] A,int low,int high)\
{\
LinkedList&lt;Integer&gt; stack = new LinkedList&lt;&gt;();\
int k = -1;\
if(low &lt; high)\
{\
stack.offerFirst(low);\
stack.offerFirst(high);\
while(stack.size() != 0)\
{\
int right = (int)stack.poll();\
int left = (int)stack.poll();\
k = partion(A,left,right);\
if(k-1 &gt; left)\
{\
stack.offerFirst(left);\
stack.offerFirst(k-1);\
}\
if(k+1 &lt; right)\
{\
stack.offerFirst(k+1);\
stack.offerFirst(right);\
}\
}\
}\
}\
}

1.  []{#_Toc17131 .anchor}直接选择排序

![](media/image191.png){width="5.766666666666667in"
height="2.2819444444444446in"}

public class Solution {\
public void sortIntegers2(int\[\] A) {\
SelectSort(A);\
}\
public void SelectSort(int\[\] A)\
{\
for(int i=0;i&lt;A.length;i++)\
{\
int minIndex = i;\
for(int j=i;j&lt;A.length;j++)\
{\
if(A\[j\] &lt; A\[minIndex\])\
minIndex = j;\
}\
int temp = A\[i\];\
A\[i\] = A\[minIndex\];\
A\[minIndex\] = temp;\
}\
}\
}

1.  []{#_Toc2860 .anchor}堆排序

![](media/image192.png){width="5.761111111111111in"
height="2.551388888888889in"}

![](media/image193.png){width="5.761805555555555in"
height="3.7256944444444446in"}

1.  []{#_Toc7296 .anchor}归并排序

![](media/image194.png){width="5.759722222222222in"
height="2.692361111111111in"}

public class Solution {\
public void sortIntegers2(int\[\] A) {\
int \[\] temp = new int\[A.length\];\
mergeSort(A,0,A.length-1,temp);\
}\
public void mergeArray(int\[\] A,int leftBegin,int leftEnd,int
rightBegin,int rightEnd,int\[\] temp)\
{\
int i = leftBegin,j = rightBegin;\
int k = 0;\
while (i &lt;= leftEnd && j &lt;= rightEnd)
//谁小就把谁弄到temp数组里,直到有一方先全部弄完\
{\
if(A\[i\] &lt; A\[j\])\
temp\[k++\] = A\[i++\];\
else\
temp\[k++\] = A\[j++\];\
}\
while(i &lt;= leftEnd)
//无法确定哪一方先全部遍历结束，所以写了两个循环,只要没结束就会继续复制到temp中\
temp\[k++\] = A\[i++\];\
while(j &lt;= rightEnd)\
temp\[k++\] = A\[j++\];\
for(i=0;i&lt;k;i++)\
A\[leftBegin+i\] = temp\[i\];
//将排序好的temp复制到A\[leftBegin\]到A\[rightEnd\]中，完成排序\
}\
public void mergeSort(int\[\] A,int left,int right,int\[\] temp)\
{\
if(left &lt; right)\
{\
int mid = (left + right) /
2;//递归的过程中一层层往下，直到left=right,也就是当前要归并的两数组都是只有一个元素\
mergeSort(A,left,mid,temp);\
mergeSort(A,mid+1,right,temp);\
mergeArray(A,left,mid,mid+1,right,temp);\
}\
}\
}

import java.util.\*;\
public class Solution {\
public void sortIntegers2(int\[\] A) {\
if(A.length == 0)\
return;\
System.*out*.println(A.length+"");\
int \[\] temp = new int\[A.length\];\
mergeSort(A,0,A.length-1,temp);\
}\
public void mergeArray(int\[\] A,int leftBegin,int leftEnd,int
rightBegin,int rightEnd,int\[\] temp)\
{\
int i = leftBegin,j = rightBegin;\
int k = 0;\
while (i &lt;= leftEnd && j &lt;= rightEnd)
//谁小就把谁弄到temp数组里,直到有一方先全部弄完\
{\
if(A\[i\] &lt; A\[j\])\
temp\[k++\] = A\[i++\];\
else\
temp\[k++\] = A\[j++\];\
}\
while(i &lt;= leftEnd)
//无法确定哪一方先全部遍历结束，所以写了两个循环,只要没结束就会继续复制到temp中\
temp\[k++\] = A\[i++\];\
while(j &lt;= rightEnd)\
temp\[k++\] = A\[j++\];\
for(i=0;i&lt;k;i++)\
A\[leftBegin+i\] = temp\[i\];
//将排序好的temp复制到A\[leftBegin\]到A\[rightEnd\]中，完成排序\
}\
public void mergeSort(int\[\] A,int left,int right,int\[\] temp)\
{\
int s=2,i=0;\
while(s &lt;= A.length-1)\
{\
i = 0;\
while(i+s &lt;= A.length) //按照跨度s进行两两合并，s=2 两两合并 s=4
四四合并\
{\
mergeArray(A,i,(i+i+s-1)/2,(i+i+s-1)/2+1,i+s-1,temp);\
i += s;\
}\
mergeArray(A,i-s,i-1,i,A.length-1,temp);//合并尾部剩下的数据，具体见我举的例子\
s \*= 2;\
}\
mergeArray(A,0,s/2-1,s/2,A.length-1,temp);//合并尾部与前面一大片已经排序序的部分。\
}\
}

1.  []{#_Toc10609 .anchor}基数排序

![](media/image195.png){width="5.7652777777777775in"
height="4.7756944444444445in"}

![](media/image196.png){width="5.763888888888889in" height="2.6375in"}

1.  []{#_Toc580 .anchor}**树**

[]{#_Toc29063 .anchor}**7.2.1二分查找树**

![](media/image197.png){width="5.767361111111111in"
height="3.4805555555555556in"}

7.2.2LRU实现

*https://blog.csdn.net/hxqneuq2012/article/details/52709652*

![](media/image198.png){width="5.763194444444444in"
height="2.5319444444444446in"}

***https://blog.csdn.net/hxqneuq2012/article/details/52709652***

import java.util.HashMap;\
public class Main {\
\
int capacity;\
HashMap&lt;Integer, Node&gt; map = new HashMap&lt;Integer, Node&gt;();\
Node head = null;\
Node end = null;\
\
public Main(int capacity) {\
this.capacity = capacity;\
}\
\
public int get(int key) {\
if (map.containsKey(key)) {\
Node n = map.get(key);\
remove(n);\
setHead(n);\
printNodes("get");\
return n.value;\
}\
printNodes("get");\
return -1;\
}\
\
public void remove(Node n) {\
if (n.pre != null) {\
n.pre.next = n.next;\
} else {\
head = n.next;\
}\
\
if (n.next != null) {\
n.next.pre = n.pre;\
} else {\
end = n.pre;\
}\
\
}\
\
public void setHead(Node n) {\
n.next = head;\
n.pre = null;\
\
if (head != null)\
head.pre = n;\
\
head = n;\
\
if (end == null)\
end = head;\
}\
\
public void set(int key, int value) {\
if (map.containsKey(key)) {\
Node old = map.get(key);\
old.value = value;\
remove(old);\
setHead(old);\
} else {\
Node created = new Node(key, value);\
if (map.size() &gt;= capacity) {\
map.remove(end.key);\
remove(end);\
setHead(created);\
\
} else {\
setHead(created);\
}\
\
map.put(key, created);\
}\
printNodes("set");\
}\
\
public void printNodes(String explain) {\
\
System.*out*.print(explain + ":" + head.toString());\
Node node = head.next;\
while (node != null) {\
System.*out*.print(node.toString());\
node = node.next;\
}\
System.*out*.println();\
}\
\
public static void main(String\[\] args) {\
Main lruCacheTest = new Main(5);\
lruCacheTest.set(1, 1);\
lruCacheTest.set(2, 2);\
lruCacheTest.set(3, 3);\
lruCacheTest.set(4, 4);\
lruCacheTest.set(5, 5);\
System.*out*.println("lruCacheTest.get(1):" + lruCacheTest.get(1));\
lruCacheTest.set(6, 6);\
System.*out*.println("lruCacheTest.get(2):" + lruCacheTest.get(2));\
}\
\
}\
\
class Node {\
int key;\
int value;\
Node pre;\
Node next;\
\
public Node(int key, int value) {\
this.key = key;\
this.value = value;\
}\
\
@Override\
public String toString() {\
return this.key + "-" + this.value + " ";\
}\
}

7.2.3判断一个数是不是整数

考虑字母，整数上界，整数下界

public class Main {\
public static void main(String\[\] args) {\
String str = "-8888888888888888 123";\
String \[\] list = str.split(" ");\
String firstStr = list\[0\];\
if(*isNumeric*(firstStr))\
{\
if(str.charAt(0) == '-')\
{\
try{\
System.*out*.println(Integer.*parseInt*(firstStr));\
}catch (Exception e)\
{\
System.*out*.println(Integer.*MIN\_VALUE*);\
}\
return;\
}\
try{\
System.*out*.println(Integer.*parseInt*(firstStr));\
}catch (Exception e)\
{\
System.*out*.println(Integer.*MAX\_VALUE*);\
}\
return;\
}\
System.*out*.println(0);\
}\
//方法五：用ascii码\
public static boolean isNumeric(String str){\
int begin = 0;\
if(str.charAt(0) == '-')\
begin = 1;\
for(int i=str.length();--i&gt;=begin;){\
int chr=str.charAt(i);\
if(chr&lt;48 || chr&gt;57)\
return false;\
}\
return true;\
}\
}

.红黑树与二叉树有什么区别、红黑树用途

直接上手红黑树和平衡二叉树区别

AVL树的概念, 四种旋转方式, AVL树左右旋转的例子

红黑树的旋转 2node节点插入和3node节点插入时候旋转的情况 简述伪代码

字典树

链表使用的循环链表还是双向链表

树和图的区别

了解哈夫曼树、b+/b-树、红黑树

栈和队列的区别,如何实现栈

有序集合底层数据结构是

找到二叉树第m层的第n个节点

.链表的结构，操作的时间复杂度分析

前缀树

堆与普通二叉树有什么区别

什么是递归，递归的几个条件？写递归要注意些什么？

八.数据库
=========

8.1索引 B树B+树
---------------

### 8.1.1 索引特点优缺点适用场合

*http://blog.jobbole.com/24006/*

*http://www.yuanrengu.com/index.php/2017-01-13.html*

*8.1.1.1 索引的优缺点特点*

![](media/image199.png){width="5.7659722222222225in"
height="3.0284722222222222in"}

![](media/image200.png){width="5.761805555555555in"
height="0.9423611111111111in"}

8.1.1.2 索引使用的注意事项

![](media/image201.png){width="5.591666666666667in"
height="3.316666666666667in"}

> ![](media/image202.png){width="5.764583333333333in"
> height="1.0520833333333333in"}

8.1.1.3 索引的适用场景

![](media/image203.png){width="5.758333333333334in"
height="1.6743055555555555in"}

性别不适应用建立索引？为什么？

因为你访问索引需要付出额外的IO开销，你从索引中拿到的只是地址，要想真正访问到数据还是要对表进行一次IO。假如你要从表的100万行数据中取几个数据，那么利用索引迅速定位，访问索引的这IO开销就非常值了。但如果你是从100万行数据中取50万行数据，就比如性别字段，那你相对需要访问50万次索引，再访问50万次表，加起来的开销并不会比直接对表进行一次完整扫描小。

### 8.1.2 Mysql索引原理B+树：

*https://blog.csdn.net/v\_july\_v/article/details/6530142*

*https://blog.csdn.net/guoziqing506/article/details/64122287*

索引是怎么优化查询效率的？这中间的过程能描述下吗？

可以从B+树原理回答

1.  索引为什么采用B+树

> B+树更有利于对数据库的扫描
>
> B树在提高了磁盘IO性能的同时并没有解决元素遍历的效率低下的问题，而B+树只需要遍历叶子节点就可以解决对全部关键字信息的扫描，所以对于数据库中频繁使用的range
> query，B+树有着更高的性能。
>
> B+树的磁盘读写代价更低
>
> B+树的内部结点并没有指向关键字具体信息的指针。因此其内部结点相对B树更小。如果把所有同一内部结点的关键字存放在同一盘块中，那么盘块所能容纳的关键字数量也越多。一次性读入内存中的需要查找的关键字也就越多。相对来说I/O读写次数也就降低了。
>
> B+树的查询效率更加稳定
>
> 由于内部结点并不是最终指向文件内容的结点，而只是叶子结点中关键字的索引。所以任何关键字的查找必须走一条从根结点到叶子结点的路。所有关键字查询的路径长度相同，导致每一个数据的查询效率相当。

2\. B+树

> B+树是B树的一种变形，它更适合实际应用中操作系统的文件索引和数据库索引。
>
> 定义：
>
> ![](media/image204.png){width="5.767361111111111in"
> height="1.4895833333333333in"}
>
> ![](media/image205.png){width="5.761805555555555in"
> height="3.3340277777777776in"}

3.  **B-树（也就是B树）**

> ![](media/image206.png){width="5.763194444444444in"
> height="4.20625in"}
>
> ![](media/image207.png){width="5.759722222222222in"
> height="3.670138888888889in"}
>
> B-树搜索：
>
> ![](media/image208.png){width="5.763194444444444in"
> height="0.6104166666666667in"}

3.  **B+树与B-树的区别**

> 答：1.内部节点中，关键字的个数与其子树的个数相同，不像B树种，子树的个数总比关键字个数多1个
>
> 2.所有指向文件的关键字及其指针都在叶子节点中，不像B树，有的指向文件的关键字是在内部节点中。换句话说，B+树中，内部节点仅仅起到索引的作用，
>
> 3.B+在搜索过程中，如果查询和内部节点的关键字一致，那么搜索过程不停止，而是继续向下搜索这个分支，B+为了找到这个关键字的指针。

[]{#_Toc16017 .anchor}**8.1.3 索引分类**

***https://www.cnblogs.com/heyonggang/p/6610526.html***

8.1.3.0 索引分类

-   组合索引：实质上是将多个字段建到一个索引里，列值的组合必须唯一

-   聚集索引：定义：数据行的物理顺序与列值（一般是主键的那一列）的逻辑顺序相同，一个表中只能拥有一个聚集索引。

-   非聚集索引：唯一索引 普通索引 主键索引 全文索引

-   UNIQUE(唯一索引)：不可以出现相同的值，可以有NULL值

-   INDEX(普通索引)：允许出现相同的索引内容

-   PROMARY KEY(主键索引)：不允许出现相同的值

-   fulltext index(全文索引)：可以针对值中的某个单词，但效率确实不敢恭维

-   

**8.1.3.1 创建索引语句**

**创建唯一，主键，普通，全文索引**

![](media/image209.png){width="5.7625in" height="1.5131944444444445in"}

**创建组合索引**

![](media/image210.png){width="5.763888888888889in" height="2.66875in"}

8.1.3.2 索引类型

**1.直接创建索引和间接创建索引**\
    直接创建索引：CREATE INDEX mycolumn\_index ON mytable (myclumn)\
    间接创建索引：定义主键约束或者唯一性键约束，可以间接创建索引\
   ** 2.普通索引和唯一性索引\
**    普通索引：CREATE INDEX mycolumn\_index ON mytable (myclumn)\
    唯一性索引：保证在索引列中的全部数据是唯一的，对聚簇索引和非聚簇索引都可以使用\
    CREATE UNIQUE COUSTERED INDEX myclumn\_cindex ON mytable(mycolumn)

普通索引允许被索引的数据列包含重复的值。比如说，因为人有可能同名，所以同一个姓名在同一个“员工个人资料”数据表里可能出现两次或更多次。

如果能确定某个数据列将只包含彼此各不相同的值，在为这个数据列创建索引的时候就应该用关键字UNIQUE把它定义为一个唯一索引。这么做的好处：一是简化了MySQL对这个索引的管理工作，这个索引也因此而变得更有效率；二是MySQL会在有新记录插入数据表时，自动检查新记录的这个字段的值是否已经在某个记录的这个字段里出现过了；如果是，MySQL将拒绝插入那条新记录。也就是说，唯一索引可以保证数据记录的唯一性。事实上，在许多场合，人们创建唯一索引的目的往往不是为了提高访问速度，而只是为了避免数据出现重复。\
**    3.单个索引和复合索引**\
    单个索引：即非复合索引\
    复合索引：又叫组合索引，在索引建立语句中同时包含多个字段名，最多16个字段\
    CREATE INDEX name\_index ON username(firstname,lastname)\
**    4.聚簇索引和非聚簇索引(聚集索引，群集索引) **

*https://www.cnblogs.com/s-b-b/p/8334593.html*

**MySQL里主键就是聚集索引**

定义：数据行的物理顺序与列值（一般是主键的那一列）的逻辑顺序相同，一个表中只能拥有一个聚集索引。

![](media/image211.png){width="5.763888888888889in"
height="1.9104166666666667in"}

**5.主索引 和外键索引**

在前面已经反复多次强调过：必须为主键字段创建一个索引，这个索引就是所谓的“主索引”。主索引与唯一索引的唯一区别是：前者在定义时使用的关键字是PRIMARY而不是UNIQUE。

主索引：CREATE PRIMARY COUSTERED INDEX myclumn\_cindex ON
mytable(mycolumn) 或者mysql&gt;ALTER TABLE \`table\_name\` ADD PRIMARY
KEY ( \`column\` )

外键索引：外键索引 mysql&gt;ALTER TABLE \`table\_name\` ADD FULLTEXT (
\`column\`)

**6.全文索引**

*http://www.360doc.com/content/17/1211/13/33260087\_712076317.shtml*

![](media/image212.png){width="5.7625in" height="5.423611111111111in"}

**7.空间索引**

空间索引是指依据空间对象的位置和形状或空间对象之间的某种空间关系按一定的顺序排列的一种数据结构 ，其中包含空间对象的概要信息，如对象的标识、外接矩形及指向空间对象实体的指针。

区别：它将空间对象按范围划分，每个结点都对应一个区域和一个磁盘页，非叶结点的磁盘页中

> 数据库从左到右原则

 

8.2 innoDB与MyISAM引擎区别
--------------------------

![](media/image213.png){width="5.763888888888889in"
height="2.5236111111111112in"}

两种存储引擎在索引上的区别：

*https://blog.csdn.net/zsq520520/article/details/68954646*

![](media/image214.png){width="5.761805555555555in"
height="4.395138888888889in"}

![](media/image215.png){width="5.764583333333333in" height="3.45625in"}

(图inndb主键索引）是InnoDB主索引（同时也是数据文件）的示意图，可以看到叶节点包含了完整的数据记录。这种索引叫做**聚集索引**。因为InnoDB的数据文件本身要按主键聚集，所以InnoDB要求表必须有主键（MyISAM可以没有），如果没有显式指定，则**MySQL**系统会自动选择一个可以唯一标识数据记录的列作为主键，如果不存在这种列，则MySQL自动为InnoDB表生成一个隐含字段作为主键，这个字段长度为6个字节，类型为长整形

8.3 事务隔离级别（恶果：脏读 幻读 不可重复读）
----------------------------------------------

**Mysql默认级别可重复读**

![](media/image216.png){width="5.761111111111111in"
height="5.603472222222222in"}

![](media/image217.png){width="5.7659722222222225in"
height="1.3506944444444444in"}

8.4 数据库特性 ACID
-------------------

1.原子性（Atomicity）：原子性很容易理解，也就是说事务里的所有操作要么全部做完，要么都不做，事务成功的条件是事务里的所有操作都成功，只要有一个操作失败，整个事务就失败，需要回滚。

2.一致性（Consistency）：从一个一致性状态到另一个一致性状态。

例如现有完整性约束a+b=10，如果一个事务改变了a，那么必须得改变b，使得事务结束后依然满足a+b=10，否则事务失败。

3.隔离性（Isolation）：一个事务所做的修改在最终提交以前，对其它事务不可见。

比如现有有个交易是从A账户转100元至B账户，在这个交易还未完成的情况下，如果此时B查询自己的账户，是看不到新增加的100元的。

4.(Durability) 持久性\
持久性是指一旦事务提交后，它所做的修改将会永久的保存在数据库上，即使出现宕机也不会丢失。

8.5 sql
-------

[]{#_Toc32293 .anchor}8.5.1．Sql优化

![](media/image218.png){width="5.7652777777777775in"
height="2.1909722222222223in"}

![](media/image219.png){width="5.764583333333333in"
height="5.450694444444444in"}

![](media/image220.png){width="5.7659722222222225in"
height="1.0923611111111111in"}

![](media/image221.png){width="5.7652777777777775in"
height="5.2972222222222225in"}

![](media/image222.png){width="5.7652777777777775in"
height="3.1305555555555555in"}

![](media/image223.png){width="5.759722222222222in"
height="4.4006944444444445in"}

8.6 5种连接left join、right join、inner join，full join cross join
------------------------------------------------------------------

***https://www.cnblogs.com/pcjim/articles/799302.html***

**sql之left join、right join、inner join的区别**

**left join(左联接) 返回包括左表中的所有记录和右表中联结字段相等的记录 \
right join(右联接) 返回包括右表中的所有记录和左表中联结字段相等的记录\
inner join(等值连接) 只返回两个表中联结字段相等的行**

举例如下： \
--------------------------------------------\
表A记录如下：\
aID　　　　　aNum\
1　　　　　a20050111\
2　　　　　a20050112\
3　　　　　a20050113\
4　　　　　a20050114\
5　　　　　a20050115

表B记录如下:\
bID　　　　　bName\
1　　　　　2006032401\
2　　　　　2006032402\
3　　　　　2006032403\
4　　　　　2006032404\
8　　　　　2006032408

--------------------------------------------\
1.left join\
sql语句如下: \
select \* from A\
left join B \
on A.aID = B.bID

结果如下:\
aID　　　　　aNum　　　　　bID　　　　　bName\
1　　　　　a20050111　　　　1　　　　　2006032401\
2　　　　　a20050112　　　　2　　　　　2006032402\
3　　　　　a20050113　　　　3　　　　　2006032403\
4　　　　　a20050114　　　　4　　　　　2006032404\
5　　　　　a20050115　　　　NULL　　　　　NULL

（所影响的行数为 5 行）\
结果说明:\
left join是以A表的记录为基础的,A可以看成左表,B可以看成右表,left
join是以左表为准的.\
换句话说,左表(A)的记录将会全部表示出来,而右表(B)只会显示符合搜索条件的记录(例子中为:
A.aID = B.bID).\
B表记录不足的地方均为NULL.\
--------------------------------------------\
2.right join\
sql语句如下: \
select \* from A\
right join B \
on A.aID = B.bID

结果如下:\
aID　　　　　aNum　　　　　bID　　　　　bName\
1　　　　　a20050111　　　　1　　　　　2006032401\
2　　　　　a20050112　　　　2　　　　　2006032402\
3　　　　　a20050113　　　　3　　　　　2006032403\
4　　　　　a20050114　　　　4　　　　　2006032404\
NULL　　　　　NULL　　　　　8　　　　　2006032408

（所影响的行数为 5 行）\
结果说明:\
仔细观察一下,就会发现,和left
join的结果刚好相反,这次是以右表(B)为基础的,A表不足的地方用NULL填充.\
--------------------------------------------\
3.inner join\
sql语句如下: \
select \* from A\
innerjoin B \
on A.aID = B.bID

结果如下:\
aID　　　　　aNum　　　　　bID　　　　　bName\
1　　　　　a20050111　　　　1　　　　　2006032401\
2　　　　　a20050112　　　　2　　　　　2006032402\
3　　　　　a20050113　　　　3　　　　　2006032403\
4　　　　　a20050114　　　　4　　　　　2006032404

结果说明:\
很明显,这里只显示出了 A.aID = B.bID的记录.这说明inner
join并不以谁为基础,它只显示符合条件的记录.\
--------------------------------------------\
注: \
LEFT JOIN操作用于在任何的 FROM 子句中，组合来源表的记录。使用 LEFT JOIN
运算来创建一个左边外部联接。左边外部联接将包含了从第一个（左边）开始的两个表中的全部记录，即使在第二个（右边）表中并没有相符值的记录。

语法：FROM table1 LEFT JOIN table2 ON table1.field1 compopr
table2.field2

说明：table1, table2参数用于指定要将记录组合的表的名称。\
field1,
field2参数指定被联接的字段的名称。且这些字段必须有相同的数据类型及包含相同类型的数据，但它们不需要有相同的名称。\
compopr参数指定关系比较运算符："="， "&lt;"， "&gt;"， "&lt;="， "&gt;="
或 "&lt;&gt;"。\
如果在INNER JOIN操作中要联接包含Memo 数据类型或 OLE Object
数据类型数据的字段，将会发生错误. 

4.全外连接（full join ...on...）

select \* from table1 a full join table2 b on a.id=b.id
全外连接其实是左连接和右连接的一个合集，也就是说他会查询出左表和右表的全部数据，匹配不上的会显示为null；如下图：

5.交叉连接（cross join...）

select \* from table1 a crossjoin table2 b ；

也可以写为 select \* from table1,table2;

交叉连接，也称为笛卡尔积，查询返回结果的行数等于两个表行数的乘积

8.7 数据库范式
--------------

![](media/image224.png){width="5.763888888888889in"
height="1.2840277777777778in"}

8.8 数据库连接池
----------------

[]{#_Toc9848 .anchor}**8.8.1 数据库连接池原理**

*https://blog.csdn.net/xiebaochun/article/details/28901363*

*https://blog.csdn.net/shuaihj/article/details/14223015*

连接池的工作原理主要由三部分组成，分别为连接池的建立、连接池中连接的使用管理、连接池的关闭。

第一、连接池的建立。一般在系统初始化时，连接池会根据系统配置建立，并在池中创建了几个连接对象，以便使用时能从连接池中获取。连接池中的连接不能随意创建和关闭，这样避免了连接随意建立和关闭造成的系统开销。Java中提供了很多容器类可以方便的构建连接池，例如Vector、Stack等。

第二、连接池的管理。连接池管理策略是连接池机制的核心，连接池内连接的分配和释放对系统的性能有很大的影响。其管理策略是：

当客户请求数据库连接时，首先查看连接池中是否有空闲连接，如果存在空闲连接，则将连接分配给客户使用；如果没有空闲连接，则查看当前所开的连接数是否已经达到最大连接数，如果没达到就重新创建一个连接给请求的客户；如果达到就按设定的最大等待时间进行等待，如果超出最大等待时间，则抛出异常给客户。
当客户释放数据库连接时，先判断该连接的引用次数是否超过了规定值，如果超过就从连接池中删除该连接，否则保留为其他客户服务。

该策略保证了数据库连接的有效复用，避免频繁的建立、释放连接所带来的系统资源开销。

3.  连接池的关闭。当应用程序退出时，关闭连接池中所有的连接，释放连接池相关的资源，该过程正好与创建相反

[]{#_Toc8504 .anchor}**8.8.2 数据库连接池的示例代码**

> ![](media/image225.png){width="5.763888888888889in"
> height="5.343055555555556in"}

像打开关闭数据库连接这种和数据库的交互可能是很费时的，尤其是当客户端数量增加的时候，会消耗大量的资源，成本是非常高的。可以在应用服务器启动的时候建立很多个数据库连接并维护在一个池中。连接请求由池中的连接提供。在连接使用完毕以后，把连接归还到池中，以用于满足将来更多的请求。

![](media/image226.png){width="5.763194444444444in"
height="1.3152777777777778in"}

数据库分页查询

![](media/image227.png){width="5.7652777777777775in"
height="1.1659722222222222in"}

[]{#_Toc12666 .anchor}**8.9 DDL DML DCL**

**DML（data manipulation language）： \
**它们是SELECT、UPDATE、INSERT、DELETE，就象它的名字一样，这4条命令是用来对数据库里的数据进行操作的语言 

**DDL is Data Definition Language statements. Some
examples:数据定义语言，**用于定义和管理 SQL 数据库中的所有对象的语言 \
1.CREATE - to create objects in the database 创建 \
2.ALTER - alters the structure of the database 修改 \
3.DROP - delete objects from the database 删除 \
4.TRUNCATE - remove all records from a table, including all spaces
allocated for the records are removed 

**DCL is Data Control Language statements. Some
examples**:数据控制语言，用来授予或回收访问数据库的某种特权，并控制数据库操纵事务发生的时间及效果，对数据库实行监视等 \
\
1.COMMIT - save work done 提交 \
2.SAVEPOINT - identify a point in a transaction to which you can later
roll back 保存点 \
3.ROLLBACK - restore database to original since the last COMMIT 回滚 \
4.SET TRANSACTION - Change transaction options like what rollback
segment to use 设置当前事务的特性，它对后面的事务没有影响．

[]{#_Toc6498 .anchor}**8.10 explain**

***https://www.cnblogs.com/gomysql/p/3720123.html***

**8.10.1.什么是explain?**

> 需要知道该SQL的执行计划，比如是全表扫描，还是索引扫描，这些都需要通过EXPLAIN去完成。EXPLAIN命令是查看优化器如何决定执行查询的主要方法。
>
> **8.10.2 explain命令详解**
>
> ![](media/image228.png){width="5.763888888888889in"
> height="0.7291666666666666in"}
>
> **1.id**
>
> **包含一组数字，表示查询中执行select子句或操作表的顺序（第一个select是1，子查询是2.子子查询是3.依次类推）**
>
> **2.select\_type**
>
> 示查询中每个select子句的类型（简单OR复杂）
>
> a\. SIMPLE：查询中不包含子查询或者UNION\
> b. 查询中若包含任何复杂的子部分，最外层查询则被标记为：PRIMARY\
> c. 在SELECT或WHERE列表中包含了子查询，该子查询被标记为：SUBQUERY\
> d.
> 在FROM列表中包含的子查询被标记为：DERIVED（衍生）用来表示包含在from子句中的子查询的select，mysql会递归执行并将结果放到一个临时表中。服务器内部称为"派生表"，因为该临时表是从子查询中派生出来的\
> e.
> 若第二个SELECT出现在UNION之后，则被标记为UNION；若UNION包含在FROM子句的子查询中，外层SELECT将被标记为：DERIVED\
> f. 从UNION表获取结果的SELECT被标记为：UNION RESULT
>
> SUBQUERY和UNION还可以被标记为DEPENDENT和UNCACHEABLE。\
> DEPENDENT意味着select依赖于外层查询中发现的数据。\
> UNCACHEABLE意味着select中的某些
> 特性阻止结果被缓存于一个item\_cache中。
>
> **3.type**

表示MySQL在表中找到所需行的方式，又称“访问类型”，常见类型如下:

 ALL, index,  range, ref, eq\_ref, const, system,
NULL（全局遍历啦，还是索引查询等）

> **4.possible\_keys**
>
> 指出MySQL能使用哪个索引在表中找到记录，查询涉及到的字段上若存在索引，则该索引将被列出，但不一定被查询使用（表中的某一列上有多个索引都和这个有关系，索引建立在这个字段上了，那么都列出来）
>
> **5.key**
>
> 显示MySQL在查询中实际使用的索引，若没有使用索引，显示为NULL
>
> **6.key\_len**
>
> **表示索引中使用的字节数，可通过该列计算查询中使用的索引的长度**

**7. ref\
表示上述表的连接匹配条件，即哪些列或常量被用于查找索引列上的值**

**8. rows\
表示MySQL根据表统计信息及索引选用情况，估算的找到所需的记录所需要读取的行数**

**9. Extra**\
**包含不适合在其他列中显示但十分重要的额外信息**

**10.table **

**Select 查询的表的名字**

[]{#_Toc2320 .anchor}**8.11 分库分表**

***https://blog.csdn.net/winy\_lm/article/details/50708493***

**8.11.1 概念**

1.  **分表 **

**用户id直接mod分成表的数目大小，将大表拆成小表**

1.  **分库**

**同分表**

1.  **分库分表**

 1. 中间变量 = user\_id % (分库数量 \* 每个库的表数量)

    2. 库 = 取整数 (中间变量 / 每个库的表数量)

    3. 表 = 中间变量 % 每个库的表数量

还有一种就是分库分表的垂直切分和水平划分
个人感觉这个垂直划分就是上文的分库

1.  垂直切分

将关联的表切分到数据库中（不涉及到切分数据表的操作）。

1.  水平切分

> 将一个表中的数据切分到不同的数据库中。

**8.11.2 垂直切分水平切分的坏处**

![](media/image229.png){width="4.641666666666667in" height="3.4in"}

![](media/image230.png){width="4.591666666666667in"
height="0.2916666666666667in"}

![](media/image231.png){width="4.683333333333334in"
height="1.3583333333333334in"}

**8.11.3 如何解决分库分表带来的坏处**

> 8.11.3.1 ACID解决方法

![](media/image232.png){width="4.141666666666667in"
height="4.691666666666666in"}

> 8.11.3.2 水平切分ID被破坏（递增ID）
>
> ![](media/image233.png){width="3.683333333333333in"
> height="0.6583333333333333in"}
>
> ![](media/image234.png){width="3.825in" height="2.925in"}
>
> ![](media/image235.png){width="3.7583333333333333in"
> height="1.3416666666666666in"}
>
> 8.11.3.3 跨库join
>
> ![](media/image236.png){width="3.408333333333333in"
> height="1.6333333333333333in"}
>
> ![](media/image237.png){width="3.4in" height="0.6416666666666667in"}
>
> 数据冗余就是分开表以后，在每个表中多添加一些被分走的数据的信息，可能会重复，但是可以在一个库中进行join(就是把需要的数据就算其它数据库有了，我还是要添加到我的数据库中）
>
> ![](media/image238.png){width="3.525in" height="1.7666666666666666in"}
>
> 8.11.3.4 外键约束解决
>
> ![](media/image239.png){width="3.525in" height="1.575in"}

[]{#_Toc12161 .anchor}**8.12 数据库锁**

[]{#_Toc22702 .anchor}**8.12.1 封锁**

![](media/image240.png){width="5.764583333333333in"
height="3.484722222222222in"}

![](media/image241.png){width="5.666666666666667in"
height="3.283333333333333in"}

[]{#_Toc20694 .anchor}**8.12.2 封锁协议（解决脏读不可重复读）**

> ![](media/image242.png){width="5.558333333333334in" height="2.625in"}
>
> ![](media/image243.png){width="5.575in" height="0.8in"}
>
> ![](media/image244.png){width="5.433333333333334in"
> height="3.4583333333333335in"}
>
> ![](media/image245.png){width="5.716666666666667in"
> height="1.7666666666666666in"}
>
> []{#_Toc29125 .anchor}**8.12.3 死锁活锁**
>
> ![](media/image246.png){width="5.633333333333334in" height="2.0in"}
>
> ![](media/image247.png){width="5.533333333333333in"
> height="1.5916666666666666in"}
>
> ![](media/image248.png){width="5.633333333333334in"
> height="1.9833333333333334in"}

[]{#_Toc1401 .anchor}**8.12.3 解决死锁的方法**

> **8.12.3.1 死锁的预防**
>
> ![](media/image249.png){width="5.764583333333333in"
> height="3.3777777777777778in"}
>
> ![](media/image250.png){width="5.767361111111111in"
> height="3.922222222222222in"}
>
> **8.12.3.2 死锁的诊断与解除**
>
> ![](media/image251.png){width="5.741666666666666in"
> height="4.758333333333334in"}
>
> ![](media/image252.png){width="5.768055555555556in"
> height="2.577777777777778in"}

[]{#_Toc28359 .anchor}**8.12.4 两段锁协议**

> ![](media/image253.png){width="5.767361111111111in"
> height="3.9770833333333333in"}

[]{#_Toc28104 .anchor}**8.12.5 GAP锁（解决幻读）**

在索引记录的间隙上加锁，禁止插入，这样就避免了幻读

具体例子:

*https://blog.csdn.net/cug\_jiang126com/article/details/50596729*

![](media/image254.png){width="5.763888888888889in"
height="1.5368055555555555in"}

![](media/image255.png){width="5.7625in" height="3.667361111111111in"}

[]{#_Toc1909 .anchor}**8.12.6 next-key 锁**

***https://blog.csdn.net/xifeijian/article/details/20313977***

当我们用范围条件而不是相等条件检索数据，并请求共享或排他锁时，InnoDB会给符合条件的已有数据记录的索引项加锁；对于键值在条件范围内但并不存在的记录，叫做“间隙（GAP)”，InnoDB也会对这个“间隙”加锁，这种锁机制就是所谓的间隙锁（Next-Key锁）。

举例来说，假如emp表中只有101条记录，其empid的值分别是
1,2,...,100,101，下面的SQL：

Select \* from  emp where empid &gt; 100 for update;

是一个范围条件的检索，InnoDB不仅会对符合条件的empid值为101的记录加锁，也会对empid大于101（这些记录并不存在）的“间隙”加锁。

InnoDB使用间隙锁的目的，一方面是为了防止幻读，以满足相关隔离级别的要求，对于上面的例子，要是不使用间隙锁，如果其他事务插入了empid大于100的任何记录，那么本事务如果再次执行上述语句，就会发生幻读；另外一方面，是为了满足其恢复和复制的需要。有关其恢复和复制对锁机制的影响，以及不同隔离级别下InnoDB使用间隙锁的情况，在后续的章节中会做进一步介绍。

[]{#_Toc24594 .anchor}**8.13 其它问题**

[]{#_Toc26685 .anchor}**8.13.1 limit20000 如何优化**

*http://uule.iteye.com/blog/2422189*

** 1.子查询优化法**

原始slq语句：select \* from Member limit 10000,100   

先找出第一条数据，然后大于等于这条数据的id就是要获取的数据

 
 **缺点：数据必须是连续的**，可以说不能有where条件，where条件会筛选数据，导致数据失去连续性

这种：

> **Sql代码  **![IMG\_256](media/image256.png){width="0.15625in"
> height="0.14583333333333334in"}

1.  **select** \* **from** Member **where** MemberID &gt;= (**select** MemberID **from** Member limit 100000,1) limit 100   

**2、使用 id 限定优化**

原始sql语句：select\* from orders\_history where type=2 limit
100000,100.

这种方式假设数据表的**id是连续递增的**，则我们根据查询的页数和查询的记录数可以算出查询的id的范围，**可以使用
id between and 来查询：**

> **Java代码  **![IMG\_256](media/image256.png){width="0.15625in"
> height="0.14583333333333334in"}

1.  select \* from orders\_history where type=2 and id between 1000000 and 1000100 limit 100;  

** 3.反向查找优化法**

   当偏移超过一半记录数的时候，先用排序，这样偏移就反转了

   缺点：order
by优化比较麻烦，要增加索引，索引影响数据的修改效率，并且**要知道总记录数**

   ，偏移大于数据的一半

![](media/image257.png){width="5.764583333333333in"
height="2.2909722222222224in"}

[]{#_Toc20705 .anchor}8.13.2 数据库的隔离级别 隔离级别如何实现

（封锁协议 X锁 S锁 GAP锁）

[]{#_Toc11771 .anchor}8.13.3 char varchar text 区别

*https://blog.csdn.net/wxq1987525/article/details/6564380*

具体对这三种类型的说明不做阐述可以查看mysql帮助文档。

**char的总结：\
**     
char最大长度是255字符，注意是**字符数**和**字符集**没关系。可以有默认值，尾部有空格会被截断。\
**varchar的总结：\
**      varchar的最大长度65535是指能存储的字节数，其实最多只能存储65532个字节，还有3个字节用于存储长度。注意是**字节数**这个和**字符集**有关系。一个汉字字符用utf8占用3字节，用gbk占用2字节。可以有默认值，尾部有空格不会截断。\
**text的总结：\
**     
text和varchar基本相同。text会忽略指定的大小这和varchar有所不同，text不能有默认值。尾部有空格不会被截断。text使用额外的2个字节来存储数据的大小，varchar根据存储数据的大小选择用几个字节来存储。text的65535字节全部用来存储数据，varchar则会占用1－3个字节去存储数据大小。\
上面所说的一切只针对mysql，其他数据库可能不同。有不妥的地方请指出

[]{#_Toc16974 .anchor}**8.13.4 drop delete truncate区别**

-   **delete和truncate**只删除表的数据不删除表的结构

-   速度,一般来说:** drop&gt; truncate &gt;delete **

-   **delete**语句是dml,这个操作会放到**rollback
    > segement**中,事务提交之后才生效;\
    > 如果有相应的**trigger**,执行的时候将被触发. **truncate,drop**是ddl,
    > 操作立即生效,原数据不放到r**ollback segment**中,不能回滚.
    > 操作不触发**trigger**. 

drop直接删掉表

truncate删除表中数据，再插入时自增长id又从1开始

delete删除表中数据，可以加where字句。

[]{#_Toc28766 .anchor}**8.13.5 事务**

> 事务（Transaction）是并发控制的基本单位。所谓的事务，它是一个操作序列，这些操作要么都执行，要么都不执行，它是一个不可分割的工作单位。事务是数据库维护数据一致性的单位，在每个事务结束时，都能保持数据一致性。

[]{#_Toc6983 .anchor}**8.13.6 超键、候选键、主键、外键 视图**

超键：在关系中能唯一标识元组的属性集称为关系模式的超键。一个属性可以为作为一个超键，多个属性组合在一起也可以作为一个超键。超键包含候选键和主键。

候选键：是最小超键，即没有冗余元素的超键。

主键：数据库表中对储存数据对象予以唯一和完整标识的数据列或属性的组合。一个数据列只能有一个主键，且主键的取值不能缺失，即不能为空值（Null）。

外键：在一个表中存在的另一个表的主键称此表的外键。

视图是一种虚拟的表，具有和物理表相同的功能。可以对视图进行增，改，查，操作，试图通常是有一个表或者多个表的行或列的子集。对视图的修改不影响基本表。它使得我们获取数据更容易，相比多表查询。

[]{#_Toc22706 .anchor}**8.13.7 存储过程与触发器**

**存储过程**（Stored
Procedure）是一组为了完成特定功能的SQL语句集，经编译后存储在数据库中，用户通过指定存储过程的名字并给定参数（如果该存储过程带有参数）来调用执行它。

![](media/image258.png){width="5.7659722222222225in" height="2.91875in"}

![](media/image259.png){width="5.741666666666666in" height="0.8in"}

B+树和B树的区别 插入节点怎么分裂

有人建议给每张表都建一个自增主键，这样做有什么优点跟缺点

MyISAM、InnoDB的区别(一个B+树叶子节点存的地址，一个是直接存的数据)

sql，group by的理解

对MySQL的了解，和oracle的区别

mybatis中 %与\$的区别

一个成绩表求出有不及格科目的同学

500万数字排序，内存只能容纳5万个，如何排序，如何优化？

平时怎么写数据库的模糊查询（由字典树扯到模糊查询，前缀查询，例如“abc%”，还是索引策略的问题）

数据库里有10000000条用户信息，需要给每位用户发送信息（必须发送成功），要求节省内存（主键索引、分区技术、异步处理）

数据库连接池（druid）、线程池作用等等

数据库设计与优化能力：\
数据库基本知识（存取控制、触发器、存储过程（了解作用）、游标（了解作用）

基本数据库安全

数据库设计，不多讲看看i西科和圈子表结构设计（满足三范式等等），多思考。

并发控制（并发数据不一致性、事务隔离级别、乐观锁与悲观锁等）

mysql锁机制

项目中如何实现事务

数据库设计一般设计成第几范式

mysql用的什么版本 5.7跟5.6有啥区别 提升 MySQL 安全性

问了一个这样的表(三个字段:姓名，id，分数)要求查出平均分大于80的id然后分数降序排序。
然后经过提示用聚合函数avg。select id from table group by id having avg(score) &gt; 80 order by avg(score) desc。

，为什么mysql事务能保证失败回滚 ACID

学生表，成绩表，说出查找学生总成绩大于500的学生的姓名跟总分

一道算法题，在一个整形数组中，找出第三大的数，注意时间效率

主键索引底层的实现原理？B+树

经典的01索引问题？

如何在长文本中快捷的筛选出你的名字？ 全文索引

多列索引及最左前缀原则和其他使用场景

数据库的完整性约束，事务隔离级别，写一个SQL语句，索引的最左前缀原则

数据库悲观锁怎么实现的

建表的原则

索引的内涵和用法

写怎么创建表

给了两条SQL语句，让根据这两条语句建索引（个人想法：主要考虑复合索引只能匹配前缀列的特点）

 select语句实现顺序

那么我们来聊一下数据库。A和B两个表做等值连接(Inner join) 怎么优化 哈希

数据库连接池的理解和优化

.数据库事物，什么是事物，什么情况下会用到事物，举例说明

  Sql 语句。增删改查基本语句，建表建索引。需要注意细节，比如 count 是否计算 null 值的行等。

Sql 语句 分组排序

SQL语句的5个连接概念

-   数据库优化和架构（主要是主从分离和分库分表相关） 分库分表
    跨库join实现 探讨 主从分离和分库分表相关

数据库中间件

-   跨库join

-   读写分离在中间件的实现

-   限流and熔断

-   **行锁适用场景 **

九.网络
=======

9.1.HTTP
--------

### 9.1.1 http请求报文 & http响应报文

**1.http请求报文**

![](media/image260.png){width="5.761805555555555in"
height="1.0715277777777779in"}

http响应报文由状态行，响应头部，空行，响应数据组成\
**2.http响应报文**

HTTP响应由四个部分组成：\
1.状态码(Status
Code)：描述了响应的状态。可以用来检查是否成功的完成了请求。请求失败的情况下，状态码可用来找出失败的原因。如果Servlet没有返回状态码，默认会返回成功的状态码HttpServletResponse.SC\_OK。\
2.HTTP头部(HTTP
Header)：它们包含了更多关于响应的信息。比如：头部可以指定认为响应过期的过期日期，或者是指定用来给用户安全的传输实体内容的编码格式。如何在Serlet中检索HTTP的头部看这里。

3.空行\
4.主体(Body)：它包含了响应的内容。它可以包含HTML代码，图片，等等。主体是由传输在HTTP消息中紧跟在头部后面的数据字节组成的。

### 9.1.2 http报文头部请求头和响应头

![](media/image261.png){width="5.761111111111111in"
height="2.0861111111111112in"}

![](media/image262.png){width="5.763888888888889in"
height="2.6006944444444446in"}

### 9.1.3 http 请求方法

![](media/image263.png){width="5.759722222222222in"
height="0.4041666666666667in"}

![](media/image264.png){width="5.766666666666667in"
height="4.107638888888889in"}

### 9.1.4 http请求过程

以下是 HTTP 请求/响应的步骤：

1、客户端连接到Web服务器

一个HTTP客户端，通常是浏览器，与Web服务器的HTTP端口（默认为80）建立一个TCP套接字连接。例如，http://www.oakcms.cn。

2、发送HTTP请求

通过TCP套接字，客户端向Web服务器发送一个文本的请求报文，一个请求报文由请求行、请求头部、空行和请求数据4部分组成。

3、服务器接受请求并返回HTTP响应

Web服务器解析请求，定位请求资源。服务器将资源复本写到TCP套接字，由客户端读取。一个响应由状态行、响应头部、空行和响应数据4部分组成。

4、释放连接TCP连接

若connection
模式为close，则服务器主动关闭TCP连接，客户端被动关闭连接，释放TCP连接;若connection
模式为keepalive，则该连接会保持一段时间，在该时间内可以继续接收请求;

5、客户端浏览器解析HTML内容

客户端浏览器首先解析状态行，查看表明请求是否成功的状态代码。然后解析每一个响应头，响应头告知以下为若干字节的HTML文档和文档的字符集。客户端浏览器读取响应数据HTML，根据HTML的语法对其进行格式化，并在浏览器窗口中显示。

1.http协议，ajax； 协议的划分

6\. **http 请求流程 **

> **http长连接设置  短链接\
> http怎么记住状态 **

http是无状态的怎么来

### 9.1.4 Get 和 Post 区别

![](media/image265.png){width="5.7625in" height="1.7in"}

![](media/image266.png){width="5.7652777777777775in"
height="1.9340277777777777in"}

![](media/image267.png){width="5.7625in" height="0.3770833333333333in"}

幂等

从定义上看，HTTP方法的幂等性是指一次和多次请求某一个资源应该具有同样的副作用。

post并不是幂等的。

### 9.1.5 http状态码

![](media/image268.png){width="5.758333333333334in"
height="0.8423611111111111in"}

![](media/image269.png){width="5.767361111111111in"
height="0.4152777777777778in"}

![](media/image270.png){width="5.763194444444444in"
height="0.42777777777777776in"}

![](media/image271.png){width="5.764583333333333in"
height="1.1993055555555556in"}

![](media/image272.png){width="5.7652777777777775in" height="0.425in"}

![](media/image273.png){width="5.7652777777777775in"
height="3.1034722222222224in"}

![](media/image274.png){width="5.767361111111111in"
height="0.40347222222222223in"}

![](media/image275.png){width="5.768055555555556in"
height="3.0520833333333335in"}

![](media/image276.png){width="5.7652777777777775in"
height="1.4402777777777778in"}

![](media/image277.png){width="5.766666666666667in"
height="2.6527777777777777in"}

**600 源站没有返回响应头部,只返回实体内容 **

### 9.1.6 http长连接 短连接 HTTP协议是无状态

无状态：HTTP协议是无状态的，指的是协议对于事务处理没有记忆能力，服务器不知道客户端是什么状态。也就是说，打开一个服务器上的网页和上一次打开这个服务器上的网页之间没有任何联系。HTTP是一个无状态的面向连接的协议，无状态不代表HTTP不能保持TCP连接，更不能代表HTTP使用的是UDP协议（无连接）。

https://www.cnblogs.com/gotodsp/p/6366163.html

短连接：在HTTP/1.0中默认使用短连接。也就是说，客户端和服务器每进行一次HTTP操作，就建立一次连接，任务结束就中断连接。当客户端浏览器访问的某个HTML或其他类型的Web页中包含有其他的Web资源（如JavaScript文件、图像文件、CSS文件等），每遇到这样一个Web资源，浏览器就会重新建立一个HTTP会话。

长连接：而从HTTP/1.1起，默认使用长连接，用以保持连接特性。使用长连接的HTTP协议，会在响应头加入这行代码：

Connection:keep-alive

在使用长连接的情况下，当一个网页打开完成后，客户端和服务器之间用于传输HTTP数据的TCP连接不会关闭，客户端再次访问这个服务器时，会继续使用这一条已经建立的连接。Keep-Alive不会永久保持连接，它有一个保持时间，可以在不同的服务器软件（如Apache）中设定这个时间。实现长连接需要客户端和服务端都支持长连接。

HTTP协议的长连接和短连接，实质上是TCP协议的长连接和短连接。

**什么时候用长连接，短连接？  　　**

**长连接**多用于操作频繁，点对点的通讯，而且连接数不能太多情况，。每个TCP连接都需要三步握手，这需要时间，如果每个操作都是先连接，再操作的话那么处理速度会降低很多，所以每个操作完后都不断开，次处理时直接发送数据包就OK了，不用建立TCP连接。例如：数据库的连接用长连接，
如果用短连接频繁的通信会造成socket错误，而且频繁的socket
创建也是对资源的浪费。 \
  \
　　而像WEB网站的http服务一般都用**短链接**，因为长连接对于服务端来说会耗费一定的资源，而像WEB网站这么频繁的成千上万甚至上亿客户端的连接用短连接会更省一些资源，如果用长连接，而且同时有成千上万的用户，如果每个用户都占用一个连接的话，那可想而知吧。所以并发量大，但每个用户无需频繁操作情况下需用短连好

[]{#_Toc7800 .anchor}9.1.7 http1.1与http1.0的区别

1.http1.0需要keep-alive参数来告知服务器要建立一个长连接，而http1.1默认支持长连接

2.HTTP
1.1支持只发送header信息(不带任何body信息)，如果服务器认为客户端有权限请求服务器，则返回100，否则返回401。客户端如果接受到100，才开始把请求body发送到服务器。这样当服务器返回401的时候，客户端就可以不用发送请求body了，节约了带宽。

3.host域 http1.0 没有host域，http1.1才支持这个参数。

4.**带宽优化及网络连接的使用**，HTTP1.0中，存在一些浪费带宽的现象，例如客户端只是需要某个对象的一部分，而服务器却将整个对象送过来了，并且不支持断点续传功能，HTTP1.1则在请求头引入了range头域，它允许只请求资源的某个部分，即返回码是206（Partial
Content），这样就方便了开发者自由的选择以便于充分利用带宽和连接。

[]{#_Toc18110 .anchor}9.1.8 http2.0 与 http1.0的区别

> ***https://www.cnblogs.com/heluan/p/8620312.html***
>
> **新的二进制格式**（Binary
> Format），HTTP1.x的解析是基于文本。基于文本协议的格式解析存在天然缺陷，文本的表现形式有多样性，要做到健壮性考虑的场景必然很多，二进制则不同，只认0和1的组合。基于这种考虑HTTP2.0的协议解析决定采用二进制格式，实现方便且健壮。
>
> **多路复用**（MultiPlexing），即连接共享，建立起一个连接请求后，可以在这个链接上一直发送，不要等待上一次发送完并且受到回复后才能发送下一个（http1.0是这样），是可以同时发送多个请求，互相并不干扰。
>
> **header压缩**，如上文中所言，对前面提到过HTTP1.x的header带有大量信息，而且每次都要重复发送，HTTP2.0利用HPACK对消息头进行压缩传输，客服端和服务器维护一个动态链表（当一个头部没有出现的时候，就插入，已经出现了就用表中的索引值进行替代），将既避免了重复header的传输，又减小了需要传输的大小。（Hpack
> https://www.jianshu.com/p/f44b930cfcac）
>
> **服务端推送**（server
> push），就是客户端请求html的时候，服务器顺带把此html需要的css,js也一起发送给客服端，而不像http1.0中需要请求一次html，然后再请求一次css，然后再请求一次js。

[]{#_Toc958 .anchor}**9.1.9 转发与重定向的区别**

一句话，转发是服务器行为，重定向是客户端行为。为什么这样说呢，这就要看两个动作的工作流程：

**转发过程：**客户浏览器发送http请求----》web服务器接受此请求--》调用内部的一个方法在容器内部完成请求处理和转发动作----》将目标资源发送给客户；在这里，转发的路径必须是同一个web容器下的url，其不能转向到其他的web路径上去，中间传递的是自己的容器内的request。在客户浏览器路径栏显示的仍然是其第一次访问的路径，也就是说客户是感觉不到服务器做了转发的。转发行为是浏览器只做了一次访问请求。

**重定向过程：**客户浏览器发送http请求----》web服务器接受后发送302状态码响应及对应新的location给客户浏览器--》客户浏览器发现是302响应，则**自动**再发送一个新的http请求，请求url是新的location地址----》服务器根据此请求寻找资源并发送给客户。在这里location可以重定向到任意URL，既然是浏览器重新发出了请求，则就没有什么request传递的概念了。在客户浏览器路径栏显示的是其重定向的路径，客户可以观察到地址的变化的。重定向行为是浏览器做了至少两次的访问请求的。

9.2.TCP UDP
-----------

*https://blog.csdn.net/oney139/article/details/8103223*

### 9.2.0 TCP头部

![](media/image278.png){width="5.761805555555555in"
height="4.142361111111111in"}

![](media/image279.png){width="5.763194444444444in"
height="3.5083333333333333in"}

![](media/image280.png){width="5.7625in" height="2.2895833333333333in"}

的IP，TCP协议号。

URG=1\
当URG字段被置1，表示本数据报的数据部分包含紧急信息，此时紧急指针有效。紧急数据一定位于当前数据包数据部分的最前面，紧急指针标明了紧急数据的尾部。如control+c：这个命令要求操作系统立即停止当前进程。此时，这条命令就会存放在数据包数据部分的开头，并由紧急指针标识命令的位置，并URG字段被置1。

> PSH=1\
> 当接收方收到PSH=1的报文后，会立即将数据交付给应用程序，而不会等到缓冲区满后再提交。一些交互式应用需要这样的功能，降低命令的响应时间。
>
> RST=1\
> 当该值为1时，表示当前TCP连接出现严重问题，必须要释放重连。

三次握手需要的信息：暂时需要的信息有：

ACK ：
TCP协议规定，只有ACK=1时有效，也规定连接建立后所有发送的报文的ACK必须为1。

SYN(SYNchronization) ：
在连接建立时用来同步序号。当SYN=1而ACK=0时，表明这是一个连接请求报文。对方若同意建立连接，则应在响应报文中使SYN=1和ACK=1.
因此,  SYN置1就表示这是一个连接请求或连接接受报文。

FIN （finis）即完，终结的意思， 用来释放一个连接。当 FIN = 1
时，表明此报文段的发送方的数据已经发送完毕，并要求释放连接

### 9.2.1 TCP与UDP区别

![](media/image281.png){width="5.763888888888889in"
height="4.270833333333333in"}

UDP首部8个字节，TCP首部最低20个字节。

**对应的协议不同**

**TCP对应的协议：**

（1） **FTP**：定义了文件传输协议，使用21端口。常说某某计算机开了FTP服务便是启动了文件传输服务。下载文件，上传主页，都要用到FTP服务。

（2） **Telnet**：它是一种用于远程登陆的端口，用户可以以自己的身份远程连接到计算机上，通过这种端口可以提供一种基于DOS模式下的通信服务。如以前的BBS是-纯字符界面的，支持BBS的服务器将23端口打开，对外提供服务。

 

（3） **SMTP**：定义了简单邮件传送协议，现在很多邮件服务器都用的是这个协议，用于发送邮件。如常见的免费邮件服务中用的就是这个邮件服务端口，所以在电子邮件设置-中常看到有这么SMTP端口设置这个栏，服务器开放的是25号端口。

（4） **POP3**：它是和SMTP对应，POP3用于接收邮件。通常情况下，POP3协议所用的是110端口。也是说，只要你有相应的使用POP3协议的程序（例如Fo-xmail或Outlook），就可以不以Web方式登陆进邮箱界面，直接用邮件程序就可以收到邮件（如是163邮箱就没有必要先进入网易网站，再进入自己的邮-箱来收信）。

（5）HTTP协议：是从Web服务器传输超文本到本地浏览器的传送协议。

**UDP对应的协议：**

（1） **DNS**：用于域名解析服务，将域名地址转换为IP地址。DNS用的是53号端口。

（2） **SNMP**：简单网络管理协议，使用161号端口，是用来管理网络设备的。由于网络设备很多，无连接的服务就体现出其优势。

（3）** TFTP**(Trival File Transfer
Protocal)，简单文件传输协议，该协议在熟知端口69上使用UDP服务。

### 9.2.2 TCP三次握手

![](media/image282.png){width="5.760416666666667in"
height="3.8631944444444444in"}

1.首先由Client发出请求连接即 SYN=1 ACK=0 (请看头字段的介绍),
TCP规定SYN=1时不能携带数据，但要消耗一个序号,因此声明自己的序号是 seq=x

2.然后 Server 进行回复确认，即 SYN=1 ACK=1 seq=y, ack=x+1,

3.再然后 Client 再进行一次确认，但不用SYN 了，这时即为 ACK=1, seq=x+1,
ack=y+1.然后连接建立，为什么要进行三次握手呢（两次确认）。

**为什么采用三次握手而不是采用两次握手？**

![](media/image283.png){width="5.761111111111111in"
height="3.216666666666667in"}

### 9.2.3 TCP四次挥手

![](media/image284.png){width="5.763194444444444in"
height="4.033333333333333in"}

![](media/image285.png){width="5.758333333333334in"
height="2.1215277777777777in"}

![](media/image286.png){width="5.757638888888889in"
height="0.5354166666666667in"}

TIME\_WAIT阶段要等待2个MSL时间才关闭，因为网络原因可能要重发。CLOSE\_WAIT是要等待自己（通常是服务器）把自己传输东西发送完了。

### 9.2.4 tcp粘包问题 nagle算法

![](media/image287.png){width="5.768055555555556in"
height="2.957638888888889in"}

![](media/image288.png){width="5.759722222222222in"
height="2.841666666666667in"}

![](media/image289.png){width="5.7652777777777775in"
height="3.2152777777777777in"}

### 9.2.5 tcp 如何保证可靠性传输

1.数据包校验：目的是检测数据在传输过程中的任何变化，若校验出包有错，则丢弃报文段并且不给出响应，这时TCP发送数据端超时后会重发数据；

2.对失序数据包重排序：既然TCP报文段作为IP数据报来传输，而IP数据报的到达可能会失序，因此TCP报文段的到达也可能会失序。TCP将对失序数据进行重新排序，然后才交给应用层；

3.丢弃重复数据：对于重复数据，能够丢弃重复数据；

4.应答机制：当TCP收到发自TCP连接另一端的数据，它将发送一个确认。这个确认不是立即发送，通常将推迟几分之一秒；

5.超时重发：当TCP发出一个段后，它启动一个定时器，等待目的端确认收到这个报文段。如果不能及时收到一个确认，将重发这个报文段；

6.流量控制：TCP连接的每一方都有固定大小的缓冲空间。TCP的接收端只允许另一端发送接收端缓冲区所能接纳的数据，这可以防止较快主机致使较慢主机的缓冲区溢出，这就是流量控制。TCP使用的流量控制协议是可变大小的滑动窗口协议。

![](media/image290.png){width="5.761111111111111in"
height="3.4555555555555557in"}

*https://coolshell.cn/articles/11564.html*

*https://coolshell.cn/articles/11609.html*

*http://blog.chinaunix.net/uid-26275986-id-4109679.html*

*https://blog.csdn.net/jhh\_move\_on/article/details/45770087*

### 9.2.6 TCP流量控制 拥塞控制

![](media/image291.png){width="5.763888888888889in"
height="1.1708333333333334in"}

*https://blog.csdn.net/sicofield/article/details/9708383*

拥塞控制

**9.2.6.1 慢开始与拥塞避免**

**1.慢开始**

发送方维持一个叫做**拥塞窗口cwnd（congestion
window）**的状态变量。拥塞窗口的大小取决于网络的拥塞程度，并且动态地在变化。发送方让自己的发送窗口等于拥塞窗口，另外考虑到接受方的接收能力，发送窗口可能小于拥塞窗口。

       慢开始算法的思路就是，不要一开始就发送大量的数据，先探测一下网络的拥塞程度，也就是说由小到大逐渐增加拥塞窗口的大小。

这里用报文段的个数的拥塞窗口大小举例说明慢开始算法，实时拥塞窗口大小是以字节为单位的。如下图：

![](media/image292.png){width="5.75in" height="2.9166666666666665in"}

**解释一下这张图：就是发送方每收到一个确认就cwnd+1，也就是说发送方发送2就收到2个，所以就是cwnd就是4，也就是翻倍成长的道理，每次都是翻倍，也就是指数增长。**

为了防止cwnd增长过大引起网络拥塞，还需设置一个慢开始门限ssthresh状态变量。ssthresh的用法如下：

**当cwnd&lt;ssthresh时，使用慢开始算法。**

**当cwnd&gt;ssthresh时，改用拥塞避免算法。**

**当cwnd=ssthresh时，慢开始与拥塞避免算法任意。**

**2.拥塞避免**

     拥塞避免算法让拥塞窗口缓慢增长，即每经过一个往返时间RTT就把发送方的拥塞窗口cwnd加1，而不是加倍。这样拥塞窗口按线性规律缓慢增长。

无论是在**慢开始阶段**还是在**拥塞避免阶段**，只要发送方判断网络出现拥塞（其根据就是没有收到确认，虽然没有收到确认可能是其他原因的分组丢失，但是因为无法判定，所以都当做拥塞来处理），就把慢开始门限设置为出现拥塞时的发送窗口大小的一半。然后把拥塞窗口设置为1，执行慢开始算法。如下图：

![](media/image293.png){width="5.425in" height="2.54375in"}

**9.2.6.2 快速重传快速恢复**

   快重传要求接收方在收到一个失序的报文段后就立即发出重复确认（为的是使发送方及早知道有报文段没有到达对方）而不要等到自己发送数据时捎带确认。快重传算法规定，发送方只要一连收到三个重复确认就应当立即重传对方尚未收到的报文段，而不必继续等待设置的重传计时器时间到期。如下图：

![](media/image294.png){width="4.666666666666667in"
height="2.683333333333333in"}

快重传配合使用的还有快恢复算法，有以下两个要点:

①当发送方连续收到三个重复确认时，就执行“乘法减小”算法，把ssthresh门限减半。但是接下去并不执行慢开始算法。

②考虑到如果网络出现拥塞的话就不会收到好几个重复的确认，所以发送方现在认为网络可能没有出现拥塞。所以此时不执行慢开始算法，而是将cwnd设置为ssthresh的大小，然后执行拥塞避免算法。如下图：

![](media/image295.png){width="5.768055555555556in"
height="2.5548611111111112in"}

### 9.2.7 滑动窗口机制

*https://blog.csdn.net/GitChat/article/details/78546898*

![](media/image296.png){width="5.7652777777777775in"
height="4.1305555555555555in"}

![](media/image297.png){width="5.764583333333333in"
height="2.1333333333333333in"}

### 9.2.8 TCP 状态转移

![IMG\_256](media/image298.jpeg){width="5.208333333333333in"
height="6.604166666666667in"}

**1.CLOSED**：起始

点，在超时或者连接关闭时候进入此状态。

**2.LISTEN**：svr端在等待连接过来时候的状态，svr端为此要调用socket，
bind,listen函数，就能

进入此状态。此称为应用程序被动打开（等待客户端来连接）。

**3.SYN\_SENT**:客户端发起连接，发送SYN给服务器端。如果服务器端不能连接，则直接进入

CLOSED状态。

**4.SYN\_RCVD**：跟3对应，服务器端接受客户端的SYN请求，服务器端由LISTEN状态进入

SYN\_RCVD状态。同时服务器端要回应一个ACK，同时发送一个SYN给客户端；另外一种情

况，客户端在发起SYN的同时接收到服务器端得SYN请求，客户端就会由SYN\_SENT到

SYN\_RCVD状态。

5.  **ESTABLISHED**：服务器端和客户端在完成3次握手进入状态，说明已经可以开始传输数据了

以上是建立连接时服务器端和客户端产生的状态转移说明。相对来说比较简单明了，如果你

对三次握手比较熟悉，建立连接时的状态转移还是很容易理解。

接下来服务器端和客户端就进行数据传输。。。。，当然，里面也大有学问，就此打住，稍

后再表。

下面，我们来看看连接关闭时候的状态转移说明，关闭需要进行4次双方的交互，还包括要处

理一些善后工作（TIME\_WAIT状态），注意，这里主动关闭的一方或被动关闭的一方不是指

特指服务器端或者客户端，是相对于谁先发起关闭请求来说的：

**6.FIN\_WAIT\_1**:主动关闭的一方，由状态5进入此状态。具体的动作时发送FIN给对方。

**7.FIN\_WAIT\_2**:主动关闭的一方，接收到对方的FIN
ACK，进入此状态。由此不能再接收对方

的数据。但是能够向对方发送数据。

**8.CLOSE\_WAIT**：接收到FIN以后，被动关闭的一方进入此状态。具体动作时接收到FIN，同

时发送ACK。

**9.LAST\_ACK**：被动关闭的一方，发起关闭请求，由状态8进入此状态。具体动作时发送FIN

给对方，同时在接收到ACK时进入CLOSED状态。

**10.CLOSING**：两边同时发起关闭请求时，会由FIN\_WAIT\_1进入此状态。具体动作是，接收

到FIN请求，同时响应一个ACK。

**11.TIME\_WAIT**：最纠结的状态来了。从状态图上可以看出，有3个状态可以转化成它，我们

一一来分析：

a.由FIN\_WAIT\_2进入此状态：在双方不同时发起FIN的情况下，主动关闭的一方在完成自身发

起的关闭请求后，接收到被动关闭一方的FIN后进入的状态。

b.由CLOSING状态进入:双方同时发起关闭，都做了发起FIN的请求，同时接收到了FIN并做了

ACK的情况下，由CLOSING状态进入。

c.由FIN\_WAIT\_1状态进入：同时接受到FIN（对方发起），ACK（本身发起的FIN回应），与

b的区别在于本身发起的FIN回应的ACK先于对方的FIN请求到达，而b是FIN先到达。这种情

况概率最小。

### 9.2.9 TIME\_WAIT 和 CLOSE\_WAIT

关闭的4次连接最难理解的状态是TIME\_WAIT，存在TIME\_WAIT的2个理由：

1.可靠地实现TCP全双工连接的终止。

2.允许老的重复分节在网络中消逝。

*https://blog.csdn.net/wu936754331/article/details/49104497*

*https://blog.csdn.net/u013616945/article/details/77510925*

**1.为什么time\_wait需要2\*MSL等待时间？**\
MSL就是maximum segment
lifetime(最大分节生命期），这是一个IP数据包能在互联网上生存的最长时间，超过这个时间将在网络中消失。

现在我们考虑终止连接时的被动方发送了一个FIN，然后主动方回复了一个ACK，然而这个ACK可能会丢失，这会造成被动方重发FIN，这个FIN可能会在互联网上存活MSL。\
如果没有TIME\_WAIT的话，假设连接1已经断开，然而其被动方最后重发的那个FIN(或者FIN之前发送的任何TCP分段)还在网络上，然而连接2重用了连接1的所有的5元素(源IP，目的IP，TCP，源端口，目的端口)，刚刚将建立好连接，连接1迟到的FIN到达了，这个FIN将以比较低但是确实可能的概率终止掉连接

2\. 大量的time\_wait如何解决

> ![](media/image299.png){width="5.763194444444444in"
> height="3.6256944444444446in"}
>
> ![](media/image300.png){width="5.759722222222222in"
> height="1.8027777777777778in"}

**2. 当一个tcp监听了80端口后，Udp还能否监听80端口**

答：由于TCP/IP传输层的两个协议TCP和UDP是完全独立的两个软件模块，因此各自的端口号也相互独立，如TCP有一个255号端口，UDP也可以有一个255号端口，二者并不冲突。

。

9.tcp的滑动端口机制 如何保证不重复发送的

10.描述TCP滑动窗口机制，如何实现流控

11.防止xxs攻击和sql攻击等等

12.TCP/IP 有几层，每层有何含义

> *https://blog.csdn.net/xieyutian1990/article/details/23789871*
>
> ![](media/image301.png){width="4.186805555555556in"
> height="3.176388888888889in"}

3.**为什么TIME\_WAIT状态还需要等2\*MSL（**Max
SegmentLifetime，最大分段生存期**）秒之后才能返回到CLOSED状态呢？**

因为虽然双方都同意关闭连接了，而且握手的4个报文也都发送完毕，按理可以直接回到CLOSED状态（就好比从SYN\_SENT状态到ESTABLISH状态那样），但是我们必须假想网络是不可靠的，你无法保证你最后发送的ACK报文一定会被对方收到，就是说对方处于LAST\_ACK状态下的SOCKET可能会因为超时未收到ACK报文，而重发FIN报文，所以这个TIME\_WAIT状态的作用就是用来重发可能丢失的ACK报文。

13\. tcp包可以被篡改吗？

9.7.计算机网络分层模型 
-----------------------

[]{#_Toc20602 .anchor}**9.7.1 osi七层**

![](media/image302.png){width="5.7652777777777775in"
height="6.038888888888889in"}

![](media/image303.png){width="5.767361111111111in" height="1.475in"}

![](media/image304.png){width="5.763194444444444in"
height="3.578472222222222in"}

[]{#_Toc5563 .anchor}**9.7.2 APR**

(1)首先，每个主机都会在自己的ARP缓冲区中建立一个ARP列表，以表示IP地址和MAC地址之间的对应关系。

（2）当源主机要发送数据时，首先检查ARP列表中是否有对应IP地址的目的主机的MAC地址，如果有，则直接发送数据，如果没有，就向本网段的所有主机发送ARP数据包，该数据包包括的内容有：源主机IP地址，源主机MAC地址，目的主机的IP地址。

（3）当本网络的所有主机收到该ARP数据包时，首先检查数据包中的IP地址是否是自己的IP地址，如果不是，则忽略该数据包，如果是，则首先从数据包中取出源主机的IP和MAC地址写入到ARP列表中，如果已经存在，则覆盖，然后将自己的MAC地址写入ARP响应包中，告诉源主机自己是它想要找的MAC地址。

（4）源主机收到ARP响应包后。将目的主机的IP和MAC地址写入ARP列表，并利用此信息发送数据。如果源主机一直没有收到ARP响应数据包，表示ARP查询失败。

广播发送ARP请求，单播发送ARP响应。

[]{#_Toc13905 .anchor}**9.7.3 ICMP 协议**

ICMP是InternetControl Message
Protocol，因特网控制报文协议。它是TCP/IP协议族的一个子协议，用于在IP主机、路由器之间传递控制消息。控制消息是指网络通不通、主机是否可达、路由器是否可用等网络本身的消息。这些控制消息虽然并不传输用户数据，但是对于用户数据的传递起着重要的作用。ICMP报文有两种：差错报告报文和询问报文。

[]{#_Toc30193 .anchor}**9.7.4 DNCP协议**

动态主机配置协议，是一种让系统得以连接到网络上，并获取所需要的配置参数手段。通常被应用在大型的局域网络环境中，主要作用是集中的管理、分配IP地址，使网络环境中的主机动态的获得IP地址、Gateway地址、DNS服务器地址等信息，并能够提升地址的使用率。

[]{#_Toc15258 .anchor}9.7.5 RARP协议

逆地址解析协议，作用是完成硬件地址到IP地址的映射，主要用于无盘工作站，因为给无盘工作站配置的IP地址不能保存。

[]{#_Toc25331 .anchor}**9.7.6 路由选择协议OSPF RIP**

**RIP：(距离向量路由)**

![](media/image305.png){width="5.768055555555556in"
height="2.8506944444444446in"}

***https://blog.csdn.net/xuzhiwangray/article/details/50502233***

**RIP：1.A收到附近节点C的路由表信息，然后将附近节点C作为下一跳，那么A的距离就得在C上加1**

1.  **然后合并新的路由节点信息，合并过程：**

（1 ）无新信息，不改变

（2 ）新的项目，直接添加

（3 ）相同的下一跳，更新

（4 ）不同的下一跳，距离更短则更新距离和下一跳地址，否则不变

> **OSPF：(链路状态路由）**
>
> ![](media/image306.png){width="5.7652777777777775in"
> height="4.199305555555555in"}

[]{#_Toc12823 .anchor}**9.7.7 SNMP **

**简单网络管理协议（SNMP），由一组网络管理的标准组成，包含一个应用层协议（application
layer protocol）、数据库模型（database
schema）和一组资源对象。该协议能够支持网络管理系统，用以监测连接到网络上的设备是否有任何引起管理上关注的情况。**

[]{#_Toc10895 .anchor}**9.7.8 SMTP**

SMTP（Simple Mail Transfer
Protocol）即简单邮件传输协议,它是一组用于由源地址到目的地址传送邮件的规则，由它来控制信件的中转方式。

9.9 IP
------

[]{#_Toc14400 .anchor}**1.IP报文**

![](media/image307.png){width="5.7659722222222225in"
height="3.1527777777777777in"}

2.  []{#_Toc30077 .anchor}**IP地址类别**

![](media/image308.png){width="5.759027777777778in" height="2.24375in"}

2.  []{#_Toc7351 .anchor}**特殊的地址**

> ![](media/image309.png){width="5.7659722222222225in"
> height="2.629861111111111in"}

2.  []{#_Toc4324 .anchor}**私有地址**

> ![](media/image310.png){width="5.763194444444444in"
> height="1.601388888888889in"}

9.10 网络攻击
-------------

[]{#_Toc24122 .anchor}**1.SYN Flood攻击**

关于SYN Flood攻击。一些恶意的人就为此制造了SYN
Flood攻击——给服务器发了一个SYN后，就下线了，于是服务器需要默认等63s才会断开连接，这样，攻击者就可以把服务器的syn连接的队列耗尽，让正常的连接请求不能处理。于是，Linux下给了一个叫tcp\_syncookies的参数来应对这个事——当SYN队列满了后，TCP会通过源地址端口、目标地址端口和时间戳打造出一个特别的Sequence
Number发回去（又叫cookie），如果是攻击者则不会有响应，如果是正常连接，则会把这个
SYN
Cookie发回来，然后服务端可以通过cookie建连接（即使你不在SYN队列中）。请注意，请先千万别用tcp\_syncookies来处理正常的大负载的连接的情况。因为，synccookies是妥协版的TCP协议，并不严谨。对于正常的请求，你应该调整三个TCP参数可供你选择，第一个是：tcp\_synack\_retries
可以用他来减少重试次数；第二个是：tcp\_max\_syn\_backlog，可以增大SYN连接数；第三个是：tcp\_abort\_on\_overflow
处理不过来干脆就直接拒绝连接了。

2.  []{#_Toc25622 .anchor}**DDOS攻击**

DDoS攻击是Distributed Denial of
Service的缩写，即不法黑客组织通过控制服务器等资源，发动对包括国家骨干网络、重要网络设施、政企或个人网站在内的互联网上任一目标的攻击，致使目标服务器断网，最终停止提供服务。

预防:1.高防服务器 主要是指能独立硬防御 50Gbps
以上的服务器，能够帮助网站拒绝服务攻击，定期扫描网络主节点等2.DDoS
清洗会对用户请求数据进行实时监控，及时发现DOS攻击等异常流量，在不影响正常业务开展的情况下清洗掉这些异常流量。3.CDN
加速 在现实中，CDN
服务将网站访问流量分配到了各个节点中，这样一方面隐藏网站的真实
IP，另一方面即使遭遇 DDoS
攻击，也可以将流量分散到各个节点中，防止源站崩溃。

[]{#_Toc18254 .anchor}**3.DNS欺骗**

DNS欺骗就是攻击者冒充 域名服务器 的一种欺骗行为

预防：1.使用入侵检测系统 2.使用DNSSEC

4.  []{#_Toc9776 .anchor}**重放攻击**

重放攻击又称重播攻击、回放攻击，是指攻击者发送一个目的主机已接收过的包，来达到欺骗系统的目的，主要用于身份认证过程，破坏认证的正确性。

预防：1.加随机数 2.加时间戳

[]{#_Toc31518 .anchor}**5.SQL注入**

所谓SQL注入，就是通过把SQL命令插入到Web表单提交或输入域名或页面请求的查询字符串，最终达到欺骗服务器执行恶意的SQL命令。

预防：1.**加密处理**
将用户登录名称、密码等数据加密保存。加密用户输入的数据，然后再将它与数据库中保存的数据比较，这相当于对用户输入的数据进行了“消毒”处理，用户输入的数据不再对数据库有任何特殊的意义，从而也就防止了攻击者注入SQL命令。

2\. **确保数据库安全**
只给访问数据库的web应用功能所需的最低的权限，撤销不必要的公共许可3.**输入验证**
检查用户输入的合法性，确信输入的内容只包含合法的数据。数据检查应当在客户端和服务器端都执行之所以要执行服务器端验证，是为了弥补客户端验证机制脆弱的安全性。

![](media/image311.png){width="5.768055555555556in"
height="4.250694444444444in"}

9.11 DNS 浏览器中输入URL到页面加载的发生了什么
----------------------------------------------

*https://blog.csdn.net/dojiangv/article/details/51794535*

1.  **DNS的解析流程**

![](media/image312.png){width="5.766666666666667in"
height="2.9180555555555556in"}

[]{#_Toc27883 .anchor}CDN

其中在DNS通过域名解析成IP地址的过程中，会涉及到DNS重定向的问题，

定义：CDN，英文Content Delivery
Network，中文翻译是内容分发网络，目的就是通过现有的Internet中增加一新的网络架构，将网站内容发布到离用户最近的网络“边缘”，提高用户访问网站的速度，所以更像是增加了一层CACHE（缓存）层

功能：当用户访问加入CDN服务的网站时，域名解析请求将最终交给全局负载均衡DNS进行处理。全局负载均衡DNS通过一组预先定义好的策略，将当时最接近用户的节点地址提供给用户，使用户能够得到快速的服务。

组成：每个CDN节点由两部分组成：负载均衡设备和高速缓存服务器

负载均衡设备负责每个节点中各个Cache的负载均衡，保证节点的工作效率；同时，负载均衡设备还负责收集节点与周围环境的信息，保持与全局负载DNS的通信，实现整个系统的负载均衡。

高速缓存服务器（Cache）负责存储客户网站的大量信息，就像一个靠近用户的网站服务器一样响应本地用户的访问请求。

1.  **在浏览器中输入www.baidu.com后执行的全部过程**

1.客户端浏览器通过DNS解析到www.baidu.com的IP地址为220.181.0.1，通过这个ip地址找到客户端到服务器的路径，客户端浏览器发起一个http会话到220.181.0.1，然后通过TCP进行封装数据包，输入到网络层。

2.在客户端的传输层，把HTTP会话请求分成报文段，添加源和目的端口，如服务器端用80端口监听客户端的请求，客户端由系统随机选择一个端口，如5000，与客户端进行交换，服务器把相应的请求返回给客户端的5000端口。然后使用ip层的ip地址查找目的端。

3.客户端的网络层不用关心应用层和传输层的东西，主要做的是通过查找路由表确定如何到达服务器，期间可能经过多个路由器。

4,。客户端的链路层，包通过链路层发送到路由器，通过邻居协议查找给定的ip地址和MAC地址，然后发送ARP请求查找目的地址，如果得到回应后就可以使用ARP的请求应答交换的ip数据包现在就可以传输了，然后发送Ip数据包到达服务器的地址。

DNS均衡

9.12 https ssl
--------------

### 9.12.1 什么是https

> HTTPS协议是由SSL+HTTP协议构建的可进行加密传输、身份认证的网络协议，要比http协议安全。

[]{#_Toc16142 .anchor}**9.12.2 https与http区别**

> HTTPS和HTTP的区别主要如下：

　　1）https协议需要到ca申请证书，一般免费证书较少，因而需要一定费用。

　　2）http是超文本传输协议，信息是明文传输，https则是具有安全性的ssl加密传输协议。

3）http和https使用的是完全不同的连接方式，用的端口也不一样，前者是80，后者是443。 \
　　 \
　　4）http的连接很简单，是无状态的；HTTPS协议是由SSL+HTTP协议构建的可进行加密传输、身份认证的网络协议，比http协议安全。 

1\. HTTP 的 URL 以 http:// 开头，而 HTTPS 的 URL 以 https:// 开头\
2. HTTP 是不安全的，而 HTTPS 是安全的\
4. 在 OSI 网络模型中，HTTP 工作于应用层，而 HTTPS 工作在传输层\
5. HTTP 无需加密，而 HTTPS 对传输的数据进行加密\
6. HTTP 无需证书，而 HTTPS 需要认证证书

![](media/image313.png){width="5.761805555555555in"
height="1.5541666666666667in"}

[]{#_Toc17330 .anchor}9.12.3 https的通信过程

![](media/image314.png){width="4.229166666666667in" height="4.90625in"}

文字简述：客户端A和服务器B之间的交互

1.  A与B通过TCP建立链接，初始化SSL层。

2.  进行SSL握手，A发送https请求，传送客户端SSL协议版本号、支持的加密算法、随机数等。

3.  服务器B把CA证书（包含B的公钥），把自己支持的加密算法、随机数等回传给A。

4.  A接收到CA证书，验证证书有效性。

5.  校验通过，客户端随机产生一个字符串作为与B通信的对称密钥，通过CA证书解出服务器B的公钥，对其加密，发送给服务器。

6.  B用私钥解开信息，得到随机的字符串（对称密钥），利用这个密钥作为之后的通信密钥。

7.  客户端向服务器发出信息，指明后面的数据使用该对称密钥进行加密，同时通知服务器SSL握手结束。

8.  服务器接收到信息，使用对称密钥通信，通知握手接收。

9.  SSL握手结束，使用对称密钥加密数据。

[]{#_Toc23969 .anchor}9.12.4 SSL工作原理

> ***https://blog.csdn.net/ENERGIE1314/article/details/54581411/***
>
> **三种协议：1.握手协议 2.记录协议 3，警报协议**

1.  **RSA握手协议 **

第一步，Client给出协议版本号、一个客户端生成的随机数（Client
random），以及客户端支持的加密方法。

第二步，Server确认双方使用的加密方法，并给出数字证书、以及一个服务器生成的随机数（Server
random）。

第三步，Client确认数字证书有效，然后生成一个新的随机数（Premaster
secret），并使用数字证书中的公钥，加密这个随机数，发给Server。

第四步，Server使用自己的私钥，获取Client发来的随机数（即Premaster
secret）。

第五步，Client和Server根据约定的加密方法，使用前面的三个随机数，生成”对话密钥”（session
key），用来加密接下来的整个对话过程。

1.  **记录协议**

> 记录协议 对数据传输提供保密性和完整性
>
> ![](media/image315.png){width="5.7659722222222225in"
> height="3.303472222222222in"}

1.  **警报协议**

![](media/image316.png){width="5.766666666666667in"
height="0.2923611111111111in"}

建立连接的过程客户端跟服务端会交换什么信息(参考TCP报文结构)

丢包如何解决重传的消耗

traceroute实现原理

select和poll区别？

在不使用WebSocket情况下怎么实现服务器推送的一种方法

可以使用客户端定时刷新请求或者和TCP保持心跳连接实现。

查看磁盘读写吞吐量？

PING位于哪一层

网络重定向，说下流程

controller怎么处理的请求：路由

.IP地址分为几类，每类都代表什么，私网是哪些

十 操作系统
===========

*http://c.biancheng.net/cpp/html/2611.html*

操作系统概述：

操作系统用来协调软件与底层硬件，相当于彼此的接口

操作系统有进程管理，内存管理，文件管理，输入输出管理。

内存管理的功能有：

-   内存空间的分配与回收：由操作系统完成主存储器空间的分配和管理，使程序员摆脱存储分配的麻烦，提高编程效率。

-   地址转换：在多道程序环境下，程序中的逻辑地址与内存中的物理地址不可能一致，因此存储管理必须提供地址变换功能，把逻辑地址转换成相应的物理地址。

-   内存空间的扩充：利用虚拟存储技术或自动覆盖技术，从逻辑上扩充内存。

-   存储保护：保证各道作业在各自的存储空间内运行，.互不干扰。

10.1进程线程
------------

### 10.1.1．进程线程区别

进程是系统进行资源分配和调度的一个独立单位，最小的资源管理单位。线程是进程的一个实体，是CPU调度和分派的基本单位，它是比进程更小的能独立运行的基本单位，最小的CPU执行单元。

线程拥有的资源：程序计数器 寄存器 栈 状态字

### 10.1.2 进程通信方式

![](media/image317.png){width="5.7652777777777775in"
height="3.795138888888889in"}

共享内存：共享内存可以说是最有用的进程间通信方式，也是最快的IPC形式。两个不同进程A、B共享内存的意思是，同一块物理内存被映射到进程A、B各自的进程地址空间。进程A可以即时看到进程B对共享内存中数据的更新，反之亦然。由于多个进程共享同一块内存区域，必然需要某种同步机制，互斥锁和信号量都可以。

[]{#_Toc28862 .anchor}**10.1.3 僵尸进程**

**1 什么是僵尸进程： **\
当子进程比父进程先结束，而父进程又没有回收子进程，释放子进程占用的资源，此时子进程将成为一个僵尸进程。

**2 怎样来清除僵尸进程： **\
1.改写父进程，在子进程死后要为它收尸。具体做法是接管SIGCHLD信号。子进程死后，会发送SIGCHLD信号给父进程，父进程收到此信号后，执行waitpid()函数为子进程收尸。这是基于这样的原理：就算父进程没有调用wait，内核也会向它发送SIGCHLD消息，尽管对的默认处理是忽略，如果想响应这个消息，可以设置一个处理函数。 \
2.把父进程杀掉。父进程死后，僵尸进程成为”孤儿进程”，过继给1号进程init，init始终会负责清理僵尸进程．它产生的所有僵尸进程也跟着消失。 

[]{#_Toc10832 .anchor}**10.1.4 进程同步 PV 信号量**

*https://blog.csdn.net/leves1989/article/details/3305609*

首先应弄清***PV*操作的含义**：*PV*操作由*P*操作原语和*V*操作原语组成（原语是不可中断的过程），对信号量进行操作，具体定义如下：*\
    P*（*S*）：①将信号量*S*的值减*1*，即*S=S−1*；*\
           *②如果*S≥0*，则该进程继续执行；否则该进程置为等待状态，排入等待队列。*\
    V*（*S*）：①将信号量*S*的值加*1*，即*S=S+1*；*\
           *②如果*S&gt;0*，则该进程继续执行；否则释放队列中第一个等待信号量的进程。***\
PV*操作的意义**：我们用信号量及*PV*操作来实现进程的同步和互斥。*PV*操作属于进程的低级通信。

**什么是信号量**？信号量（*semaphore*）的数据结构为一个值和一个指针，指针指向等待该信号量的下一个进程。信号量的值与相应资源的使用情况有关。当它的值大于*0*时，表示当前可用资源的数量；当它的值小于*0*时，其绝对值表示等待使用该资源的进程个数。注意，信号量的值仅能由*PV*操作来改变。*\
* *    *一般来说，信号量*S≥0*时，*S*表示可用资源的数量。执行一次*P*操作意味着请求分配一个单位资源，因此*S*的值减*1*；当*S&lt;0*时，表示已经没有可用资源，请求者必须等待别的进程释放该类资源，它才能运行下去。而执行一个*V*操作意味着释放一个单位资源，因此*S*的值加*1*；若*S≤0*，表示有某些进程正在等待该资源，因此要唤醒一个等待状态的进程，使之运行下去。

10.2 死锁
---------

![](media/image318.png){width="5.7659722222222225in"
height="0.6930555555555555in"}

![](media/image319.png){width="5.756944444444445in"
height="1.729861111111111in"}

![](media/image320.png){width="5.7625in" height="3.4451388888888888in"}

![](media/image321.png){width="5.7652777777777775in" height="0.93125in"}

![](media/image322.png){width="5.754861111111111in" height="0.675in"}

[]{#_Toc24896 .anchor}**10.2.1 死锁避免-银行家算法**

我们可以把操作系统看作是银行家，操作系统管理的资源相当于银行家管理的资金，进程向操作系统请求分配资源相当于用户向银行家贷款。

为保证资金的安全，银行家规定：

\(1) 当一个顾客对资金的最大需求量不超过银行家现有的资金时就可接纳该顾客；

\(2) 顾客可以分期贷款，但贷款的总数不能超过最大需求量；

(3)
当银行家现有的资金不能满足顾客尚需的贷款数额时，对顾客的贷款可推迟支付，但总能使顾客在有限的时间里得到贷款；

\(4) 当顾客得到所需的全部资金后，一定能在有限的时间里归还所有的资金.

操作系统按照银行家制定的规则为进程分配资源，当进程首次申请资源时，要测试该进程对资源的最大需求量，如果系统现存的资源可以满足它的最大需求量则按当前的申请量分配资源，否则就推迟分配。当进程在执行中继续申请资源时，先测试该进程本次申请的资源数是否超过了该资源所剩余的总量。若超过则拒绝分配资源，若能满足则按当前的申请量分配资源，否则也要推迟分配。

[]{#_Toc17642 .anchor}**10.2.2 死锁避免-安全序列**

**安全序列**

安全序列是指对当前申请资源的进程排出一个序列，保证按照这个序列分配资源完成进程，不会发生“酱油和醋”的尴尬问题。

我们假设有进程P1,P2,.....Pn\
则安全序列要求满足：Pi(1&lt;=i&lt;=n)需要资源&lt;=剩余资源 + 分配给Pj(1
&lt;= j &lt; i)资源\
为什么等号右边还有已经被分配出去的资源？想想银行家那个问题，分配出去的资源就好比第二个开发商，人家能还回来钱，咱得把这个考虑在内。

10.3 同步 异步 阻塞 非阻塞
--------------------------

![](media/image323.png){width="5.754861111111111in" height="2.0875in"}

*https://www.cnblogs.com/George1994/p/6702084.html*

**1 例子**

故事：老王烧开水。

出场人物：老张，水壶两把（普通水壶，简称水壶；会响的水壶，简称响水壶）。

老王想了想，有好几种等待方式

1.老王用水壶煮水，并且站在那里，不管水开没开，每隔一定时间看看水开了没。－**同步阻塞**

老王想了想，这种方法不够聪明。

2.老王还是用水壶煮水，不再傻傻的站在那里看水开，跑去寝室上网，但是还是会每隔一段时间过来看看水开了没有，水没有开就走人。－**同步非阻塞**

老王想了想，现在的方法聪明了些，但是还是不够好。

3.老王这次使用高大上的响水壶来煮水，站在那里，但是不会再每隔一段时间去看水开，而是等水开了，水壶会自动的通知他。－**异步阻塞**

老王想了想，不会呀，既然水壶可以通知我，那我为什么还要傻傻的站在那里等呢，嗯，得换个方法。

4.老王还是使用响水壶煮水，跑到客厅上网去，等着响水壶自己把水煮熟了以后通知他。－**异步非阻塞**

老王豁然，这下感觉轻松了很多。

> **同步和异步**
>
> 同步就是烧开水，需要自己去轮询（每隔一段时间去看看水开了没），异步就是水开了，然后水壶会通知你水已经开了，你可以回来处理这些开水了。\
> 同步和异步是相对于操作结果来说，会不会等待结果返回。
>
> **阻塞和非阻塞**
>
> 阻塞就是说在煮水的过程中，你不可以去干其他的事情，非阻塞就是在同样的情况下，可以同时去干其他的事情。阻塞和非阻塞是相对于线程是否被阻塞。

其实，这两者存在本质的区别，它们的修饰对象是不同的。阻塞和非阻塞是指**进程访问的数据如果尚未就绪，进程是否需要等待**，简单说这相当于函数内部的实现区别，也就是未就绪时是直接返回还是等待就绪。\
而同步和异步是指**消息通信机制**,同步一般指主动请求并等待I/O操作完毕的方式,当数据就绪后在读写的时候必须阻塞,异步则指主动请求数据后便可以继续处理其它任务,随后等待I/O,操作完毕的通知,这可以使进程在数据读写时也不阻塞。

[]{#_Toc25044 .anchor}**10.4 操作系统CPU调度算法**

**由于要执行的进程的数目是多于处理器的数目，所以需要处理器去决定下一次运行哪个进程**

**进程就是作业**

1.**先来先服务调度算法（FCFS）**:就是按照各个作业进入系统的自然次序来调度作业。这种调度算法的优点是实现简单，公平。其缺点是没有考虑到系统中各种资源的综合使用情况，往往使短作业的用户不满意，因为短作业等待处理的时间可能比实际运行时间长得多。 

2.**短作业优先调度算法 (SPF):** 就是优先调度并处理短作业，所谓短是指作业的运行时间短。而在作业未投入运行时，并不能知道它实际的运行时间的长短，因此需要用户在提交作业时同时提交作业运行时间的估计值。  

3.**最高响应比优先算法(HRN)：**FCFS可能造成短作业用户不满，SPF可能使得长作业用户不满，于是提出HRN，选择响应比最高的作业运行。响应比=1+作业等待时间/作业处理时间。

4**. 基于优先数调度算法(HPF)：**每一个作业规定一个表示该作业优先级别的整数，当需要将新的作业由输入井调入内存处理时，优先选择优先数最高的作业。

5.时间片轮转调度算法

时间片轮转调度算法主要适用于分时系统。在这种算法中，系统将所有就绪进程按到达时间的先后次序排成一个队列，进程调度程序总是选择就绪队列中第一个进程执行，即先来先服务的原则，但仅能运行一个时间片，如100ms。在使用完一个时间片后，即使进程并未完成其运行，它也必须释放出（被剥夺）处理机给下一个就绪的进程，而被剥夺的进程返回到就绪队列的末尾重新排队，等候再次运行。

[]{#_Toc30465 .anchor}**10.5 内存管理方式（页存储 段存储 段页存储）**

**页存储**

  为了便于在内存中找到进程的每个页面所对应的物理块，系统为每个进程建立一张页表，记录页面在内存中对应的物理块号，页表一般存放在内存中。在配置了页表后，进程执行时，通过查找该表，即可找到每页在内存中的物理块号。可见页表作用是实现从页号到物理块号的地址映射，这种是**页存储**管理方式。如下图所示： \
![1](media/image324.png){width="3.1354166666666665in"
height="2.3645833333333335in"}

[]{#t3 .anchor}**段存储**

  将用户程序地址空间分成若干个大小不等的段，每段可以定义一组相对完整的逻辑信息。存储分配时，以段为单位，段与段在内存中可以不相邻接，也实现了离散分配，这种是**段存储**管理方式。如下图所示： \
![1](media/image325.png){width="3.7604166666666665in" height="2.375in"}

[]{#t4 .anchor}**段页存储**

  作业的地址空间首先被分成若干个逻辑分段，每段都有自己的段号，然后再将每段分成若干个大小相等的页。对于主存空间也分成大小相等的页，主存的分配以页为单位，这种是**段页存储**管理方式。如下图所示： \
![1](media/image326.png){width="4.770833333333333in"
height="2.2083333333333335in"}

[]{#_Toc27581 .anchor}**10.6 页面置换算法**

[]{#_Toc32301 .anchor}**10.6.1 概念**

缺页中断：缺页中断就是要访问的页不在主存，需要操作系统将其调入主存后再进行访问。

页面置换算法：在地址映射过程中，若在页面中发现所要访问的页面不在内存中，则产生缺页中断。当发生缺页中断时，如果操作系统内存中没有空闲页面，则操作系统必须在内存选择一个页面将其移出内存，以便为即将调入的页面让出空间。而用来选择淘汰哪一页的规则叫做页面置换算法。

[]{#_Toc3239 .anchor}10.6.2 OPT **最优页面置换算法**

寻找在将来的时间段内，最晚被访问到的页面，然后将其置换到。（无法预知未来，不现实）

[]{#_Toc2250 .anchor}**10.6.3** 先进先出置换算法（FIFO）

最简单的页面置换算法是先入先出（FIFO）法。这种算法的实质是，总是选择在主存中停留时间最长（即最老）的一页置换，即**先进入内存的页，先退出内存**。

[]{#_Toc29399 .anchor}**10.6.4 最近最久未使用（LRU）算法**

它的实质是，当需要置换一页时，选择在最近一段时间里最久没有使用过的页面予以置换。这种算法就称为最久未使用算法（Least
Recently Used，LRU）

LRU算法是经常采用的页面置换算法，并被认为是相当好的，但是存在如何实现它的问题。LRU算法需要实际硬件的支持。其问题是怎么确定最后使用时间的顺序，对此有两种可行的办法：\
   
1.计数器。最简单的情况是使每个页表项对应一个使用时间字段，并给CPU增加一个逻辑时钟或计数器。每次存储访问，该时钟都加1。每当访问一个页面时，时钟寄存器的内容就被复制到相应页表项的使用时间字段中。这样我们就可以始终保留着每个页面最后访问的“时间”。在置换页面时，选择该时间值最小的页面。这样做，不仅要查页表，而且当页表改变时（因CPU调度）要维护这个页表中的时间，还要考虑到时钟值溢出的问题。\
   
2.栈。用一个栈保留页号。每当访问一个页面时，就把它从栈中取出放在栈顶上。这样一来，栈顶总是放有目前使用最多的页，而栈底放着目前最少使用的页。由于要从栈的中间移走一项，所以要用具有头尾指针的双向链连起来。在最坏的情况下，移走一页并把它放在栈顶上需要改动6个指针。每次修改都要有开销，但需要置换哪个页面却可直接得到，用不着查找，因为尾指针指向栈底，其中有被置换页。\
**10.6.5 时钟(CLOCK)置换算法**

简单的CLOCK算法是给每一帧关联一个附加位，称为使用位。当某一页首次装入主存时，该帧的使用位设置为1;当该页随后再被访问到时，它的使用位也被置为1。对于页替换算法，用于替换的候选帧集合看做一个循环缓冲区，并且有一个指针与之相关联。当某一页被替换时，该指针被设置成指向缓冲区中的下一帧。当需要替换一页时，操作系统扫描缓冲区，以查找使用位被置为0的一帧。每当遇到一个使用位为1的帧时，操作系统就将该位重新置为0；如果在这个过程开始时，缓冲区中所有帧的使用位均为0，则选择遇到的第一个帧替换；如果所有帧的使用位均为1,则指针在缓冲区中完整地循环一周，把所有使用位都置为0，并且停留在最初的位置上，替换该帧中的页。由于该算法循环地检查各页面的情况，故称为CLOCK算法，又称为最近未用(Not
Recently Used, NRU)算法。\
\
CLOCK算法的性能比较接近LRU，而通过增加使用的位数目，可以使得CLOCK算法更加高效。在使用位的基础上再增加一个修改位，则得到改进型的CLOCK置换算法。这样，每一帧都处于以下四种情况之一：

1.  最近未被访问，也未被修改(u=0, m=0)。

2.  最近被访问，但未被修改(u=1, m=0)。

3.  最近未被访问，但被修改(u=0, m=1)。

4.  最近被访问，被修改(u=1, m=1)。

算法执行如下操作步骤：

1.  从指针的当前位置开始，扫描帧缓冲区。在这次扫描过程中，对使用位不做任何修改。选择遇到的第一个帧(u=0,
    m=0)用于替换。

2.  如果第1)步失败，则重新扫描，查找(u=0,
    m=1)的帧。选择遇到的第一个这样的帧用于替换。在这个扫描过程中，对每个跳过的帧，把它的使用位设置成0。

3.  如果第2)步失败，指针将回到它的最初位置，并且集合中所有帧的使用位均为0。重复第1步，并且如果有必要，重复第2步。这样将可以找到供替换的帧。

[]{#_Toc22978 .anchor}**10.7 IO种类 IO的原理**

[]{#_Toc13441 .anchor}1. IO种类

计算机系统中的I/O设备按使用特性可分为以下类型：\
\
1)
人机交互类外部设备：用于同计算机用户之间交互的设备，如打印机、显示器、鼠标、键盘等。这类设备数据交换速度相对较慢，通常是以字节为单位进行数据交换。\
\
2)
存储设备：用于存储程序和数据的设备，如磁盘、磁带、光盘等。这类设备用于数据交换，速度较快，通常以多字节组成的块为单位进行数据交换。\
\
3)
网络通信设备：用于与远程设备通信的设备，如各种网络接口、调制解调器等。其速度介于前两类设备之间。网络通信设备在使用和管理上与前两类设备也有很大不同。\
\
除了上面最常见的分类方法，I/O设备还可以按以下方法分类：\
\
1) 按传输速率分类：

-   低速设备：传输速率仅为每秒几个到数百个字节的一类设备，如键盘、鼠标等。

-   中速设备：传输速率在每秒数千个字节至数万个字节的一类设备，如行式打印机、
    激光打印机等。

-   高速设备：传输速率在数百个千字节至千兆字节的一类设备，如磁带机、磁盘机、
    光盘机等。

2\) 按信息交换的单位分类：

-   块设备：由于信息的存取总是以数据块为单位，所以存储信息的设备称为块设备。它属于有结构设备，如磁盘等。磁盘设备的基本特征是传输速率较高，以及可寻址，即对它可随机地读/写任一块。

-   字符设备：用于数据输入/输出的设备为字符设备，因为其传输的基本单位是字符。它属于无结构类型，如交互式终端机、打印机等。它们的基本特征是传输速率低、不可寻址，并且在输入/输出时常釆用中断驱动方式。

[]{#_Toc14771 .anchor}2.设备I/0 输入输出控制方式

**程序直接控制方式**

计算机从外部设备读取数据到存储器，每次读一个字的数据。对读入的每个字，CPU需要对外设状态进行循环检查，直到确定该字已经在I/O控制器的数据寄存器中。

**中断驱动方式、**

中断驱动方式的思想是，允许I/O设备主动打断CPU的运行并请求服务，从而“解放”CPU，使得其向I/O控制器发送读命令后可以继续做其他有用的工作。

**DMA方式**

在中断驱动方式中，I/O设备与内存之间的数据交换必须要经过CPU中的寄存器，所以速度还是受限，而DMA（直接存储器存取）方式的基本思想是在I/O设备和内存之间开辟直接的数据交换通路，彻底“解放”
CPU。

***通道控制方式***

I/O通道是指专门负责输入/输出的处理机。I/O通道方式是DMA方式的发展，它可以进一步减少CPU的干预，即把对一个数据块的读（或写）为单位的干预，减少为对一组数据块的读（或写）及有关的控制和管理为单位的干预。

I/O通道与DMA方式的区别是：DMA方式需要CPU来控制传输的数据块大小、传输的内存位置，而通道方式中这些信息是由通道控制的。另外，每个DMA控制器对应一台设备与内存传递数据，而一个通道可以控制多台设备与内存的数据交换。

[]{#_Toc24063 .anchor}**10.8 进程打开同一个文件
那么这两个进程得到的文件描述符（fd）相同**

整个系统表包含进程相关信息，如文件在磁盘的位置、访问日期和大小。一个进程打开一个文件，系统打开文件表就会为打开的文件增加相应的条目。当另一个进程执行open时，只不过是在其进程打开表中增加一个条目，并指向整个系统表的相应条目。通常，系统打开文件表的每个文件时，还用一个文件打开计数器(Open
Count)，以记录多少进程打开了该文件。每个关闭操作close则使count递减，当打开计数器为0时，表示该文件不再被使用。系统将回收分配给该文件的内存空间等资源，若文件被修改过，则将文件写回外存，并将系统打开文件表中相应条目删除，最后释放文件的文件控制块(File
Control Block, FCB)。

所以文件描述符不同，count++，不同的count不同

[]{#_Toc14564 .anchor}**10.9 select epoll **

**select原理概述**

调用select时，会发生以下事情：

1.  从用户空间拷贝fd\_set到内核空间；

2.  注册回调函数\_\_pollwait；

3.  遍历所有fd，对全部指定设备做一次poll（这里的poll是一个文件操作，它有两个参数，一个是文件fd本身，一个是当设备尚未就绪时调用的回调函数\_\_pollwait，这个函数把设备自己特有的等待队列传给内核，让内核把当前的进程挂载到其中）；

4.  当设备就绪时，设备就会唤醒在自己特有等待队列中的【所有】节点，于是当前进程就获取到了完成的信号。poll文件操作返回的是一组标准的掩码，其中的各个位指示当前的不同的就绪状态（全0为没有任何事件触发），根据mask可对fd\_set赋值；

5.  如果所有设备返回的掩码都没有显示任何的事件触发，就去掉回调函数的函数指针，进入有限时的睡眠状态，再恢复和不断做poll，再作有限时的睡眠，直到其中一个设备有事件触发为止。

6.  只要有事件触发，系统调用返回，将fd\_set从内核空间拷贝到用户空间，回到用户态，用户就可以对相关的fd作进一步的读或者写操作了。

[]{#t1 .anchor}**epoll原理概述**

调用**epoll\_create**时，做了以下事情：

1.  内核帮我们在epoll文件系统里建了个file结点；

2.  在内核cache里建了个红黑树用于存储以后epoll\_ctl传来的socket；

3.  建立一个list链表，用于存储准备就绪的事件。

调用**epoll\_ctl**时，做了以下事情：

1.  把socket放到epoll文件系统里file对象对应的红黑树上；

2.  给内核中断处理程序注册一个回调函数，告诉内核，如果这个句柄的中断到了，就把它放到准备就绪list链表里。

调用**epoll\_wait**时，做了以下事情：

观察list链表里有没有数据。有数据就返回，没有数据就sleep，等到timeout时间到后即使链表没数据也返回。而且，通常情况下即使我们要监控百万计的句柄，大多一次也只返回很少量的准备就绪句柄而已，所以，epoll\_wait仅需要从内核态copy少量的句柄到用户态而已。

**对比**

select缺点:

1.  最大并发数限制：使用32个整数的32位，即32\*32=1024来标识fd，虽然可修改，但是有以下第二点的瓶颈；

2.  效率低：每次都会线性扫描整个fd\_set，集合越大速度越慢；

3.  内核/用户空间内存拷贝问题。

epoll的提升：

1.  本身没有最大并发连接的限制，仅受系统中进程能打开的最大文件数目限制；

2.  效率提升：只有活跃的socket才会主动的去调用callback函数；

3.  省去不必要的内存拷贝：epoll通过内核与用户空间mmap同一块内存实现。

①了解内存管理页面置换算法（LRU，Java中如何实现（LinkedHashMap））

④了解死锁与饥饿区别

⑥了解如何预防死锁（银行家算法、破坏条件等等）

⑦实现阻塞队列

⑧生产者消费者模型实现

32位系统的最大寻址空间？ 2的32次方 4GB

不同进程打开了同一个文件，那么这两个进程得到的文件描述符（fd）相同吗？

操作系统如何实现输出

三级缓存原理

内存管理： 固定分区 动态分区  段 页  都讲讲 

32位系统的内存寻址空间多大,
具体分为哪几种形态?库函数和系统调用有什么区别?

操作系统内一个进程的内存分段以及对应的作用

[]{#_Toc26248 .anchor}**10.10 物理地址 虚拟地址 逻辑地址**

物理地址(空间)

   
用于内存芯片级内存单元寻址。它们与从微处理器的地址引脚按发送到内存总线上的电信号相对应。物理地址由32位或64位无符号整数表示

虚拟地址：就是在分段 分页的 基础上，比如说将地址分为32位，

![1536988271230](media/image327.jpeg){width="5.763194444444444in"
height="7.684722222222222in"}

如图
虚拟地址就是页号加上偏移量这种的表示方法，页号与偏移量结合去找到页表中在物理内存中对应的页。

**逻辑地址（Logical Address）：**\
包含在机器语言指令中用来指定一个操作数或一条指令的地址，每个逻辑地址都由一个段和偏移量组成，偏移量指明了从段开始的地方到实际地址之间的距离。

十一 Linux命令
==============

![](media/image328.png){width="5.760416666666667in"
height="2.1430555555555557in"}

![](media/image329.png){width="5.764583333333333in"
height="3.011111111111111in"}

![](media/image330.png){width="5.763888888888889in"
height="2.8958333333333335in"}

[]{#_Toc26554 .anchor}10.1 Vim

\(1) 打开与退出\
        vi file：打开文件file\
        :q ：退出vi编辑器\
        :wq：保存缓冲区的修改并退出编辑器\
        :q!：不保存直接退出\
        :w 保存缓冲区内容至默认的文件\
        :w file 保存缓冲区内容至file文件\
(2) 插入文本\
        a : 在当前光标的右边插入文本\
        A : 在当前光标行的末尾插入文本\
        i : 在当前光标的左边插入文本\
        I : 在当前光标所在行的开始处插入文本\
        o: 在当前行在下面新建一行\
        O:在当前行的上面新建一行\
        R:替换当前光标位置以及以后的若干文本\
        J:连接光标所在行和下一行\
(3) 删除文本\
        x:  删除一个字符\
        dd: 删除一行\
        ndd: 删除n行\
        u: 撤销上一次操作\
        U: 撤销对当前行的所有操作\
(4) 搜索\
        /word 从前向后搜索第一个出现的word\
        ？word 从后向前搜索第一个出现的word

\(5) 设置行号\
        :set nu  在屏幕上显示行号\
        :set nonu 取消行号

![](media/image331.png){width="5.761805555555555in"
height="2.301388888888889in"}

[]{#_Toc9687 .anchor}10.2 linux如何查看端口被哪个进程占用？

lsof -i:端口号

![](media/image332.png){width="5.761805555555555in"
height="0.49166666666666664in"}

*https://www.cnblogs.com/bonelee/p/7735479.html*

[]{#_Toc5762 .anchor}10.3 查看进程打开了哪些文件

lsof -p pid

[]{#_Toc28012 .anchor}**10.4 top**

![](media/image333.png){width="4.916666666666667in"
height="1.1833333333333333in"}

　　PID：进程的ID\
　　USER：进程所有者\
　　PR：进程的优先级别，越小越优先被执行\
　　NInice：值\
　　VIRT：进程占用的虚拟内存\
　　RES：进程占用的物理内存\
　　SHR：进程使用的共享内存\
　　S：进程的状态。S表示休眠，R表示正在运行，Z表示僵死状态，N表示该进程优先值为负数\
　　%CPU：进程占用CPU的使用率\
　　%MEM：进程使用的物理内存和总内存的百分比\
　　TIME+：该进程启动后占用的总的CPU时间，即占用CPU使用时间的累加值。\
　　COMMAND：进程启动命令名称

top -p 进程id 查看具体的进程的内存占用

Top -u 用户名 查看用户的进程内存

输入top后出来数据了 然后输入M按照内存排序，输入P按照CPU排序
输入T按照占用CPU的时间排序

[]{#_Toc12316 .anchor}10.5 查看cpu核的个数主频

cat /proc/cpuinfo

[]{#_Toc2861 .anchor}10.6 Linux如何创建守护进程

（1）创建子进程，父进程退出。 

经过这步以后，子进程就会成为孤儿进程（父进程先于子进程退出，
此时的子进程，成为孤儿进程，会被init进程收养）。使用fork（）函数，如果返回值大于0，表示为父进程，exit（0），父进程退出，子进程继续。 

（2）在子进程中创建新会话，使当前进程成为新会话组的组长。 

使用setsid()函数，如果当前进程不是进程组的组长，则为当前进程创建一个新的会话期，使当前进程成为这个会话组的首进程，成为这个进程组的组长。 

（3）改变当前目录为根目录。 

由于守护进程在后台运行，开始于系统开启，终止于系统关闭，所以要将其目录改为系统的根目录下。进程在执行时，其文件系统不能被卸下。 

（4）重新设置文件权限掩码。 

进程从父进程那里继承了文件创建掩码，所以可能会修改守护进程存取权限位，所以要将文件创建掩码清除，umask（0）； 

（5）关闭文件描述符。 

子进程从父进程那里继承了打开文件描述符。所以使用close即可关闭。 

[]{#_Toc25671 .anchor}10.7 Linux 管道机制原理

实际上，管道是一个固定大小的缓冲区。在Linux中，该缓冲区的大小为1页，即4K字节，使得它的大小不象文件那样不加检验地增长。使用单个固定缓冲区也会带来问题，比如在写管道时可能变满，当这种情况发生时，随后对管道的write()调用将默认地被阻塞，等待某些数据被读取，以便腾出足够的空间供write()调用写。

·    读取进程也可能工作得比写进程快。当所有当前进程数据已被读取时，管道变空。当这种情况发生时，一个随后的read()调用将默认地被阻塞，等待某些数据被写入，这解决了read()调用返回文件结束的问题。

[]{#_Toc24324 .anchor}10.8 查看进程下的线程

*https://www.cnblogs.com/EasonJim/p/8098217.html*

top -H -p 进程ID

![](media/image334.png){width="5.7652777777777775in" height="1.14375in"}

[]{#_Toc19935 .anchor}**10.9 linux锁**

1.互斥锁

互斥锁只能有对一个线程使用，就是用来互斥的。

以下是互斥锁的基本操作

![](media/image335.png){width="4.45in" height="3.65in"}

1.  自旋锁

> 自旋锁上锁后让等待线程进行忙等待而不是睡眠阻塞，而信号量是让等待线程睡眠阻塞。自旋锁的忙等待浪费了处理器的时间，但时间通常很短，在1毫秒以下。

[]{#_Toc20621 .anchor}10.10 查看行数指令（比如第100行到第150行 top IP）

1.要显示一百行到一百五十行的内容怎么输入命令

> sed -n "100,150p" +文件名
> sed命令是一个选取命令，它后面单引号括起来的100,150就表示100行到150行的意思，100,150后面的英文字母p是print显示的意思。

2.  有一个文件ip.txt，每行一条ip记录，共若干行，下面哪个命令可以实现“统计出现次数最多的前3个ip及其次数”？

sort ip.txt | uniq -c | sort -rn | head -n 3

首先sort进行排序，将重复的行都排在了一起，然后使用uniq
-c将重复的行的次数放在了行首，在用sort
-rn进行反向和纯文本排序，这样就按照重复次数从高到低进行了排列，最后利用head
-n 3 输出行首的三行。

2.  Linux下 给定一个文件，里面存放的是IP地址，统计各个IP地址出现的次数

> sort ip.txt | uniq -c | sort -rn

5.统计文件中出现最多的前10个单词

![](media/image336.png){width="5.761805555555555in"
height="2.4229166666666666in"}

[]{#_Toc21878 .anchor}**10.11 linux进程调度**

1、 进程调度的作用

,进程调度就是对进程进行调度,即负责选择下一个要运行的进程.通过合理的调度,系统资源才能最大限度地发挥作用,多进程才会有并发执行的效果.最终要完成的目标就是为了最大限度的利用处理器时间.即,只要有可以执行的进程,那么就总会有进程正在执行.当进程数大于处理器个数时,某一时刻总会有一些进程进程不能执行.这些进程等待运行.在这些等待运行的进程中选择一个合适的来执行,是调度程序所需完成的基本工作.

2、调度策略

先给一张直观图

【1】考虑到进程类型时:I/O消耗型进程 pk 处理器消耗型进程.\
I/O消耗型进程:指进程大部分时间用来提交I/O请求或者是等待I/O请求.处理器消耗型进程:与I/O消耗型相反,此类进程把时间大多用在执行代码上.此时调度策略通常要在两个矛盾的目标中寻找平衡:进程响应时间短(优先I/O消耗型进程)和最大系统利用率(优先处理器消耗型进程).linux为了保证交互式应用,所以对进程的响应做了优化,即更倾向于优先调度I/O消耗型进程.\
【2】考虑到进程优先级时\
调度算法中最基本的一类就是基于优先级的调度.调度程序总是选择时间片未用尽而且优先级最高的进程运行.\
linux实现了一种基于动态优先级的调度方法.即:一开始,先设置基本的优先级,然后它允许调度程序根据需要加,减优先级.\
eg:如果一个进程在I/O等待上消耗的时间多于运行时间,则明显属于I/O消耗型进程,那么根据1中的考虑,应该动态提高其优先级.\
linux提供了两组独立的优先级范围:\
1)nice值:范围从-20到+19.默认值是0,值越小,优先级越高.nice值也用来决定分配给进程的时间片的长短.\
2)实时优先级:范围为0到99.注意,任何实时进程的优先级都高于普通的进程.\
【3】考虑到进程时间片时\
时间片是一个数值,它表明进程在被抢占前所能持续运行的时间.调度策略必须规定一个默认的时间片.时间片过长,则会影响系统的交互性.时间片过短,则会明显增大因进程频繁切换所耗费的时间.调度程度提供较长的默认时间片给交互式程序.此外,linux调度程序还能根据进程的优先级动态调整分配给它的时间片,从而保证了优先级高的进程,执行的频率高,执行时间长.当一个进程的时间片耗尽时,则认为进程到期了,此时不能在运行.除非所有进程都耗尽了他们的时间片,此时系统会给所有进程重新

**10.12 零拷贝技术**

![](media/image337.png){width="5.7652777777777775in"
height="4.042361111111111in"}

[]{#_Toc28623 .anchor}**10.14 系统调用与库函数的区别**

![](media/image338.png){width="5.266666666666667in"
height="2.4833333333333334in"}

[]{#_Toc30130 .anchor}**10.15 free**

我们按照图中来一细细研读(数字编号和图对应)\
\
1，total：物理内存实际总量\
2，used：这块千万注意，这里可不是实际已经使用了的内存哦，这里是总计分配给缓存（包含buffers
与cache ）使用的数量，但其中可能部分缓存并未实际使用。\
3，free：未被分配的内存\
4，shared：共享内存\
5，buffers：系统分配的，但未被使用的buffer剩余量。注意这不是总量，而是未分配的量\
6，cached：系统分配的，但未被使用的cache 剩余量。buffer 与cache
的区别见后面。\
\
7，buffers/cache
used：这个是buffers和cache的使用量，也就是实际内存的使用量，这个非常重要了，这里才是内存的实际使用量哦\
\
8， buffers/cache free：未被使用的buffers 与cache
和未被分配的内存之和，这就是系统当前实际可用内存。千万注意，这里是
三者之和，也就是第一排的
free+buffers+cached，可不仅仅是未被使用的buffers
与cache的和哦，还要加上free(未分配的和)\
\
9，swap，这个我想大家都理解，交换分区总量，使用量，剩余量\
\
我想我说得很清晰了

 

 

[]{#_Toc13490 .anchor} 10.16 cache 和 buffer的区别：

**cache在cpu和内存之间，它的速度比内存快，但是造价高**

缓冲区**buffer**主要存在于RAM中，作为CPU暂时存储数据的区域，例如，**当计算机和其他设备具有不同的速度时**, **buffer**存储着缓冲的数据，
这样计算机就可以完成其他任务了

Cache：高速缓存，是位于CPU与主内存间的一种容量较小但速度很高的存储器。由于CPU的速度远高于主内存，CPU直接从内存中存取数据要等待一定时间周期，Cache中保存着CPU刚用过或循环使用的一部分数据，当CPU再次使用该部分数据时可从Cache中直接调用，这样就减少了CPU的等待时间，提高了系统的效率。Cache又分为一级Cache（L1
Cache）和二级Cache（L2 Cache），L1 Cache集成在CPU内部，L2
Cache早期一般是焊在主板上，现在也都集成在CPU内部，常见的容量有256KB或512KB
L2 Cache。\
   
Buffer：缓冲区，一个用于存储速度不同步的设备或优先级不同的设备之间传输数据的区域。通过缓冲区，可以使进程之间的相互等待变少，从而使从速度慢的设备读入数据时，速度快的设备的操作进程不发生间断。\
    Free中的buffer和cache：（它们都是占用内存）：\
    buffer : 作为buffer cache的内存，是块设备的读写缓冲区\
    cache: 作为page cache的内存， 文件系统的cache\
    如果 cache
的值很大，说明cache住的文件数很多。如果频繁访问到的文件都能被cache住，那么磁盘的读IO
必会非常小。 

[]{#_Toc22376 .anchor}**10.13 其它的小问题**

1.查看所有端口的占用情况netstat，

2.怎么查看一个服务器是否正常运作ps aux

**3.创建用户命令  adduser 用户名**\
4.Linux：fork和wait，有什么作用 fork用来创建子进程 wait
如果子进程状态已经改变，那么wait调用会立即返回。否则调用wait的进程将会阻塞直到有子进程改变状态或者有信号来打断（这里所指的状态的改变包括：子进程终止；子进程被一个信号终止来；子进程被一个信号恢复。）这个调用。
wait是父进程用来等待来获取子进程的状态信息，获取到以后清除掉子进程。

5.Linux 线程 其实在Linux
中，新建的线程并不是在原先的进程中，而是系统通过一个系统调用clone()
。该系统copy
了一个和原先进程完全一样的进程，并在这个进程中执行线程函数。不过这个copy
过程和fork 不一样。copy
后的进程和原先的进程共享了所有的变量，运行环境。这样，原先进程中的变量变动在copy
后的进程中便能体现出来。

6.内存中buffer和swap，cache的区别

Swap:读取数据到内存，内存不够用，这时候把部分内存中的数据写入到磁盘上，这部分磁盘空间就是swap

Buffer：buffer（缓冲）是为了提高内存和硬盘（或其他I/O设备）之间的数据交换的速度而设计的。 当程序要写入磁盘时候，不必等写入磁盘这个操作结束再去执行其他的，可以直接写入到buffer

Cache:cache（缓存）是为了提高cpu和内存之间的数据交换速度而设计的.
从磁盘读取的先存入到cacahe，以便下次再次访问时候使用。

7.linux 查看进程的运行堆栈信息命令-gstack gstack 进程id

8.linux查看进程消耗的资源

*https://www.cnblogs.com/sparkbj/p/6148817.html*

可以使用一下命令查使用内存最多的10个进程

**查看占用cpu最高的进程**

*ps* aux|head -1;ps aux|grep -v PID|sort -rn -k +3|head

或者top （然后按下M，注意这里是大写）

**查看占用内存最高的进程**

ps aux|head -1;ps aux|grep -v PID|sort -rn -k +4|head

或者top （然后按下P，注意这里是大写）

9.smp SMP的全称是"对称多处理"（Symmetrical
Multi-Processing）技术，是指在一个计算机上汇集了一组处理器(多CPU),各CPU之间共享内存子系统以及总线结构。

进程文件里有哪些信息，，

sed和awk的区别

Linux命令（有一个文件被锁住，如何查看锁住它的线程，,)

linux如何查找文件

**\
**

11. []{#_Toc6933 .anchor}**安全加密**

***http://www.ruanyifeng.com/blog/2011/08/what\_is\_a\_digital\_signature.html***

[]{#_Toc11219 .anchor}**11.1数字签名**

![](media/image339.png){width="5.763194444444444in"
height="1.9555555555555555in"}

2.验证过程

发送者：将报文通过hash算法生成摘要，用私钥加密生成签名。 \
接收者：使用公钥解密数字签名，得到摘要A，再对报文进行Hash算法得到摘要B，比较A和B，一致则表示没有被修改。

[]{#_Toc2230 .anchor}11.2 数字证书

数字证书则是由证书认证机构（CA, Certificate
Authority）对证书申请者真实身份验证之后，用CA的根证书对申请人的一些基本信息以及申请人的公钥进行签名（相当于加盖发证书机构的公章）后形成的一个数字文件。 

![](media/image340.png){width="1.6770833333333333in"
height="1.9375in"}左图是CA证书![](media/image341.png){width="2.2291666666666665in"
height="3.7395833333333335in"}

数字证书验证过程：CA机构的公钥已经是在浏览器发布前提前嵌入到浏览器内部了，所以CA的公钥是真实可靠的（如果CA机构被黑客攻陷，那么也可能是不可靠的），然后服务器发送自己的公钥给CA（用CA的公钥进行加密），CA对服务器的发来的内容解密得到服务器的公钥，然后CA对服务器的公钥进行颁发数字证书（就是数字签名），发给服务器，服务器收到以后，将数字证书，公开密钥发送给客户端，客户端用CA的公开密钥验证得到服务器的公开密钥，然后这样客户端就得到了真正可靠的服务器的公开密钥。

[]{#_Toc7522 .anchor}11.3 公私钥

公钥（Public Key）与私钥（Private
Key）是通过一种算法得到的一个密钥对（即一个公钥和一个私钥），公钥是密钥对中公开的部分，私钥则是非公开的部分。

使用这个密钥对的时候，如果用其中一个密钥加密一段数据，必须用另一个密钥解密。比如用公钥加密数据就必须用私钥解密，如果用私钥加密也必须用公钥解密，否则解密将不会成功。

[]{#_Toc4944 .anchor}11.4 非对称加密 RSA

非对称加密算法需要两个密钥：公开密钥（publickey）和私有密钥（privatekey）。公开密钥与私有密钥是一对，如果用公开密钥对数据进行加密，只有用对应的私有密钥才能解密；如果用私有密钥对数据进行加密，那么只有用对应的公开密钥才能解密。因为加密和解密使用的是两个不同的密钥，所以这种算法叫作非对称加密算法。

RSA：

***RSA算法的步骤主要有以下几个步骤：*** \
    1、选择 p、q两个超级大的质数 ，都是1024位，

   2、令n = p \* q。取 φ(n) =(p-1) \* (q-1)。
计算与n互质的整数的个数。 \
    3、取 e ∈ 1 &lt; e &lt; φ(n) ，( n , e
)作为公钥对，正式环境中取65537。可以打开任意一个被认证过的https证书，都可以看到。 \
    4、令 ed mod φ(n) = 1，计算d，( n , d ) 作为私钥对。
计算d可以利用扩展欧几里的算法进行计算 \
    5、销毁 p、q。密文 = 明文 \^ e mod n ， 明文 = 密文 \^ d mod
n。利用蒙哥马利方法进行计算，也叫反复平方法，非常简单、

其中（n,e）是公钥 （n,d）是私钥

[]{#_Toc13280 .anchor}11.5 对称密钥 DES

DES：**DES算法是一种分组加密机制，将明文分成N个组，然后对各个组进行加密，形成各自的密文，最后把所有的分组密文进行合并，形成最终的密文**。

对称密钥就是加密使用的密钥是一致的。

[]{#_Toc12433 .anchor}11.6 DH加密算法

Diffie-Hellman算法概述：

（1）Alice与Bob确定两个大素数n和g，这两个数不用保密

（2）Alice选择另一个大随机数x，并计算A如下：A=g\^x mod n

（3）Alice将A发给Bob

（4）Bob选择另一个大随机数y，并计算B如下：B=g\^y mod n

（5）Bob将B发给Alice

（6）计算Alice的秘密密钥K1如下：K1=B\^x mod n

（7）计算Bob的秘密密钥K2如下：K2=A\^y mod n
K1=K2，因此Alice和Bob可以用其进行加解密

[]{#_Toc12047 .anchor}11.7 SHA MD5

MD5：**MD5消息摘要算法**（英语：MD5 Message-Digest
Algorithm），一种被广泛使用的密码散列函数，可以产生出一个128位（16字节）的散列值（hash
value），用于确保信息传输完整一致。

SHA：**安全散列算法**（英语：Secure Hash
Algorithm，缩写为SHA）是一个密码散列函数家族，是FIPS所认证的安全散列算法。能计算出一个数字消息所对应到的，长度固定的字符串（又称消息摘要）的算法。且若输入的消息不同，它们对应到不同字符串的机率很高。

11. []{#_Toc26327 .anchor}**代码**

[]{#_Toc13035 .anchor}**12.1 读写文件(BufferedReader)**

import java.io.\*;\
public class ReadWriteTxt {\
public static void main(String args\[\]) {\
try { // 防止文件建立或读取失败，用catch捕捉错误并打印，也可以throw\
/\* 读入TXT文件 \*/\
String pathname = "input.txt"; //
绝对路径或相对路径都可以，写入文件时演示相对路径\
File filename = new File(pathname); // 要读取以上路径的input.txt文件\
InputStreamReader reader = new InputStreamReader(\
new FileInputStream(filename)); // 建立一个输入流对象reader\
BufferedReader br = new BufferedReader(reader); //
建立一个对象，它把文件内容转成计算机能读懂的语言\
String line;\
//网友推荐更加简洁的写法\
while ((line = br.readLine()) != null) {\
// 一次读入一行数据\
System.*out*.println(line);\
}\
} catch (Exception e) {\
e.printStackTrace();\
}\
\
try {\
/\* 写入Txt文件 \*/\
File writename = new File("output.txt"); //
相对路径，如果没有则要建立一个新的output.txt文件\
writename.createNewFile(); // 创建新文件\
BufferedWriter out = new BufferedWriter(new FileWriter(writename));\
out.write("我会写入文件啦1\\r\\n"); // \\r\\n即为换行\
out.write("我会写入文件啦2\\r\\n"); // \\r\\n即为换行\
out.flush(); // 把缓存区内容压入文件\
out.close(); // 最后记得关闭文件\
} catch (IOException e) {\
e.printStackTrace();\
}\
}\
}

[]{#_Toc3293 .anchor}**12.2 反射**

//Test01.java\
import java.lang.reflect.Field;\
import java.lang.reflect.InvocationTargetException;\
import java.lang.reflect.Method;\
//Exam.java\
class Exam{\
private String field1="私有属性";\
public String field2="公有属性";\
public void fun1(){\
System.*out*.println("fun1:这是一个public访问权限方法");\
}\
\
private void fun2(){\
System.*out*.println("fun2:这是一个private访问权限方法");\
}\
\
private void fun3(String arg){\
System.*out*.println("fun3:这是一个private访问权限且带参数的方法，参数为："+arg);\
}\
\
}\
\
public class ReflectTest {\
public static void main(String args\[\]){\
Exam e=new Exam();\
try {\
Field field1 = e.getClass().getDeclaredField("field1");\
Field field2 = e.getClass().getDeclaredField("field2");\
field1.setAccessible(true);\
System.*out*.println("field1: "+field1.get(e));\
field1.set(e,"重新设置一个field1值");\
System.*out*.println("field1: "+field1.get(e));\
System.*out*.println("field2: "+field2.get(e));\
field2.set(e,"重新设置一个field2值");\
System.*out*.println("field2: "+field2.get(e));\
} catch (NoSuchFieldException e1) {\
e1.printStackTrace();\
}catch (IllegalArgumentException e1) {\
e1.printStackTrace();\
} catch (IllegalAccessException e1) {\
e1.printStackTrace();\
}\
\
try {\
\
Method method1 = e.getClass().getDeclaredMethod("fun1");\
method1.invoke(e);\
\
Method method2 = e.getClass().getDeclaredMethod("fun2");\
method2.setAccessible(true);\
method2.invoke(e);\
\
Method method3 = e.getClass().getDeclaredMethod("fun3",String.class);\
method3.setAccessible(true);\
method3.invoke(e,"fun3的参数");\
} catch (NoSuchMethodException e1) {\
// *TODO Auto-generated catch block\
*e1.printStackTrace();\
} catch (SecurityException e1) {\
// *TODO Auto-generated catch block\
*e1.printStackTrace();\
}catch (IllegalAccessException e1) {\
// *TODO Auto-generated catch block\
*e1.printStackTrace();\
} catch (IllegalArgumentException e1) {\
// *TODO Auto-generated catch block\
*e1.printStackTrace();\
} catch (InvocationTargetException e1) {\
// *TODO Auto-generated catch block\
*e1.printStackTrace();\
}\
}\
\
}

**13.3 快排**

public class Solution {\
*/\*\*\
\* **@param** A: an integer array\
\* **@return:** nothing\
\*/\
*public void sortIntegers2(int\[\] A) {\
// write your code here\
quicksort(A,0,A.length-1);\
}\
public void quicksort(int\[\] A,int begin,int end)\
{\
int i = begin;\
int j = end;\
if(i &gt;= j)\
{\
return;\
}\
int keng = A\[i\];\
while(i &lt; j)\
{\
while(i&lt;j && A\[j\] &gt; keng)\
{\
j--;\
}\
if(i&lt;j && A\[j\] &lt;= keng)\
{\
A\[i\] = A\[j\];\
i++;\
}\
while(i&lt;j && A\[i\] &lt; keng)\
{\
i++;\
}\
if(i&lt;j && A\[i\] &gt;= keng)\
{\
A\[j\] = A\[i\];\
j--;\
}\
}\
A\[i\] = keng;\
quicksort(A,begin,i-1);\
quicksort(A,i+1,end);\
}\
}

[]{#_Toc15149 .anchor}**12.3 LRU**

11. 面经
    ====

    13.1 作业帮面经

    一面挂

<!-- -->

1.  循环有序数组找一个数

import java.util.\*;\
public class Main {\
public static void main(String\[\] arg) {\
int \[\] temp = {3,2};\
System.*out*.println(*find*(temp,2));\
}\
public static int find(int \[\] array,int n)\
{\
if(array.length == 1)\
{\
if(array\[0\] == n)\
return 0;\
return -1;\
}\
int start = 0;\
int end = array.length-1;\
if(start &gt;= end)\
return -1;\
int mid = (start + end) / 2;\
while(start &lt;= end)\
{\
mid = (start + end) / 2;\
int flag = 0;\
if(array\[mid\] == n)\
return mid;\
if(array\[start\] == n)\
return start;\
if(array\[end\] == n)\
return end;\
if(array\[mid\] &gt; array\[start\])\
{\
if(array\[mid\] &gt; n && n &gt; array\[start\])\
{\
end = mid - 1;\
}\
else\
{\
start = mid + 1;\
}\
}else {\
if(array\[mid\] &lt; n && n &lt; array\[end\])\
{\
start = mid + 1;\
}\
else\
{\
end = mid - 1;\
}\
}\
}\
return -1;\
}\
}

2.

11. 项目
    ====

    []{#_Toc12764 .anchor}**14.1. jieba分词原理**

*jieba分词的原理*

** jieba介绍：**

一、支持三种分词模式：

精确模式，试图将句子最精确地切开，适合文本分析；

全模式，把句子中所有的可以成词的词语都扫描出来,
速度非常快，但是不能解决歧义；

搜索引擎模式，在精确模式的基础上，对长词再次切分，提高召回率，适合用于搜索引擎分词。

二、jieba自带了一个叫做dict.txt的词典, 里面有2万多条词,
包含了词条出现的次数(这个次数是于作者自己基于人民日报语料等资源训练得出来的)和词性.
这个第一条的trie树结构的词图扫描, 说的就是把这2万多条词语,
放到一个trie树中, 而trie树是有名的前缀树,
也就是说一个词语的前面几个字一样, 就表示他们具有相同的前缀,
就可以使用trie树来存储, 具有查找速度快的优势。

三、jieba分词应该属于概率语言模型分词

     
 概率语言模型分词的任务是：在全切分所得的所有结果中求某个切分方案S，使得P(S)最大。

jieba用到的算法：

一、基于Trie树结构实现高效的词图扫描，生成句子中汉字所有可能成词情况所构成的有向无环图（DAG)

       1. 根据dict.txt生成trie树。字典在生成trie树的同时,
也把每个词的出现次数转换为了频率；

       2. 对待分词句子, 根据dict.txt生成的trie树, 生成DAG,
实际上通俗的说, 就是对待分词句子, 根据给定的词典进行查词典操作,
生成几种可能的句子切分。jieba的作者在DAG中记录的是句子中某个词的开始位 
           置, 从0到n-1(n为句子的长度), 每个开始位置作为字典的键,
value是个list, 其中保存了可能的词语的结束位置(通过查字典得到词,
开始位置+词语的长度得到结束位置)注：所以可以联想到，jieba支持全模       
     式分词，能把句子中所有的可以成词的词语都扫描出来

       例如:{0:\[1,2,3\]} 这样一个简单的DAG, 就是表示0位置开始,
在1,2,3位置都是词, 就是说0\~1, 0\~2,0\~3这三个起始位置之间的字符,
在dict.txt中是词语.可看示例切分词图。

二、采用了动态规划查找最大概率路径, 找出基于词频的最大切分组合

     
 1.查找待分词句子中已经切分好的词语（我觉得这里应该是全模式下的分词list）,
对该词语查找该词语出现的频率(次数/总数), 如果没有该词(既然是基于词典查找进行的分词,
应该是有的), 就把词典中出现频率最小的那个词语的频率作为该词的频率,
也就是说P(某词语)=FREQ.get(‘某词语’,min\_freq)

       2.根据动态规划查找最大概率路径的方法,
对句子从右往左反向计算最大概率(一些教科书上可能是从左往右,
这里反向是因为汉语句子的重心经常落在后面, 就是落在右边,
因为通常情况下形容词太多, 后面的才是主干, 因此, 从右往左计算,
正确率要高于从左往右计算, 这个类似于逆向最大匹配), P(NodeN)=1.0,
P(NodeN-1)=P(NodeN)\*Max(P(倒数第一个词))…依次类推,
最后得到最大概率路径, 得到最大概率的切分组合.

Python
======

Python如何写爬虫

python全局锁

python爬虫分为哪几种，分别是

你爬虫那个项目中是怎么解决反爬虫问题的？

Git
===

git常用命令、有哪些目录或区域
git是怎么管理代码的，提交错误的话，怎么撤销

介绍数据仓库

计算机磁盘
==========

为什么磁盘I/O阻塞代价很大

SSD没有磁头，为什么I/O代价还很高

Socket
======

其它
====

项目中权限管理如何实现的

非对称加密

SHA，MD5

如何设计一个秒杀系统(看来你对限流不是很熟悉啊)

程序出现问题，如何定位（哪一行代码）

20亿QQ号的插入与查找最小存储开销实现方案（提示：位图）

读过JDK源码吗

提升访问网页效率的方法(缓存:客户端缓存，cdn缓存，服务器缓存，多线程，负载均衡之类)

分布式服务中,某个服务速度很慢,如何排查(发散性较强,从计算机网络,到多线程到数据库结构都能说说)

**怎么定位查找 **

①了解分布式缓存、Zookeeper、阿里dubbo、Nginx等

②了解NoSQL（Redis等）

③了解Hadoop大数据相关知识

简述Select poll和epoll，还有direct io和buffer io区别（一脸蒙蔽…）

C 的拷贝构造函数，深拷贝和浅拷

 分布式架构中，怎么保证数据的一致性

1.pubilc A｛ public void test(){} } 

public B extends A{ protected void test(){} }

这样有问题吗？为什么？ 

2.public A｛ public long test(){} } 

public B extends A{ public int test(){} }

都不行

int i=0； Integer i1=0； Integer i2=new Integer（0）；
输出i==i1；i==i2；i1==i2分别是false还是true 

分别返回true，true，false。

jdk 1.5之后 有了自动装箱和拆箱 所以 前两个是true  后两个 是不同的对象

maven冲突如何解决；

大型论坛网站难免会出现敏感评论, 如何过滤敏感评论

自我介绍：

项目：

1.  对你来说影响最大的一个项目（该面试中有关项目问题都针对该项目展开）？

2.  项目哪一部分最难攻克？如何攻克？、

个人建议：大家一定要选自己印象最深的项目回答，首先按模块，然后组成人员，最后你在项目中的角色和发挥 的作用。全程组织好语言，最好不要有停顿，面试官可以看出你对项目的熟悉程度

1.  你觉得你在项目运行过程中作为组长是否最大限度发挥了组员的优势？具体事例？

2.  职业规划，今天想发展的工作方向

3.  项目里我遇到过的最大的困难是什么

4.  实验室的新来的研一，你会给他们什么学习上的建议，例如对于内核源码的枯燥如何克服

5.  如何协调团队中多人的工作

6.  当团队中有某人的任务没有完成的很好，如何处理

7.  平时看些什么书，技术 综合

8.  项目解决的什么问题 用到了哪些技术

9.  怎么预防bug 日志 jvm异常信息 如何找问题的根源（统计表格）

10. 你是怎么学习的，说完会让举个例子

11. 实习投了哪几个公司？为什么，原因

12. 最得意的项目是什么？为什么？(回答因为项目对实际作用大，并得到认可)

13. 最得意的项目内容，讲了会

14. 你简历上写的是最想去的部门不是我们部门，来我们部门的话对你有影响麽？

15. 你除了在学校还有哪些方式去获取知识和技术？

16. 你了解阿里文化和阿里开源吗？

17. 遇到困难解决问题的思路？

18. 我觉得最成功的一件事了，我说能说几件吗，说了我大学明白明白了自己想干什么，选择了自己喜欢的事，大学里学会了和自己相处，自己一个人的时候也不会感觉无聊，精神世界比较丰富，坚持锻炼，健身，有个很不错的身体，然后顿了顿笑着说，说，有一个对我很好的女朋友算吗？

19. 压力大的时候怎么调整？多个任务冲突了你怎么协调的？

20. 家里有几个孩子，父母对你来北京有什么看法?

21. 职业生涯规划

22. 你在什么情况下可能会离职

23. 对你影响最大的人

24. 1\. 优点3个，以及缺点2. 说说你应聘这个岗位的优势3. 说说家庭4.
    为什么想来网易，用过网易的哪些产品，对比下有什么好的地方5.
    投递了哪些公司，对第一份工作怎么看待

25. 为什么要选择互联网（楼主偏底层的）

26. 为什么来网易（看你如何夸）

27. .在校期间怎样学习

28. 经常逛的技术性网站有哪些？

29. 举出你在开发过程中遇到的原先不知道的bug,
    通过各种方式定位bug并最终成功解决的例子

30. 举出一个例子说明你的自学能力

7次面试记录，除了京东基本上也都走到了很后面的阶段。硬要说经验可能有三点：

-   **不会就不会。**我比较爽快，如果遇到的不会的甚至是不确定的，都直接说：“对不起，我答不上来”之类的。

-   **一技之长。**中间件和架构相关的实习经历，让我基本上和面试官都可以聊的很多，也可以看到，我整个过程没有多少算法题。是因为面试官和你聊完项目就知道你能做事了。其实，面试官很不愿意出算法题的（BAT那个档次除外），你能和他扯技术他当然高兴了。关键很多人只会算法（逃）。

-   **基础非常重要。**面试官只要问Java相关的基础，我都有自信让一般的面试官感觉惊讶，甚至学到新知识（之前遇到的阿里的面试官，我并没有做到，还被按在地上摩擦）。

-   **说话时面带微笑**
