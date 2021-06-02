---
title: "JDK8 新特性"
date: 2021-01-01T01:01:01+09:00
description: 
enableToc: true
draft: false
---

# Java8 流

## 创建流

```java
String[] array = {"a", "b", "c"};
Path pathObj = Paths.get("filePath");
Collection<String> collection = Lists.newArrayList();
SecureRandom random = SecureRandom.getInstanceStrong();

// 序列
Stream.of("a", "b", "c");

// 数组
Arrays.stream(array);

// 集合
collection.stream();

// 文件
Files.lines(pathObj);
Files.list(pathObj);

// 函数        
Stream.iterate(0, n -> n + 3).limit(10);
Stream.generate(random::nextInt).limit(10);
Stream.generate(() -> (int) (System.nanoTime() % 100)).limit(10);
```



## 中间操作

```java
Stream<User> stream = Stream.of(new User());

// 排序（反序）
stream.sorted();
stream.sorted(Comparator.comparing(User::getAge).reversed());

// 筛选
stream.filter(User::isMale);

// 去重
stream.distinct();

// 截断
stream.limit(10);

// 跳过
stream.skip(10);

// 映射
stream.map(User::getName);

// 流扁平化
stream.map(User::getName).map(s -> s.split("")).flatMap(Arrays::stream);
```



## 终端操作

```java
Stream<Integer> stream = Stream.of(1, 2, 3, 4, 5);

// 匹配
stream.anyMatch(n -> n == 5);           // 是否有一个元素匹配
stream.allMatch(n -> n == 5);           // 是否全部元素都匹配
stream.noneMatch(n -> n == 5);          // 是否全部元素都不匹配

// 查找
stream.findAny();                       // 查找任意元素
stream.findFirst();                     // 查找第一个元素

// 归约
stream.reduce(Integer::sum);            // 求和
stream.reduce(Integer::min);            // 最小值
stream.reduce(Integer::max);            // 最大值
stream.reduce(1, (n1, n2) -> n1 * n2);  // 从1开始，连乘元素

// 统计格式
stream.count();
// 遍历
stream.forEach(System.out::println);

// 收集
stream.collect(Collectors.toList());                        // List<T>
stream.collect(Collectors.toSet());                         // Set<T>
stream.collect(Collectors.toMap(String::valueOf, n -> "")); // Map<String,String>
stream.collect(Collectors.groupingBy(String::valueOf));     // Map<String,List<T>>，分组
```



## 数值流

```java
IntStream stream;
Stream<User> objStream = Stream.of(new User());

// 由数值范围创建
stream = IntStream.range(1, 100);        //不包含结束值100
stream = IntStream.rangeClosed(1, 100);  //包含结束值100

// 由对象流映射
stream = objStream.mapToInt(User::getAge);

// 聚合函数
stream.sum();
stream.min();
stream.max();
stream.count();

// 转换回对象流
stream.boxed();
```

