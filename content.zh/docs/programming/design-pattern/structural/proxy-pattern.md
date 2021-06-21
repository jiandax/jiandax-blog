---
title: 代理模式
description: Proxy Pattern
date: 2021-06-07
draft: false
weight: 1
---


# 代理模式

## 简介

- Proxy Pattern
- 为其他对象提供一种代理以控制对这个对象的访问。



## 示例

| 类型           | 区别                                                         |
| :------------- | :----------------------------------------------------------- |
| 静态代理       | 手动生成代理类                                               |
| 动态代理       | 运用反射机制，动态生成代理类                                 |
| JDK 动态代理   | 只能代理实现了接口的类                                       |
| CGLib 动态代理 | 对目标类生成一个子类，并覆盖其中方法实现增强。 <br/>但因为采用的是继承，所以不能对final修饰的类进行代理 |



### 静态代理

```java
public interface Wow {
    void tbc();
}

public class Blizzard implements Wow {
    @Override
    public void tbc() {
        System.out.println("《魔兽世界》：燃烧的远征");
    }
}

public class NetEasy implements Wow {
    private Blizzard blizzard;

    // 传递被代理对象 
    public NetEasy(Blizzard blizzard) {
        this.blizzard = blizzard;
    }

    // 控制被代理对象的行为
    @Override
    public void tbc() {
        System.out.println("网易代理《魔兽世界》开始");
        blizzard.tbc();
        System.out.println("网易代理《魔兽世界》结束");
    }
}

public class Test {
    public static void main(String[] args) {
        Wow wow = new NetEasy(new Blizzard());
        wow.tbc();
    }
}  
```



### 动态代理（JDK）

```java
public class ProxyHandler implements InvocationHandler {
    private Object target;

    // 获取被代理对象
    public Object newProxyInstance(Object target) {
        this.target = target;
        return Proxy.newProxyInstance(
                target.getClass().getClassLoader(), target.getClass().getInterfaces(), this);
    }

    // 操作被代理对象的行为
    @Override
    public Object invoke(Object proxy, Method method, Object[] args) throws Throwable {
        System.out.println("JDK：动态代理开始");
        Object result = method.invoke(target, args);
        System.out.println("JDK：动态代理结束");
        return result;
    }
}

public class Test {
    public static void main(String[] args) {
        ProxyHandler handler = new ProxyHandler(new Blizzard());
        Wow wow = (Wow) handler.newProxyInstance();
        wow.tbc();
    }
}
```



### 动态代理（CGLIB）

```java
public class CglibInterceptor implements MethodInterceptor {
    private Enhancer enhancer = new Enhancer();

    // 获取被代理对象
    public Object newProxyInstance(Class<?> clazz) {
        enhancer.setSuperclass(clazz);
        enhancer.setCallback(this);
        return enhancer.create();
    }

    // 操作被代理对象的行为
    @Override
    public Object intercept(
        Object target, Method method, Object[] args, MethodProxy methodProxy) throws Throwable {
        
        System.out.println("CGLIB：动态代理开始");
        Object result = methodProxy.invokeSuper(target, args);
        System.out.println("CGLIB：动态代理结束");
        return result;
    }
}

public class Test {
    public static void main(String[] args) {
        CglibInterceptor interceptor = new CglibInterceptor();
        Wow wow = (Wow) interceptor.newProxyInstance(Blizzard.class);
        wow.tbc();
    }
}
```



## 应用

- **主要解决：** 直接访问对象时带来的问题（安全控制、进程外访问、对象创建开销大）
- **何时使用：** 想在访问一个类时做一些控制
- **应用场景：** Spring AOP、Windows 快捷方式
- **注意事项：**
  - 适配器模式主要改变所考虑对象的接口，而代理模式不能改变所代理类的接口
  - 装饰器模式为了增强功能，而代理模式是为了加以控制