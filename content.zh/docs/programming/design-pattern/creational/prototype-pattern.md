---
title: 原型模式
description: Prototype Pattern
date: 2021-06-07
draft: false
weight: 4
---


# 原型模式
## 简介

- Prototype Pattern
- 用原型实例指定创建对象的种类，并且通过拷贝这些原型创建新的对象。



## 示例

```java
//原型类：实现Cloneable接口
public class Prototype implements Cloneable {
	private String name;
    // setter、getter...
    
    // clone方法
    public Object clone(){
        try {
            return super.clone();
        } catch (Exception e) {
            e.printStackTrace();
            return null;
        }
    } 
}

// 情景类
public class Client {
    public static void main(String[] args) {
        Prototype pro1=new Prototype();
        pro1.setName("张三");
        
        //以pro1为原型，克隆得到pro2
        Prototype pro2=(Prototype)pro1.clone();
        System.out.println(pro1.getName());
        System.out.println(pro2.getName());
    }
}
```



## 应用

- **主要解决** 
  - 在运行期建立和删除原型
- **何时使用** 
  - 当一个系统应该独立于它的产品创建，构成和表示时。 
  - 当要实例化的类是在运行时刻指定时，例如，通过动态装载。 
  - 为了避免创建一个与产品类层次平行的工厂类层次时。 
  - 当一个类的实例只能有几个不同状态组合中的一种时。
- **应用实例**
  - 细胞分裂。
  - JAVA 中的 Object clone() 方法。
- **注意事项**
  - 克隆过程中，不会执行被克隆类的构造方法
  - 浅拷贝：Object类的clone()只拷贝类方法、类成员（基本数据类型+String类型）
  - 深拷贝：对引用数据类型的类成员也进行拷贝

