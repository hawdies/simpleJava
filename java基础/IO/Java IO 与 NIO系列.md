# IO流学习总结 #  

## 一 Java IO ##

- 按操作方式分类
- 按操作对象分类  

## 二 Java IO体系学习总结 ##

- IO流的分类
- 流的原理浅析
- 常用的IO流

## 三 Java IO面试题 ##

## NIO和AIO的学习总结 ##

### 一 Java NIO概览 ###

1. NIO简介:

2. NIO的特性  

   - IO是面向流的,NIO是面向缓冲区的;
   - IO流是阻塞的,NIO流是非阻塞的;
   - NIO由选择器,IO没有.

3. 读数据和写数据的方式:

   - 从通道进行数据读取
   - 从通道进行数据写入

4. NIO的核心组件

   - Channels
   - Buffers
   - Selectors  

### 二 Jva NIO之Buffer(缓冲区) ###

1. Buffer介绍
2. Buffer的常见方法
3. Buffer的使用方法介绍  

### 三 Java NIO之Channel ###

1. Channel介绍

- 通常来说NIO中的所有IO都是congChannel开始的.

- NIO Channel通道和流的区别

1. FileChannel的使用
2. SocketChannel和ServerSocketChannel的使用
3. DatagramChannel的使用
4. Scatter / Gather
5. 通道之间的数据传输  

### 四 Java NIO之 Selector ###

1. Selecror介绍

- Seletctor一般称为选择器或者多路复用器.用于检查一个或者多个NIO Channel的状态是否处于可读,可写.
