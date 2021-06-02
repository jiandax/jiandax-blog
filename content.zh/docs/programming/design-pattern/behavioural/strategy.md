---
title: "策略模式"
description: "Strategy"
date: 2021-01-24T00:04:41+08:00
enableToc: true
draft: false
weight: 1
---

# 概述

- Strategy
- 定义一组算法，将每个算法都封装起来，并且使他们可相互替换



# 应用

- 主要解决：在有多种相似算法的情况下，使用if/else所带来的复杂和难以维护的问题



# 优点

- 算法可以自由切换
- 避免使用多重条件判断
- 扩展性良好



# 缺点

- 策略类会增多
- 所有策略类都需要对外暴露



# 注意事项

- 策略类不应多于四个，防止策略类膨胀



# 代码示例

业务场景：获取多种数据库的元数据

- 公共接口

  ```java
  public interface DatabaseMeta{
      void getColumns();
  }
  ```

- 策略类

  ```java
  // Mysql
  public class MysqlDatabaseMeta implements DatabaseMeta{
      @Override
      public void getColumns() {
          System.out.println("Mysql column...");
      }
  }
  
  // Pgsql
  public class PgsqlDatabaseMeta implements DatabaseMeta{
      @Override
      public void getColumns() {
          System.out.println("Pgsql column...");
      }
  }
  
  // Oracle
  public class OracleDatabaseMeta implements DatabaseMeta{
      @Override
      public void getColumns() {
          System.out.println("Oracle column...");
      }
  }
  ```

- 上下文

  ```java
  public class Context{
      private DatabaseMeta meta;
      public Context(DatabaseMeta meta){
          this.meta=meta;
      }
      public void getColumns(){
          meta.getColumns();
      }
  }
  ```

- 测试类

  ```java
  public class Test {
      public static void main(String[] args) {
          Context context;
          context=new Context(new MysqlDatabaseMeta());
          context.getColumns();
  
          context=new Context(new PgsqlDatabaseMeta());
          context.getColumns();
  
          context=new Context(new OracleDatabaseMeta());
          context.getColumns();
      }
  }
  ```

  



