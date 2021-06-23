---
title: 外观模式
description: Facade Pattern
date: 2021-06-23
draft: false
weight: 5
---

# 外观模式

## 简介

- Facade Pattern
- 隐藏系统的复杂性，并向客户端提供了一个客户端可以访问系统的接口。



## 示例

```java
public interface Shape {
    void draw();
}

// 类似子系统：Rectangle、Square
public class Circle implements Shape {
    @Override
    public void draw() {
        System.out.println("Circle::draw()");
    }
}
```
```java
// 外观类
public class ShapeMaker {
    private Shape circle;
    private Shape rectangle;
    private Shape square;

    public ShapeMaker() {
        circle = new Circle();
        rectangle = new Rectangle();
        square = new Square();
    }

    public void drawCircle() {
        circle.draw();
    }

    public void drawRectangle() {
        rectangle.draw();
    }

    public void drawSquare() {
        square.draw();
    }
}
```
```java
public class Test {
    public static void main(String[] args) {
        ShapeMaker shapeMaker = new ShapeMaker();

        shapeMaker.drawCircle();
        shapeMaker.drawRectangle();
        shapeMaker.drawSquare();
    }
}
```



## 应用

- **主要解决：** 
  - 降低访问复杂系统的内部子系统时的复杂度，简化客户端与之的接口
- **何时使用：** 
  - 客户端不需要知道系统内部的复杂联系，整个系统只需提供一个"接待员"即可
  - 定义系统的入口。
- **应用场景：** 
  - JAVA 的三层开发模式
  - 为复杂的模块或子系统提供外界访问的模块
  - 子系统相对独立
  - 预防低水平人员带来的风险
- **注意事项：** 
  - 在层次化结构中，可以使用外观模式定义系统中每一层的入口