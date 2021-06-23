---
title: 工厂模式
description: Factory Pattern
date: 2021-06-04
draft: false
weight: 2
---
# 工厂模式
## 简介

- Factory Pattern
- 定义一个用于创建对象的接口，让子类决定实例化哪一个类。




## 示例

### 简单工厂

```java
// 类似产品：XiaoMi，Iphone
public interface Phone {
     void function();
}
public class HuanWei implements Phone{
    @Override
    public void function() {
        System.out.println("华为手机");
    }
} 
```
```java
// 统一工厂
public class PhoneFactory {
    public static Phone createPhone(String type){
        if ("XiaoMi".equals(type)){
            return new XiaoMi();
        }
        if ("HuanWei".equals(type)){
            return new HuanWei();
        }
        if ("Iphone".equals(type)){
            return new Iphone(); 
        }
        return null; 
    }
}
```



### 工厂方法

- **何时使用**
  - 明确计划不同条件下创建不同实例时。
- **应用场景**
  - 日志记录器（记录到硬盘/系统事件/远程服务器）
  - 数据库访问（多种类型数据库）
  - 连接服务器（多种通讯协议）

```java
// 类似产品：XiaoMi，Iphone
public interface Phone {
     void function();
}
public class HuanWei implements Phone{
    @Override
    public void function() {
        System.out.println("华为手机");
    }
}
```
```java
// 类似工厂：XiaoMiFactory，IphoneFactory
public interface PhoneFactory {
     Phone createPhone(); 
}
public class HuanWeiFactory implements PhoneFactory { 
    @Override
    public Phone createPhone() {
        return new HuanWei();
    }
}
```



### 抽象工厂

- **何时使用：** 系统的产品有多于一个的产品族，而系统只消费其中某一族的产品。
- **应用场景：** 生成不同操作系统的程序
- **注意事项：** 产品族难扩展，产品等级易扩展

```java
// 类似产品族：Camera、Screen
public interface CPU {
    void name();
}

// 类似产品等级：XiaoM、Iphone
public class HuanWeiCPU implements CPU {
    void name();
}
public class HuanWeiCamera implements Camera {
    void name();
}
public class HuanWeiScreen implements Screen {
    void name();
}
```
```java
// 类似工厂：XiaoMiFactory、IphoneFactory
public interface PhoneFactory {
    CPU createCpu();
    Camera createCamera();
    Screen createScreen();
}
public class HuanWeiFactory implements PhoneFactory { 
    @Override
    public CPU createCpu() {
        return new HuanWeiCPU();
    } 
    @Override
    public Camera createCamera() {
        return new HuanWeiCamera();
    } 
    @Override
    public Screen createScreen() {
        return new HuanWeiScreen();
    }
}
```
