
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


