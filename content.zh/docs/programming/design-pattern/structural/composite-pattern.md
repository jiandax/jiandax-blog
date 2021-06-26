---
title: 组合模式
description: Composite Pattern
date: 2021-06-26
draft: false
weight: 6
---

# 组合模式

## 简介

- Composite Pattern
- 将对象组合成树形结构以表示"部分-整体"的层次结构



## 示例

```java
// 节点
public class Employee {
    // 节点属性
    private String name;
    private String dept;
    public Employee(String name, String dept) {
        this.name = name;
        this.dept = dept;
        subEmployees = new ArrayList<>();
    }
    // setter、getter
    // ......


    // 子节点集合
    private List<Employee> subEmployees;
    public List<Employee> getSubEmployees() {
        return subEmployees;
    }
    public void add(Employee employee) {
        subEmployees.add(employee);
    }
    public void remove(Employee employee) {
        subEmployees.remove(employee);
    }
}
```
```java
public class Test {
    public static void main(String[] args) {
        Employee CEO = new Employee("John","CEO");
        Employee headSales = new Employee("Robert","Head Sales");
        Employee headMarketing = new Employee("Michel","Head Marketing");
        Employee clerk = new Employee("Laura","Marketing");
        Employee salesExecutive = new Employee("Richard","Sales");

        CEO.add(headSales);
        CEO.add(headMarketing);
        headSales.add(salesExecutive);
        headMarketing.add(clerk);

        //打印所有雇员
        printEmployee(CEO);
    }

    private static void printEmployee(Employee employee){
        System.out.println(employee);
        for (Employee subEmployee : employee.getSubEmployees()) {
            printEmployee(subEmployee);
        }
    }
}
```



## 应用

- **主要解决：** 树型结构问题
- **何时使用：** 想表达对象的部分整体层次结构时
- **应用场景：** 部分、整体场景，如树形菜单，文件、文件夹的管理
- **注意事项：** 只要是树形结构，就要考虑使用组合模式