---
title: 建造者模式
description: Builder Pattern
date: 2021-06-06
draft: false
weight: 3
---
# 建造者模式
## 简介

- Builder Pattern
- 将一个复杂对象的构建与它的表示分离，使得同样的构建过程可以创建不同的表示。



## 示例

```java
// 被建造的复杂对象
public class House {
	private String baise;
	private String wall;
	private String roofed;
	
    // getter、setter
    //...
}

// 抽象建造者：主要用来指定建造步骤
public abstract class HouseBuilder {
	protected House house = new House();
	//建设房屋的基本方法，建设根基、建设墙、建设屋顶
	public abstract void buildBasic();
	public abstract void buildWalls();
	public abstract void roofed();
	public House buildHouse() {
		return house;
	}
}

// 类似产品类：CommonHouse
public class HighBuilding extends HouseBuilder{
	@Override
	public void buildBasic() {
		System.out.println("高楼地基");
	}
	@Override
	public void buildWalls() {
		System.out.println("高楼墙面");
	}
	@Override
	public void roofed() {
		System.out.println("高楼屋顶");
	}
}

// 指挥类
public class HouseDirector {
	HouseBuilder houseBuilder = null;
	
    // 构造器创建bilder对象
	public HouseDirector(HouseBuilder houseBuilder) {
		this.houseBuilder = houseBuilder;
	}

	// 建造房屋的流程交给指挥者
	public House constructHouse() {
		houseBuilder.buildBasic();
		houseBuilder.buildWalls();
		houseBuilder.roofed();
		return houseBuilder.buildHouse();
	}
}
```



## 应用

- **主要解决** 
  - 软件系统中，一个复杂对象的创建，通常由各个部分的子对象用一定的算法构成。
  - 由于需求的变化，各子部分经常面临着剧烈的变化，但是将它们组合在一起的算法却相对稳定。
- **何时使用** 
  - 一些基本部件不会变，而其组合经常变化的时候。
- **应用实例**
  - 去肯德基，汉堡、可乐、薯条、炸鸡翅等是不变的，而其组合是经常变化的，生成出所谓的"套餐"。 
  - JAVA 中的 StringBuilder
- **注意事项**
  - 与工厂模式的区别是：建造者模式更加关注与零件装配的顺序
