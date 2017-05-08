---
date: 2017-04-19 14:49:56+00:00
layout: post
title: Java集合常用类
categories: Emulate
tags: Emulate Java
---

### 目录

1. [集合的结构图](#item1)
2. [集合顶级接口](#item2)
3. [Collection](#item3)
4. [Map](#item4)
5. [集合的存取](#item5)

---
#### <span id="item1">集合结构图</span>
> 集合结构图
```
├── Collection
│   ├── List
│   │   ├── ArrayList
│   │   ├── LinkedList
│   │   └── Vactor
│   └── Set
│       ├── HashSet
│       └── TreeSet
└── Map
    ├── HashMap
    ├── HashTable
    └── TreeMap
```

#### <span id="item2">集合顶级接口</span>
> 集合的两个顶级接口分别为：**Collection** 和 **Map**<br />

#### <span id="item3">Collection</span>
> Collection下有两个比较常用的接口分别是List（列表）和Set（集），其中List可以存储重复元素，元素是有序的（存取顺序一致），可以通过List脚标来获取指定元素；而Set不可以有重复元素，元素是无序的。<br />
> 
> **List接口**：比较常用的类有三个，ArrayList，Vactor，LinkedList
>> * ArrayList：线程不安全的，对元素的查询的速度快。
>> * Vactor：线程安全的，多了一种取出元素的方式：枚举（Enumeration），但已被ArrayList取代。
>> * LinkedList：链表结构，对元素的增删速度很快。
> 
> **Set接口**：比较常用的类右两个，HashSet，TreeSet
>> * HashSet：要保证元素唯一性，需要覆盖掉Object中的equals和hashCode方法（因为底层是通过这两个方法来判断两个元素是否是同一个）。
>> * TreeSet：以二叉树的结构对元素进行存储，可以对元素进行排序。
>>> 排序的两种方式:
>>> 方式1：元素本身具备比较功能，元素实现Comparable接口，覆盖compareTo方法。
>>> 方式2：建立一个比较器，该对象实现Comparator接口，覆盖compare方法，并将该对象作为参数传给TreeSet的构造函数（可以用匿名内部类）。
>>
> 

#### <span id="item4">Map</span>
> Map接口：元素是成对出现的，以键和值的形式体现出来，键要保证唯一性：常见类有，HashMap，HashTable，TreeMap。
>> **HashMap**：线程不安全，允许存放null键和null值。<br />
>> **HashTable**：线程安全的，不允许存放null键和null值。<br />
>> **TreeMap**：可以对键进行排序（要实现排序方法，排序方法同TreeSet）<br />
> 

#### <span id="item5">集合的存取</span>
> **存入集合**
> 
|集合类|存入方式|
|:----|:------|
|Collection|add方法|
|Map|put方法|
> 
> **从集合取出**
> 
|集合类|取出方式|
|:----|:------|
|List|get方法，通过Iterator迭代器|
|Vactor|get方法，通过Iterator迭代器，枚举方式|
|Set|迭代器|
|Map|通过keySet获取键的系列，然后通过该系列的Iterator迭代方式获取元素值|
> 

