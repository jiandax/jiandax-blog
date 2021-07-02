---
title: 模板模式
description: Template Pattern
date: 2021-07-02
draft: false
weight: 3
---

# 模板模式
## 简介

- Template Pattern
- 定义一个操作中算法的框架，而将一些步骤延迟到子类中，使得子类可以不改变算法的结构即可重定义该算法中的某些特定步骤。



## 示例

```java
public abstract class Game {
    abstract void initialize();
    abstract void startPlay();
    abstract void endPlay();

    // 模板方法
    public final void play() {
        init();
        startPlay();
        endPlay();
    }
}

// 类似游戏：Volleyball
public class Football extends Game {
    @Override
    void init() {
        System.out.println("Football：Initialized! Start playing.");
    }

    @Override
    void startPlay() {
        System.out.println("Football：Started. Enjoy the game!");
    }
    
    @Override
    void endPlay() {
        System.out.println("Football：Finished!");
    }
}
```
```java
public class Test {
    public static void main(String[] args) {
        new Football().play();
        new Volleyball().play();
    }
}
```



## 应用

- **主要解决：**  一些方法通用，却在每一个子类都重新写了这一方法
- **应用场景：** 
  - 有多个子类共有的方法，且逻辑相同；
  - 重要的、复杂的方法，可以考虑作为模板方法
- **注意事项：** 
  - 为防止恶意操作，一般模板方法都加上 final 关键词

