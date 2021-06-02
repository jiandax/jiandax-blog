---
title: "建造者模式"
description: "Builder"
date: 2021-01-24T00:53:56+08:00
enableToc: true
draft: false
weight: 3
---

# 概述

- Builder
- 将一个复杂对象的构建与它的表示分离，使得同样的构建过程可以创建不同的表示。



# 示例

```java
//产品：被构造的复杂对象
class Product {
    private String part1;
    private String part2;
    //set、get、toString...
}

//抽象建造者：规定产品所需零件，并建造产品
interface AbsBuilder {
    void setPart1();
    void setPart2();
    Product build();
}

//具体建造者：A、B、C...
class BuilderA implements AbsBuilder {
    private Product product= new Product();

    @Override
    public void setPart1() {
        product.setPart1("A1");  
    }
    @Override
    public void setPart2() {
        product.setPart2("A2");  
    }
    @Override
    public Product build() {
        return product;
    }
}

//导演类：调用建造者，指导产品零件的组装流程
class Director{
    public Product getProduct(AbsBuilder builder){
        builder.setPart1();
        builder.setPart2();
        return builder.build();
    }
}

//情景类
public class Client{
    public static void main(String[] args){
        Director director=new Director();
        Product a=director.getProduct(new BuilderA());
        Product b=director.getProduct(new BuilderB());
        System.out.println(a.toString());
        System.out.println(b.toString());
    }
}
```




# 应用

- 当创建复杂对象的算法应该独立于该对象的组成部分以及它们的装配方式时。
- 当构造过程必须允许被构造的对象有不同的表示时。



# 优缺点

- 封装性很好，便于控制细节风险
- 建造者独立，易扩展



# 注意事项

- 建造者模式关注的是零件类型和装配顺序，即产品的建造过程 
