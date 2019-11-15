# IOC学习总结

引入核心jar包,`bean, context, core, expression+logging`

## 引入主配置文件

1. `applicatationContext.xml`,管理bean.  
2. 创建实例的三种方式:
   - 构造方法
   - 静态工厂
   - 工厂方法
   - tips: 当容器中存在多个类型的对象(bean)时,只能通过id来区分获取.

## 测试程序

1. 获取一个容器的实例,根据配置文件`applicationContext.xml`来生成.

2. 通过容器对象,来获取里面它管理的bean
