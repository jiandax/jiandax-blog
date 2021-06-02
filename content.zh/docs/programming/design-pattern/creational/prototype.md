---
title: "原型模式"
description: "Prototype"
date: 2021-01-24T00:54:27+08:00
enableToc: true
draft: false
weight: 2
---



# 概述

- Prototype
- 用原型实例指定创建对象的种类，并且通过拷贝这些原型创建新的对象。



# 应用

- **主要解决：** 在运行期建立和删除原型
- **何时使用：** 
  - 当一个系统应该独立于它的产品创建，构成和表示时。 
  - 当要实例化的类是在运行时刻指定时，例如，通过动态装载。 
  - 为了避免创建一个与产品类层次平行的工厂类层次时。 
  - 当一个类的实例只能有几个不同状态组合中的一种时。
- **如何解决：** 判断系统是否已经有这个单例，如果有则返回，如果没有则创建。
- **关键代码：** 构造函数是私有的。
- 使用场景：
  - 要求生产唯一序列号。
  - WEB 中的计数器，不用每次刷新都在数据库里加一次，用单例先缓存起来。
  - 创建的一个对象需要消耗的资源过多，比如 I/O 与数据库的连接等。
- 注意事项：
  - 防止多线程情况下，实例被多次创建
  - 单例类不要实现Cloneable接口



# 优缺点



# 示例

```java
//原型类：1、实现Cloneable接口
class Prototype implements Cloneable{
    //2、覆写clone方法
    @Override
    public Prototype clone(){
        Prototype p = null;
        try {
            p = (Prototype)super.clone();
        } catch (CloneNotSupportedException e) {
            System.out.println("克隆失败...");
        }
        return p;
    }
    
    private String value;
    //setter、getter...
}

//情景类
public class Client {
    public static void main(String[] args) {
        Prototype p1=new Prototype();
        p1.setValue("张三");
        
        //以p1为原型，克隆得到p2
        Prototype p2=p1.clone();
        System.out.println("p2："+p2.getValue());
    }
}
```



# 应用

- 主要解决：在运行期建立和删除原型
- 资源优化场景
- 类初始化需要消耗很多资源的场景
- 性能和安全的场景
- 一个对象多个修改者的场景
- 原型模式一般与工厂模式配合使用



# 优缺点

- 性能优良（内存二进制流的拷贝）
- 逃避构造函数的约束
- 必须实现Cloneable接口
- 对于已有的类不容易实现该模式



# 注意事项

- 克隆过程中，不会执行被克隆类的构造方法
- 浅拷贝：Object类的clone()只拷贝类方法、类成员（基本数据类型+String类型）
- 深拷贝：对引用数据类型的类成员也进行拷贝

