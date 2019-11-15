# 简介 #
**LinkedList**是一个实现了**List接口**和**Deque接口**的**双端链表**.LinkedList底层的链表结构使它**支持高效的插入和删除操作**,另外它实现了Deque接口,使得LinkedList类也具有了队列的特性;LinkedList**不是线程安全的**,如果想使LinkedList变成线程安全的,可以调用静态类**Collection类**中的**synchronizedList**方法:
```java
List list=Collections.synchronizedList(new LinkedList(...));
```
#内部结构分析
LinkedList类中有一个**内部私有类Node**:
```java
private static class Node<E> {
        E item;//节点值
        Node<E> next;//后继节点
        Node<E> prev;//前驱节点

        Node(Node<E> prev, E element, Node<E> next) {
            this.item = element;
            this.next = next;
            this.prev = prev;
        }
    }
```
# LinkeList源码分析 #
## 构造方法 ##
### 空构造方法 ###
	publick LinkedList(){
	}
### 用已有的集合创建链表的构造方法 ###
	public LinkedList(Collection<? extends E> c){
		this();
		addAll(c);
	}
### add方法 ###
add(E e)方法:将元素添加到链表尾部
```java
public boolean add(E e){
	linkLast(e);
	return true;
}

void linkLast(E e){
	final Node<E> l = last;
	final Node<E> newNode = new Node<>(l,e,null);
	last = newNode;
	if (l == null)
		first = newNode;
	else
		l.next = newNode;
	size++;
	modCount++;
```
add(int indext, E e):在指定位置添加元素
	