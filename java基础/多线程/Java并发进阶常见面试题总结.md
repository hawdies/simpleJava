# Java并发进阶常见面试题总结 #

1. synchronized关键字
1.1 对synchronized关键字的了解
1.2 在项目中使用synchronized关键字

**synchronized关键字最主要的三种用法:**

- **修饰实例方法**:作用于当前对象的实例加锁,进入同步代码前要获得当前对象实例的锁
- **修饰静态方法**:也就是给当前类加锁,会所用于类的所有对象实例,因为静态成员不属于任何一个实例对象,是类成员,**访问静态synchronized方法占用的锁是当前类的锁,访问非静态synchronized方法占用的锁是当前实例对象的锁.**
- **修饰代码块**:
  
双重校验锁实现对象单例(线程安全)

```java
public calss Singleton{
	private volatile static Singleton uniqueInstance;
	private Singleton(){
	}
	public static Singleton getUniqueInstance(){
		if (uniqueInstance == null){
		synchronized(singleton.class){
			if (nuiqueInstance == null){
				uniqueInstance = new Singleton();
			}
		}
	}
		return uniqueInstance;
	}
}
```

1.3 讲一下synchronized关键字的底层原理
1.3.1 synchronized同步语句块
synchronized同步语句块使用的monitorenter和monitorexit指令,其中monitorenter指令指向同步代码块的开始位置,monitorexit指令则指明同步代码块的结束位置.当执行monitorenter指令时,线程试图获取锁也就是获取monitor(monitor对象存在于每个java对象的对象头中,synchronized锁便是通过这种方法获取锁的,也是为什么java中任意对象可以作为锁的原因)的特有权.当计数器为0则可以成功获取,获取后将计数器加1.相应的在执行monitorexit指令后,将锁计数器减1.如果当前对象锁获取失败,则需要等待,直到锁被另外一个线程释放为止.
1.3.2 synchronized修饰方法的情况  
synchronized修饰的方法使用ACC_SYNCHRONIZED标识,该标识指明了该方法时一个同步方法,JVM通过该访问标志来辨别一个方法是否声明为同步方法,进而执行相应的同步调用.  

1.4 **说说JDK1.6Z之后的synchronized关键字底层做了哪些优化**
JDK1.6对锁的实现引入了大量优化,如偏向锁,轻量级锁,自旋锁,适应性自旋锁,锁消除,锁粗化等技术来减少锁的开销.
