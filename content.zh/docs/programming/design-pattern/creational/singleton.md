---
title: "单例模式"
description: "Singleton"
date: 2021-01-24T00:53:14+08:00
enableToc: true
draft: false
weight: 1
---

# 概述

- Singleton
- 保证一个类仅有一个实例，并提供一个访问它的全局访问点



# 应用

- **主要解决：** 一个全局使用的类频繁的创建与销毁
- **何时使用：** 当您想控制实例数目，节省系统资源的时候。
- **如何解决：** 判断系统是否已经有这个单例，如果有则返回，如果没有则创建。
- **关键代码：** 构造函数是私有的。
- **使用场景：**
  - 要求生产唯一序列号。  
  - WEB 中的计数器，不用每次刷新都在数据库里加一次，用单例先缓存起来。  
  - 创建的一个对象需要消耗的资源过多，比如 I/O 与数据库的连接等。
- **注意事项：**
  - 防止多线程情况下，实例被多次创建
  - 单例类不要实现Cloneable接口



# 优缺点

- 在内存里只有一个实例，减少了内存的开销，尤其是频繁的创建和销毁实例
- 避免对资源的多重占用（比如写文件操作）
- 没有接口，不能继承，与单一职责原则冲突，一个类应该只关心内部逻辑，而不关心外面怎么样来实例化



# 代码实现

## 懒汉式

- 一般情况下，不推荐使用

```java
// 在第一次调用的时候实例化自己
public class Singleton {  
    private static Singleton instance = null; 
    private Singleton() {}  
    public static Singleton getInstance() {  
         if (instance == null) {    
             instance = new Singleton();  
         }    
        return single;  
    }  
}
```



## 饿汉式

- 一般情况下，推荐使用


```java
// 在类初始化时，已经自行实例化   
public class Singleton {
    private static final Singleton instance = new Singleton();
    private Singleton(){}
    public static Singleton getInstance(){
        return instance;
    }
}
```

 

## 双检锁式

- 如果有其他特殊的需求，可以考虑使用

```java
public class Singleton {
    private static volatile Singleton instance = null;    
    private Singleton(){}    
    public static Singleton getInstance(){
        //双重判定：效率、同步
        if(instance == null){
            synchronized(Singleton.class){
                if(instance == null){
                    return new Singleton();
                }
            }
        }
        return instance;        
    }
}
```



## 登记式

- 只有在要明确实现 lazy loading 效果时，才会使用


```java
public class Singleton {  
    private static class SingletonHolder {  
        private static final Singleton INSTANCE = new Singleton();  
    }  
    private Singleton (){}  
    public static final Singleton getInstance() {  
        return SingletonHolder.INSTANCE;  
    }  
}
```

 

## 枚举式

- 如果涉及到反序列化创建对象时，可以尝试使用

```java
public enum Singleton {  
    INSTANCE;  
    public void whateverMethod() {  
    }  
}
```

