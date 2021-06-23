---
title: 适配器模式
description: Adapter Pattern
date: 2021-06-23
draft: false
weight: 4
---

# 适配器模式

## 简介

- Adapter Pattern
- 将一个类的接口变换成客户端所期待的另一种接口，从而使两个不匹配的类能在一起工作。



## 示例

```java
// 源
public class Adaptee {
    public void adapteeMethod() {
        System.out.println("Adaptee method!");
    }
}
```
```java
// 目标
public interface Target {
    void adapteeMethod();
    void adapterMethod();
}
```
```java
// 适配器
public class Adapter implements Target {
    private Adaptee adaptee;
    public Adapter(Adaptee adaptee) {
        this.adaptee = adaptee;
    }

    @Override
    public void adapteeMethod() {
        adaptee.adapteeMethod();
    }

    @Override
    public void adapterMethod() {
        System.out.println("Adapter method!");
    }
}
```
```java
public class Test {
    public static void main(String[] args) {
        Target target = new Adapter(new Adaptee());
        target.adapteeMethod();
        target.adapterMethod();
    }
}
```



## 应用

- **主要解决：** 
  - 现存系统中，将一些“存在的对象”放到新环境中。而这些现存对象，不能满足新环境接口的要求
- **何时使用：** 
  - 系统需要使用现有的类，而此类的接口不符合系统的需要；
  - 通过接口转换，将一个类插入另一个类系中
- **应用场景：** 
  - JAVA 中的 jdbc
  - 有动机地修改一个正常运行的系统的接口
- **注意事项：** 
  - 适配器不是在详细设计时添加的，而是解决正在服役的项目的问题