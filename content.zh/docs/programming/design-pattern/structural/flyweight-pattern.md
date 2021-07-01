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
public interface IChess {
    public void draw();
}

public class Chess implements IChess {
    // 内部状态：不可改变，可以共享
    private String color;
    public Chess(String color) {
        this.color = color;
    }

    // 外部状态：可以改变，不可共享
    private String position;
    public void setPosition(String position) {
        this.position = position;
    }

    @Override
    public void draw() {
        System.out.println("围棋：color=" + color + ", position=" + position);
    }
}
```
```java
// 享元工厂
public class ChessFactory {
    // 池容器
    private static final HashMap<String, IChess> chessMap = new HashMap<>();

    // 获取享元对象
    public static Chess getChess(String color) {
        if (!chessMap.containsKey(color)) {
            chessMap.put(color, new Chess(color));
        }
        return (Chess) chessMap.get(color);
    }
}
```

```java
public class Test {
    public static void main(String[] args) {
        Chess chess;
        for (int i = 0; i < 3; i++) {
            for (int j = 0; j < 3; j++) {
                if (new Random().nextBoolean()) {
                    chess = ChessFactory.getChess("黑色");
                } else {
                    chess = ChessFactory.getChess("白色");
                }
                chess.setPosition("x" + i + "y" + j);
                chess.draw();
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
- **注意事项：**
  - 注意划分外部状态和内部状态，否则可能会引起线程安全问题。 
  - 这些类必须有一个工厂对象加以控制