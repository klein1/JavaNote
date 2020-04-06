## hashCode() 

**获取哈希码，也称为散列码；它实际上是返回一个int整数。**

作用是确定该对象在哈希表中的索引位置，定义在Object类中，这就意味着Java中的任何类都包含有hashCode() 函数。

hashCode() 定义在JDK的Object.java中，这就意味着Java中的任何类都包含有hashCode() 函数。



散列表存储的是键值对（key-value），它的特点是：能根据“键”快速的检索出对应的“值”，这其中就利用到了散列码。**hashCode() 在散列表（HashMap，Hashtable，HashSet）中才有用，在其它情况下没用。**



### hashCode（）与 equals（）的相关规定

1. 如果两个对象相等，则 hashcode 一定也是相同的
2. 两个对象相等,对两个对象分别调用 equals 方法都返回 true
3. 两个对象有相同的 hashcode 值，它们也不一定是相等的
4. **因此，equals 方法被覆盖过，则 hashCode 方法也必须被覆盖**
5. hashCode() 的默认行为是对堆上的对象产生独特值。如果没有重写 hashCode()，则该 class 的两个对象无论如何都不会相等（即使这两个对象指向相同的数据）