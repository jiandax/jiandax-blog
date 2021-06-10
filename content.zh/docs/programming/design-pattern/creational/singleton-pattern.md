---
title: 单例模式
description: Singleton Pattern
date: 2021-06-04
draft: false
weight: 1
---

# 单例模式
## 简介

- Singleton
- 保证一个类仅有一个实例，并提供一个访问它的全局访问点



## 示例

### 饿汉式

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



### 懒汉式

- 一般情况下，不建议使用

```java
// 在第一次调用的时候实例化自己
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



### 登记式

- 内部静态类，只有在要明确实现 lazy loading 效果时，才会使用


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

 

### 枚举式

- 如果涉及到反序列化创建对象时，可以尝试使用

```java
public enum Singleton {  
    INSTANCE;  
    public void whateverMethod() {  
    }  
}
```



## 应用

- **主要解决** 
  - 一个全局使用的类频繁的创建与销毁
- **何时使用** 
  - 当您想控制实例数目，节省系统资源的时候
- **应用实例**
  - 要求生产唯一序列号。  
  - WEB 中的计数器，不用每次刷新都在数据库里加一次，用单例先缓存起来。  
  - 创建的一个对象需要消耗的资源过多，比如 I/O 与数据库的连接等。
- **注意事项**
  - 防止多线程情况下，实例被多次创建
  - 单例类不要实现 Cloneable 接口

