---
title: "工厂方法模式"
description: "Factory Method"
date: 2021-03-24T23:24:43+08:00
enableToc: true
draft: false
weight: 4
---




# 概述

- Factory Method
- 定义一个用于创建对象的接口，让子类决定实例化哪一个类。



# 示例

- 每种产品一个工厂

```java
//抽象产品
abstract class AbsProduct {
    public abstract void operate();
}

//具体产品：A、B、C...
class ProductA extends AbsProduct {
    public void operate() {
        System.out.println("ProductA");
    }
}

//抽象工厂
interface class AbsFactory{
    public <T extends AbsProduct> T createProduct();
}

//具体工厂：A、B、C...
class FactoryA implements AbsFactory{
    @Override
    public AbsProduct createProduct(){
        return new ProductA();
    }
}

//情景类
public class Client{
    public static void main(String[] args){
        FactoryA factoryA = new FactoryA();
        AbsProduct productA = factoryA.createProduct();
        productA.operate();

        FactoryB factoryB = new FactoryB();
        AbsProduct productB = factoryB.createProduct();
        productB.operate();
    }
}
```






# 应用

- 主要解决：接口选择的问题
- 日志记录器（记录到硬盘/系统事件/远程服务器）
- 数据库访问（多种类型数据库）
- 连接服务器（多种通讯协议）



# 优缺点

- 屏蔽产品的具体实现。
- 扩展性高，可以容易的增加产品

- 增加产品时，需要增加一个具体类和对象实现工厂，增加了复杂度



# 注意事项

- 工厂方法：针对的是一个产品等级结构，由子类决定实例化那个类
- 抽象工厂：针对的是多个产品等级结构，由父类决定实例化哪个类