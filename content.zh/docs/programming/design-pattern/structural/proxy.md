---
title: "代理模式"
description: "Proxy"
date: 2021-06-07
draft: false
weight: 1
---
# 概述

- Proxy
- 为其他对象提供一种代理以控制对这个对象的访问。



# 应用

- 主要解决：直接访问对象时带来的问题（安全控制、进程外访问、对象创建开销大）
- Spring AOP



# 优点

- 职责清晰、高扩展性、智能化



# 缺点

- 由于增加了代理对象，因此可能降低处理速度
- 实现代理模式需要额外的工作，有些代理模式的实现非常复杂



# 注意事项

- 适配器模式主要改变所考虑对象的接口，而代理模式不能改变所代理类的接口
- 装饰器模式为了增强功能，而代理模式是为了加以控制



# 代码示例

## 静态代理


```java
public class Test {
    public static void main(String[] args) {
//
        Wow wow1=new NetEasy(new Blizzard());
        wow1.tbc();

        ProxyHandler handler=new ProxyHandler(new Blizzard());
        Wow wow2= (Wow) handler.newProxyInstance();
        wow2.tbc();

        CglibInterceptor interceptor=new CglibInterceptor();
        Wow wow3= (Wow) interceptor.newProxyInstance(Blizzard.class);
        wow3.tbc();

    }

}
interface Wow{
    void tbc();
}

class Blizzard implements Wow{
    @Override
    public void tbc() {
        System.out.println("Let us start The Burning Crusade");
    }
}

class NetEasy implements Wow{
    private Blizzard blizzard;

    public NetEasy(Blizzard blizzard){
        this.blizzard=blizzard;
    }

    @Override
    public void tbc() {
        System.out.println("NetEasy static proxy WOW start");
        blizzard.tbc();
        System.out.println("NetEasy static proxy WOW over");
    }
}

//动态代理
class ProxyHandler implements InvocationHandler{
    private Object originalObj;

    public ProxyHandler(Object originalObj){
        this.originalObj=originalObj;
    }

    public Object newProxyInstance(){
        return Proxy.newProxyInstance(originalObj.getClass().getClassLoader(),originalObj.getClass().getInterfaces(),this);
    }

    @Override
    public Object invoke(Object proxy, Method method, Object[] args) throws Throwable {
        System.out.println("JDK dynamic proxy WOW start");
        Object result=method.invoke(originalObj,args);
        System.out.println("JDK dynamic proxy WOW over");
        return result;
    }
}

class CglibInterceptor implements MethodInterceptor{
    private Enhancer enhancer=new Enhancer();

    public Object newProxyInstance(Class<?> clazz){
        enhancer.setSuperclass(clazz);
        enhancer.setCallback(this);
        return enhancer.create();
    }

    @Override
    public Object intercept(Object o, Method method, Object[] args, MethodProxy methodProxy) throws Throwable {
        System.out.println("CGLIB dynamic proxy WOW start");
        Object result=methodProxy.invokeSuper(o,args);
        System.out.println("CGLIB dynamic proxy WOW over");
        return result;
    }

}

```



## 动态代理（JDK）

## 动态代理（CGLIB）
