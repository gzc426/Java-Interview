
# 一. HashMap
https://blog.csdn.net/jiary5201314/article/details/51439982
## 1. hashMap的原理
hashmap  是数组和链表的结合体，数组每个元素存的是链表的头结点 往 hashmap
里面放键值对的时候先得到 key 的 hashcode，然后重新计算 hashcode， （让 1 分布均匀因为如果分布不均匀，低位全是 0，则后来计算数组下标的时候会 冲突），然后与 length-1 按位与，计算数组出数组下标 如果该下标对应的链表为空，则直接把键值对作为链表头结点，如果不为空，则 遍历链表看是否有 key 值相同的，有就把 value 替换， 没有就把该对象最为链表的第 一个节点，原有的节点最为他的后续节点
## 2. hashcode的计算
https://www.zhihu.com/question/20733617/answer/111577937
https://blog.csdn.net/justloveyou_/article/details/62893086
Key.hashcode是key的自带的hascode函数是一个int值32位

hashmap jdk1.8 中 hashmap 重计算 hashcode 方法改动： 高 16 位异或低 16 位
>return (key == null) ? 0 : h = key.hashCode() ^ (h >>> 16);
首先确认：当 length 总是 2 的n 次方时， h & (length - 1)	等价于	hash 对length 取模 ， 但是&比%具有更高的效率；
>Jdk1.7 之前：h & (length - 1);//第三步，取模运算

![](https://github.com/gzc426/picts/blob/master/%E5%BE%AE%E4%BF%A1%E5%9B%BE%E7%89%87_20191002175517.jpg)

## 3. hashMap参数以及扩容机制
初始容量 16，达到阀值扩容，阀值等于最大容量*负载因子，扩容每次 2 倍，总是 2 的n 次方
扩容机制：
使用一个容量更大的数组来代替已有的容量小的数组，transfer()方法将原有 Entry 数组的元素拷贝到新的 Entry 数组里，Java1.重新计算每个元素在数组中的位置。Java1.8 中不是重新计算，而是用了一种更巧妙的方式。
## 4. get()方法
**整个过程都不需要加锁**
![](https://github.com/gzc426/picts/blob/master/%E5%9B%BE%E7%89%871.png)
## 5. put()方法
![](https://github.com/gzc426/picts/blob/master/%E5%9B%BE%E7%89%872.png)
这里HashMap里面用到链式数据结构的一个概念。上面我们提到过Entry类里面有一个next属性，作用是指向下一个Entry。打个比方， 第一个键值对A进来，通过计算其key的hash得到的index=0，记做:Entry[0] = A。一会后又进来一个键值对B，通过计算其index也等于0，现在怎么办？HashMap会这样做:B.next = A,Entry[0] = B,如果又进来C,index也等于0,那么C.next = B,Entry[0] = C；这样我们发现index=0的地方其实存取了A,B,C三个键值对,他们通过next这个属性链接在一起。所以疑问不用担心。也就是说数组中存储的是最后插入的元素。到这里为止，HashMap的大致实现

## 6. HashMap问题 jdk1.8优化
（1）HashMap如果有很多相同key，后面的链很长的话，你会怎么优化？或者你会用什么数据结构来存储？针对HashMap中某个Entry链太长，查找的时间复杂度可能达到O(n)，怎么优化？
Java8 做的改变：
- HashMap 是数组+链表+红黑树（JDK1.8 增加了红黑树部分），当链表长度>=8 时转化为红黑树
在 JDK1.8 版本中，对数据结构做了进一步的优化，引入了红黑树。而当链表长度太长（默认超过 8）时，链表就转换为红黑树，利用红黑树快速增删改查的特点提高 HashMap 的性能，其中会用到红黑树的插入、删除、查找等算法。
- java8  中对 hashmap 扩容不是重新计算所有元素在数组的位置，而是我们使用的是 2 次幂的扩展(指长度扩为原来 2  倍)，所以，元素的位置要么是在原位置，要么是在原位置再移动 2 次幂的位置在扩充 HashMap 的时候，不需要像 JDK1.7 的实现那样重新计算 hash， 只需要看看原来的 hash 值新增的那个 bit 是 1 还是 0 就好了，是 0 的话索引没变，是 1 的话索引变成“原索引+oldCap”。


## 7. 一些面试题

###  7.1 HashMap 和 TreeMap 的区别
Hashmap 使用的是数组+链表，treemap 是红黑树

###  7.2 hashmap 为什么可以插入空值？
HashMap 中添加 key==null 的 Entry 时会调用 putForNullKey 方法直接去遍历
table[0]Entry 链表，寻找 e.key==null 的 Entry 或者没有找到遍历结束

如果找到了 e.key==null，就保存 null 值对应的原值 oldValue，然后覆盖原值，并返回oldValue
如果在 table[0]Entry 链表中没有找到就调用addEntry 方法添加一个 key 为 null 的 Entry
### 7.3 Hashmap 为什么线程不安全：(hash 碰撞和扩容导致)
- HashMap 底层是一个Entry 数组，当发生 hash 冲突的时候，hashmap 是采用链表的方式来解决的，在对应的数组位置存放链表的头结点。对链表而言，新加入的节点会从头结点加入。假如 A 线程和B 线程同时对同一个数组位置调用 addEntry，两个线程会同时得到现在的头结点，然后 A 写入新的头结点之后，B 也写入新的头结点，那 B 的写入操作就会覆盖A 的写入操作造成A 的写入操作丢失
- 删除键值对的代码如上：当多个线程同时操作同一个数组位置的时候，也都会先取得现在状态下该位置存储的头结点，然后各自去进行计算操作，之后再把结果写会到该数组位置去， 其实写回的时候可能其他的线程已经就把这个位置给修改过了，就会覆盖其他线程的修改
- 当多个线程同时检测到总数量超过门限值的时候就会同时调用 resize 操作，各自生成新的数组并 rehash 后赋给该map 底层的数组 table，结果最终只有最后一个线程生成的新数组被赋给 table 变量，其他线程的均会丢失。而且当某些线程已经完成赋值而其他线程刚开始的时候，就会用已经被赋值的 table 作为原始数组，这样也会有问题。
### 7.4 Hashmap 碰撞严重
可以自定义重写 hash——多 hash 函数
### 7.4 HashMap 高并发情况下会出现什么问题？ 
扩容问题
### 7.5 HashMap 的存放自定义类时，需要实现自定义类的什么方法？
答：hashCode 和equals。通过 hash(hashCode)然后模运算（其实是与的位操作）定位在Entry 数组中的下标，然后遍历这之后的链表，通过 equals 比较有没有相同的 key，如果有直接覆盖 value，如果没有就重新创建一个 Entry。

### 7.6 Hashmap为什么线程不安全
hash碰撞和扩容导致,HashMap扩容的的时候可能会形成环形链表，造成死循环。
### 7.7 Hashmap中的key可以为任意对象或数据类型吗？
可以为null但不能是可变对象,如果是可变对象的话,对象中的属性改变,则对象 HashCode也进行相应的改变,导致下次无法查找到己存在Map中的效据
如果可变对象在 HashMap中被用作键,时就要小心在改变对象状态的时候,不要改变它的哈希值了。我们只需要保证成员变量的改变能保证该对象的哈希值不变即可.

# 二. CurrentHashMap
http://www.importnew.com/21781.html
https://blog.csdn.net/dingji_ping/article/details/51005799
https://www.cnblogs.com/chengxiao/p/6842045.html
http://ifeve.com/hashmap-concurrenthashmap-%E7%9B%B8%E4%BF%A1%E7%9C%8B%E5%AE%8C%E8%BF%99%E7%AF%87%E6%B2%A1%E4%BA%BA%E8%83%BD%E9%9A%BE%E4%BD%8F%E4%BD%A0%EF%BC%81/
## 1. 概述

![](https://github.com/gzc426/picts/blob/master/%E5%9B%BE%E7%89%873.png)
一个ConcurrentHashMap维护一个Segment数组，一个Segment维护一个HashEntry数组。
## 2. JDK1.7 ConCurrentHashMap原理
其中 Segment 继承于 ReentrantLock
ConcurrentHashMap 使用分段锁技术，将数据分成一段一段的存储，然后给每一段数据配一把锁，当一个线程占用锁访问其中一个段数据的时候，其他段的数据也能被其他线程访问， 能够实现真正的并发访问。

![](https://github.com/gzc426/picts/blob/master/%E5%9B%BE%E7%89%874.png)

Segment继承了ReentrantLock，表明每个segment都可以当做一个锁。这样对每个segment中的数据需要同步操作的话都是使用每个segment容器对象自身的锁来实现。只有对全局需要改变时锁定的是所有的segment。
![](https://github.com/gzc426/picts/blob/master/%E5%9B%BE%E7%89%875.png)
## 3. JDK1.7 Get
![](https://github.com/gzc426/picts/blob/master/%E5%9B%BE%E7%89%876.png)
- CurrentHashMap是否使用了锁？？？

它也没有使用锁来同步，只是判断获取的entry的value是否为null，为null时才使用加锁的方式再次去获取。 这里可以看出并没有使用锁，但是value的值为null时候才是使用了加锁！！！

- Get原理：
第一步，先判断一下 count != 0；count变量表示segment中存在entry的个数。如果为0就不用找了。假设这个时候恰好另一个线程put或者remove了这个segment中的一个entry，会不会导致两个线程看到的count值不一致呢？看一下count变量的定义： transient volatile int count;
它使用了volatile来修改。我们前文说过，Java5之后，JMM实现了对volatile的保证：对volatile域的写入操作happens-before于每一个后续对同一个域的读写操作。所以，每次判断count变量的时候，即使恰好其他线程改变了segment也会体现出来
![](https://github.com/gzc426/picts/blob/master/%E5%9B%BE%E7%89%877.png)

### 3.1 在get代码的①和②之间，另一个线程新增了一个entry
如果另一个线程新增的这个entry又恰好是我们要get的，这事儿就比较微妙了。下图大致描述了put 一个新的entry的过程。

![](https://github.com/gzc426/picts/blob/master/%E5%9B%BE%E7%89%878.png)

因为每个HashEntry中的next也是final的，没法对链表最后一个元素增加一个后续entry所以新增一个entry的实现方式只能通过头结点来插入了。newEntry对象是通过 new HashEntry(K k , V v, HashEntry next) 来创建的。如果另一个线程刚好new 这个对象时，当前线程来get它。因为没有同步，就可能会出现当前线程得到的newEntry对象是一个没有完全构造好的对象引用。   如果在这个new的对象的后面，则完全不影响，如果刚好是这个new的对象，那么当刚好这个对象没有完全构造好，也就是说这个对象的value值为null,就出现了如下所示的代码，需要重新加锁再次读取这个值！

### 3.2 在get代码的①和②之间，另一个线程修改了一个entry的value
value是用volitale修饰的，可以保证读取时获取到的是修改后的值。
### 3.3 在get代码的①之后，另一个线程删除了一个entry
假设我们的链表元素是：e1-> e2 -> e3 -> e4 我们要删除 e3这个entry，因为HashEntry中next的不可变，所以我们无法直接把e2的next指向e4，而是将要删除的节点之前的节点复制一份，形成新的链表。它的实现大致如下图所示：

如果我们get的也恰巧是e3，可能我们顺着链表刚找到e1，这时另一个线程就执行了删除e3的操作，而我们线程还会继续沿着旧的链表找到e3返回。这里没有办法实时保证了，也就是说没办法看到最新的。
我们第①处就判断了count变量，它保障了在 ①处能看到其他线程修改后的。①之后到②之间，如果再次发生了其他线程再删除了entry节点，就没法保证看到最新的了，这时候的get的实际上是未更新过的！！！。
不过这也没什么关系，即使我们返回e3的时候，它被其他线程删除了，暴漏出去的e3也不会对我们新的链表造成影响。

2. JDK1.7 PUT
1.将当前 Segment 中的 table 通过 key 的 hashcode 定位到 HashEntry。
2.遍历该 HashEntry，如果不为空则判断传入的 key 和当前遍历的 key 是否相等，相等则覆盖旧的 value。
3.不为空则需要新建一个 HashEntry 并加入到 Segment 中，同时会先判断是否需要扩容。
4.最后会解除在 1 中所获取当前 Segment 的锁。

可以说是首先找到segment，确定是哪一个segment,然后在这个segment中遍历查找 key值是要查找的key值得entry,如果找到，那么就修改该key,如果没找到，那么就在头部新加一个entry.
