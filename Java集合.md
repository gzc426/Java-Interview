
# 一.HashMap
https://blog.csdn.net/jiary5201314/article/details/51439982
## 1.hashMap的原理
hashmap  是数组和链表的结合体，数组每个元素存的是链表的头结点 往 hashmap
里面放键值对的时候先得到 key 的 hashcode，然后重新计算 hashcode， （让 1 分布均匀因为如果分布不均匀，低位全是 0，则后来计算数组下标的时候会 冲突），然后与 length-1 按位与，计算数组出数组下标 如果该下标对应的链表为空，则直接把键值对作为链表头结点，如果不为空，则 遍历链表看是否有 key 值相同的，有就把 value 替换， 没有就把该对象最为链表的第 一个节点，原有的节点最为他的后续节点
## 2.hashcode的计算
https://www.zhihu.com/question/20733617/answer/111577937
https://blog.csdn.net/justloveyou_/article/details/62893086
Key.hashcode是key的自带的hascode函数是一个int值32位

hashmap jdk1.8 中 hashmap 重计算 hashcode 方法改动： 高 16 位异或低 16 位
>return (key == null) ? 0 : h = key.hashCode() ^ (h >>> 16);
首先确认：当 length 总是 2 的n 次方时， h & (length - 1)	等价于	hash 对length 取模 ， 但是&比%具有更高的效率；
>Jdk1.7 之前：h & (length - 1);//第三步，取模运算

![](https://github.com/gzc426/picts/blob/master/%E5%BE%AE%E4%BF%A1%E5%9B%BE%E7%89%87_20191002175517.jpg)

## 3.hashMap参数以及扩容机制
初始容量 16，达到阀值扩容，阀值等于最大容量*负载因子，扩容每次 2 倍，总是 2 的n 次方
扩容机制：
使用一个容量更大的数组来代替已有的容量小的数组，transfer()方法将原有 Entry 数组的元素拷贝到新的 Entry 数组里，Java1.重新计算每个元素在数组中的位置。Java1.8 中不是重新计算，而是用了一种更巧妙的方式。
## 4.get()方法

## 5.put()方法
这里HashMap里面用到链式数据结构的一个概念。上面我们提到过Entry类里面有一个next属性，作用是指向下一个Entry。打个比方， 第一个键值对A进来，通过计算其key的hash得到的index=0，记做:Entry[0] = A。一会后又进来一个键值对B，通过计算其index也等于0，现在怎么办？HashMap会这样做:B.next = A,Entry[0] = B,如果又进来C,index也等于0,那么C.next = B,Entry[0] = C；这样我们发现index=0的地方其实存取了A,B,C三个键值对,他们通过next这个属性链接在一起。所以疑问不用担心。也就是说数组中存储的是最后插入的元素。到这里为止，HashMap的大致实现

## 6.HashMap问题 jdk1.8优化
（1）HashMap如果有很多相同key，后面的链很长的话，你会怎么优化？或者你会用什么数据结构来存储？针对HashMap中某个Entry链太长，查找的时间复杂度可能达到O(n)，怎么优化？
Java8 做的改变：
- HashMap 是数组+链表+红黑树（JDK1.8 增加了红黑树部分），当链表长度>=8 时转化为红黑树
在 JDK1.8 版本中，对数据结构做了进一步的优化，引入了红黑树。而当链表长度太长（默认超过 8）时，链表就转换为红黑树，利用红黑树快速增删改查的特点提高 HashMap 的性能，其中会用到红黑树的插入、删除、查找等算法。
- java8  中对 hashmap 扩容不是重新计算所有元素在数组的位置，而是我们使用的是 2 次幂的扩展(指长度扩为原来 2  倍)，所以，元素的位置要么是在原位置，要么是在原位置再移动 2 次幂的位置在扩充 HashMap 的时候，不需要像 JDK1.7 的实现那样重新计算 hash， 只需要看看原来的 hash 值新增的那个 bit 是 1 还是 0 就好了，是 0 的话索引没变，是 1 的话索引变成“原索引+oldCap”。


## 7.一些面试题

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

