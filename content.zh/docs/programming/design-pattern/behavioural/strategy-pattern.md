---
title: 策略模式
description: Strategy Pattern
date: 2021-07-02
draft: false
weight: 2
---



# 策略模式

## 简介

- Strategy Pattern
- 定义了一组算法，将每个算法都封装起来，并且使它们之间可以互换



## 示例

业务场景：获取多种数据库的元数据

```java
public interface DatabaseMeta {
    void getColumns();
}

// 类似策略类：PgsqlDatabaseMeta、OracleDatabaseMeta
public class MysqlDatabaseMeta implements DatabaseMeta {
    @Override
    public void getColumns() {
        System.out.println("Mysql column...");
    }
}
```

```java
// 上下文
public class Context {
    private DatabaseMeta meta;
    public Context(DatabaseMeta meta) {
        this.meta = meta;
    }

    public void getColumns() {
        meta.getColumns();
    }
}
```

```java
public class Test {
    public static void main(String[] args) {
        Context context;
        context = new Context(new MysqlDatabaseMeta());
        context.getColumns();

        context = new Context(new PgsqlDatabaseMeta());
        context.getColumns();

        context = new Context(new OracleDatabaseMeta());
        context.getColumns();
    }
}
```



## 应用

- **主要解决：**  在有多种相似算法的情况下，使用if/else所带来的复杂和难以维护的问题
- **应用场景：**  
  - 许多相关的类仅仅是行为有异
  - 需要使用一个算法的不同变体
  - 一个类定义了多种行为，并且这些行为以多个条件语句的形式出现
- **注意事项：**  
  - 如果策略类多于四个，就需要考虑使用混合模式，防止策略类膨胀