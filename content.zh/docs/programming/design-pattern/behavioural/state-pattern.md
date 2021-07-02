---
title: 状态模式
description: State Pattern
date: 2021-07-01
draft: false
weight: 1
---

# 状态模式

## 简介

- State Pattern
- 允许通过改变对象的内部状态，来改变对象的行为，看起来好像修改了对象的类



## 示例

```java
public abstract class LiftState {
    // 定义一个环境角色
    protected Context context;
    public void setContext(Context context) {
        this.context = context;
    }

    public abstract void open();
    public abstract void close();
    public abstract void run();
    public abstract void stop();
}

// 类似状态：ClosingState、RunningState、StoppingState
public class OpeningState extends LiftState {
    @Override
    public void close() {
        super.context.setLiftState(Context.closingState);
        super.context.getLiftState().close();
    }

    @Override
    public void open() {
        System.out.println("电梯门开启...");
    }

    @Override
    public void run() {
        //do nothing;
    }

    @Override
    public void stop() {
        //do nothing;
    }
}
```
```java
public class Context {
    // 定义出所有的电梯状态
    public final static OpeningState openingState = new OpeningState();
    public final static ClosingState closingState = new ClosingState();
    public final static RunningState runningState = new RunningState();
    public final static StoppingState stoppingState = new StoppingState();

    // 定一个当前电梯状态
    private LiftState liftState;
    public LiftState getLiftState() {
        return liftState;
    }

    public void setLiftState(LiftState liftState) {
        this.liftState = liftState;
        // 把当前的环境通知到各个实现类中
        this.liftState.setContext(this);
    }

    public void open() {
        this.liftState.open();
    }

    public void close() {
        this.liftState.close();
    }

    public void run() {
        this.liftState.run();
    }

    public void stop() {
        this.liftState.stop();
    }
}
```

```java
public class Test {
    public static void main(String[] args) {
        Context context = new Context();
        context.setLiftState(new OpeningState());
        context.open();
        context.close();
        context.run();
        context.stop();
    }
}
```



## 应用

- **主要解决：**  对象的行为依赖于它的状态（属性），并且可以根据它的状态改变而改变它的相关行为。
- **应用场景：**  行为随状态改变而改变的场景、条件/分支语句的代替者
- **注意事项：**  在行为受状态约束的时候使用状态模式，而且状态不超过 5 个