说出所有java集合类
一.HashMap
https://blog.csdn.net/jiary5201314/article/details/51439982
(1)hashMap的原理
hashmap  是数组和链表的结合体，数组每个元素存的是链表的头结点 往 hashmap
里面放键值对的时候先得到 key 的 hashcode，然后重新计算 hashcode， （让 1 分布均匀因为如果分布不均匀，低位全是 0，则后来计算数组下标的时候会 冲突），然后与 length-1 按位与，计算数组出数组下标 如果该下标对应的链表为空，则直接把键值对作为链表头结点，如果不为空，则 遍历链表看是否有 key 值相同的，有就把 value 替换， 没有就把该对象最为链表的第 一个节点，原有的节点最为他的后续节点
2.hashcode的计算
https://www.zhihu.com/question/20733617/answer/111577937
https://blog.csdn.net/justloveyou_/article/details/62893086
Key.hashcode是key的自带的hascode函数是一个int值32位
