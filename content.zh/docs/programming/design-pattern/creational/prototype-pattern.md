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
// 原型类：实现Cloneable接口
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
```
```java
public class Test {
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

- **主要解决:**  在运行期建立和删除原型
- **应用场景：**
  - 细胞分裂。
  - JAVA 中的 Object clone() 方法。
- **注意事项：**
  - 克隆过程中，不会执行被克隆类的构造方法
  - 浅拷贝：Object类的clone()只拷贝类方法、类成员（基本数据类型+String类型）
  - 深拷贝：对引用数据类型的类成员也进行拷贝

