# Java

Oracle JDK有部分源码是闭源的，如果确实需要可以查看OpenJDK的源码，可以在该网站获取。

http://grepcode.com/snapshot/repository.grepcode.com/java/root/jdk/openjdk/8u40-b25/

http://hg.openjdk.java.net/jdk8u/jdk8u/jdk/file/73d5bcd0585d/src
上面这个还可以查看native方法。

### JDK&JRE&JVM

JDK（Java Development Kit）是针对Java开发员的产品，是整个Java的核心，包括了Java运行环境JRE、Java工具（编译、开发工具）和Java核心类库。
Java Runtime Environment（JRE）是运行JAVA程序所必须的环境的集合，包含JVM标准实现及Java核心类库。
JVM是Java Virtual Machine（Java虚拟机）的缩写，是整个java实现跨平台的最核心的部分，能够运行以Java语言写作的软件程序。

![123.png](http://ww1.sinaimg.cn/large/007s8HJUly1gdka822vwdj30dw099414.jpg)

JDK包含JRE和Java编译、开发工具；
JRE包含JVM和Java核心类库；
运行Java仅需要JRE；而开发Java需要JDK。

### 跨平台

字节码是在虚拟机上运行的，而不是编译器。换而言之，是因为JVM能跨平台安装，所以相应JAVA字节码便可以跟着在任何平台上运行。只要JVM自身的代码能在相应平台上运行，即JVM可行，则JAVA的程序员就可以不用考虑所写的程序要在哪里运行，反正都是在虚拟机上运行，然后变成相应平台的机器语言，而这个转变并不是程序员应该关心的。
