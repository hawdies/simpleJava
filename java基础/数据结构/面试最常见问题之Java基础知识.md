# 集合框架底层数据结构总结 #

## Collection ##

1. **List**  
   * Arraylist: Object数组
   * Vector: Object数组
   * LinkedList: 双向链表
2. **Set**  
   * HashSet(**无序,唯一**):基于HashMap实现的,底层采用HashMap来保存元素
   * LinkedListSet:LinkedListSet继承于HashSet,并且其内部是通过LinkedHashMap来实现的.有点类似于我们之前说过的LinkedHashMap其内部是基于HasMap实现的一样.
   * TreeSet:(**有序,唯一**):红黑树(自平衡的二叉排序树)
  
## Map ##

* HashMap: JDK1.8之前的HashMap由数组+链表组成,数组是HashMap的主体,链表则是主要为了解决哈希冲突而存在的.JDK1.8以后砸死解决哈希冲突时有了较大的变换,当链表的长度大于阈值时,将链表转化为红黑树,减少搜索时间.
* LinkedHshMap:LinkedHashMap继承自HashMap,所以它的底层仍然是基于拉链式散列结构即由数组和链表或红黑树组成.另外,LinkedHashMap在上面的结构基础上,增加了一条双向链表,使得上面的结构可以保持键值对的插入顺序.同时通过对链表进行相应的操作,实现了访问顺序的相关逻辑.详细可以查看:[LinkeHashMap源码详细分析](https://www.imooc.com/article/22931)
* Hashtable:数组+链表组成的,数组是HashMap的主体,链表则主要是用来解决冲突.
* TreeeMap:红黑树
  
## 如何选用集合 ##

主要根据集合的特点来选用,如果需要根据键值对获取元素就选用Map接口下的集合,需要排序时选择时选择TreeMap,不需要排序时就选择HashMap,需要保证线程安全就选用ConcurrentHashMap.当我们只需要存放元素值时,就选择实现了Collection接口的集合,需要保证元素唯一时选择实现了Set接口的集合比如TreeSet或HashSet,不需要就选择实现了List接口的比如ArrayList或LinkedList,然后再根据实现这些接口的集合的特点来选用.
