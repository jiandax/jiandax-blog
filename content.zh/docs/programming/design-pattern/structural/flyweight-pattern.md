---
title: 享元模式
description: Flyweight Pattern
date: 2021-06-30
draft: false
weight: 7
---

# 享元模式

## 简介

- Flyweight Pattern
- 运用共享技术有效地支持大量细粒度的对象



## 示例

```java
//抽象享元类
abstract class AbsFlyweight {
    //内部状态：不可改变，可以共享
    protected final String color;
    
    //构造方法：传入内部状态
    public AbsFlyweight(String color){
        this.color = color;
    }
    
    public abstract void display(String position);
}

//具体享元类
class Flyweight extends AbsFlyweight {
    public Flyweight(String color) {
        super(color);
    }
    
    //外部状态：可以改变，不可共享，作为参数传入方法中
    public void display(String position){
        System.out.println("棋子：" + color + "，" + position);
    }
}

```
```java
//享元工厂
class FlyweightFactory {
    //池容器
    private static HashMap<String,Flyweight> pool= new HashMap<>();
    
    //获取享元对象
    public static Flyweight getFlyweight(String color){
        Flyweight flyweight = null;
        if(pool.containsKey(color)){
            System.out.print("————————————");
            flyweight = pool.get(color);
        }else{
            System.out.print("++++++++++++");
            flyweight = new Flyweight(color);
            pool.put(color, flyweight);
        }
        return flyweight;
    }
}
```

```java
public class Test {
    public static void main(String[] args) {
        Flyweight chess;
        for (int i = 0; i < 3; i++) {
            for (int j = 0; j < 3; j++) {
                if(new Random().nextBoolean()){
                    chess=FlyweightFactory.getFlyweight("黑色");
                }else {
                    chess=FlyweightFactory.getFlyweight("白色");
                }
                chess.display("x"+i+"y"+j);
            }
        }
    }
}
```



## 应用

- **主要解决：**  
  - 在有大量对象时，有可能会造成内存溢出。
  - 把其中共同的部分抽象出来，如果有相同的业务请求，直接返回在内存中已有的对象，避免重新创建
- **应用场景：** 
  - 系统有大量相似对象
  - 需要缓冲池的场景
- **注意事项**
  - 注意划分外部状态和内部状态，否则可能会引起线程安全问题。 
  - 这些类必须有一个工厂对象加以控制