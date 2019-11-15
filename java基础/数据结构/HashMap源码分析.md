# HashMap简介 #

HashMap主要用来存放键值对,它基于哈希表的Map接口实现,是常用的java集合之一.

## 底层数据结构分析 ##

JDK1.8之前,HashMap通过key的hashcode经过扰动函数处理得到hash值,然后通过`(n-1) & hash`判断当前元素存放的位置,
如果当前位置存在元素的话,就判断该元素与要存入的元素的hash值以及key是否相同,如果相同则直接覆盖,不相同就通过拉链法
解决冲突.  

所谓扰动函数就是指HashMap的hash方法.使用hash方法是为了防止一些实现比较差的hashCode()方法,就是为了减少碰撞.
**hash方法源码**

```java
//JDK1.8
static final int hash(Object key){
	int h;
	return (key == null) ? 0 : (h = key.hashCode()) ^ (h >>> 16);
}

//JDK1.7
static int hash(int h){
	h ^= (h >>> 20) ^ (h >>> 12);
	return h ^ (h >>> 7) ^ (h >>> 4);
}
```

### 类的属性 ###

```java
public class HashMap<K,V> extends AbstractMap<K,V> implements Map<K,V>, Cloneable, Serializable {
    // 序列号
    private static final long serialVersionUID = 362498820763181265L;  
    // 默认的初始容量是16
    static final int DEFAULT_INITIAL_CAPACITY = 1 << 4;
    // 最大容量
    static final int MAXIMUM_CAPACITY = 1 << 30;
    // 默认的填充因子
    static final float DEFAULT_LOAD_FACTOR = 0.75f;
    // 当桶(bucket)上的结点数大于这个值时会转成红黑树
    static final int TREEIFY_THRESHOLD = 8;
    // 当桶(bucket)上的结点数小于这个值时树转链表
    static final int UNTREEIFY_THRESHOLD = 6;
    // 桶中结构转化为红黑树对应的table的最小大小
    static final int MIN_TREEIFY_CAPACITY = 64;
    // 存储元素的数组，总是2的幂次倍
    transient Node<k,v>[] table;
    // 存放具体元素的集
    transient Set<map.entry<k,v>> entrySet;
    // 存放元素的个数，注意这个不等于数组的长度。
    transient int size;
    // 每次扩容和更改map结构的计数器
    transient int modCount;
    // 临界值 当实际大小(容量*填充因子)超过临界值时，会进行扩容
    int threshold;
    // 加载因子
    final float loadFactor;
}
```
