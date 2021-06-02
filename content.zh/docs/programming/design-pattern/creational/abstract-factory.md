---
title: "抽象工厂模式"
description: "Abstract Factory"
date: 2021-03-24T23:25:14+08:00
enableToc: true
draft: false
weight: 5
---




# 概述

- Abstract Factory
- 提供一个创建一系列相关或相互依赖对象的接口，而无需指定它们具体的类



# 示例

- 每个产品簇一个工厂

```java
//抽象产品：Plant、Animal
interface Plant {
    public void info();
}

//具体产品：PlantA、PlantB...AnimalA、AnimalB...
class PlantA implements Plant {       
    public void info() {      
        System.out.println("PlantA");      
    }      
}

//抽象工厂：Plant、Animal
interface AbsFactory {
    public Plant createPlant();      
    public Animal createAnimal();      
}  

//具体工厂：A、B、C...
class FactoryA implements AbsFactory {      
    public Plant createPlant() {      
        return new PlantA();      
    }      
    public Animal createAnimal() {
        return new AnimalA();
    }      
}

//情景类
public class Client {
    public static void main(String[] args) {
        Plant p;
        Animal a;
        
        FactoryA factoryA = new FactoryA(); 
        p=factoryA.createPlant();
        a=factoryA.createAnimal();
        p.info();
        a.info();
        
        FactoryB factoryB = new FactoryB(); 
        p=factoryB.createPlant();
        a=factoryB.createAnimal();
        p.info();
        a.info();
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