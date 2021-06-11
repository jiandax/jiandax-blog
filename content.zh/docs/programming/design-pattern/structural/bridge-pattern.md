---
title: 桥接模式
description: Bridge Pattern
date: 2021-06-11
draft: false
weight: 2
---


# 桥接模式

## 简介

- Bridge Pattern
- 将抽象和实现解耦，使得两者可以独立地变化。



## 示例

```java
// 品牌
public interface Brand {
    void sale();
}

// 类似品牌：Shenzhou、Huawei
public class Dell implements Brand {
    @Override
    public void sale() {
        System.out.println("出售戴尔");
    }
}

// 电脑
public class Computer {
    protected Brand brand;
    public Computer(Brand brand) {
        this.brand = brand;
    }
    public void sale(){
        brand.sale();
    }
}

// 类似电脑：Laptop
public class Desktop extends Computer {
    public Desktop(Brand b) {
        super(b);
    }
    
    @Override
    public void sale() {
        super.sale();
        System.out.println("出售台式电脑");
    }
}

public class Test {
    public static void main(String[] args) {
        Computer c = new Desktop(new Dell());
        c.sale();
    }
}

```



## 应用

- **核心要点：** 处理多维度变化的场景，将各个维度设计成独立的继承结构，桥接各个维度为一体
- **主要解决：** 在多维度变化的情况下，用继承会造成类爆炸问题，扩展起来不灵活
- **注意事项：** 对于两个独立变化的维度，适合使用桥接模式