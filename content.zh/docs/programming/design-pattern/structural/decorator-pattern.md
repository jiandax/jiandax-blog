---
title: 装饰模式
description: Decorator Pattern
date: 2021-06-21
draft: false
weight: 3
---


# 装饰模式

## 简介

- Decorator Pattern
- 不改变原类结构、不使用继承的情况下，动态地给一个对象添加一些额外的职责。



## 示例

```java
// 被装饰类
public interface Shape {
    void draw();
}

// 类似形状：Circle
public class Rectangle implements Shape {
    @Override
    public void draw() {
        System.out.println("Shape: 正方形");
    }
}
```
```java
// 装饰类
public abstract class ShapeDecorator implements Shape {
    protected Shape shape;
    public ShapeDecorator(Shape shape) {
        this.shape = shape;
    }

    @Override
    public void draw() {
        shape.draw();
    }
}

// 类似装饰类:GreenShapeDecorator
public class RedShapeDecorator extends ShapeDecorator {
    public RedShapeDecorator(Shape shape) {
        super(shape);
    }

    @Override
    public void draw() {
        super.draw();
        setRedBorder(shape);
    }

    private void setRedBorder(Shape shape) {
        System.out.println("Border Color: Red");
    }
}
```
```java
public class Test {
    public static void main(String[] args) {
        Shape circle = new Circle();
        ShapeDecorator redCircle = new RedShapeDecorator(new Circle());
        ShapeDecorator redRectangle = new RedShapeDecorator(new Rectangle());

        System.out.println("Circle with normal border");
        circle.draw();

        System.out.println("Circle of red border");
        redCircle.draw();

        System.out.println("Rectangle of red border");
        redRectangle.draw();
    }
}
```



## 应用

- **主要解决：** 使用继承方式扩展类的功能，随着扩展功能的增多，导致子类膨胀问题
- **应用场景：** 扩展一个类的功能、动态增加/撤销功能
- **注意事项：** 可代替继承