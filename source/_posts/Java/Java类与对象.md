---
title: Java类与对象
tags:
  - Java
  - 类与对象
categories:
  - Code
keywords: 'java, 类与对象'
description: 详细介绍 Java 类与对象相关的概念
abbrlink: 4dffdbe9
date: 2025-12-07 20:24:58
updated: 2025-12-07 20:24:58
top_img:
cover:
series:
---

## 类与对象中的关键字

| 关键字 | 释义 | 作用 |
| :----- | :--- | :--- |
| class | 类 | 申明类的关键字 |
| new | 新建 | 创建新对象的关键字 |
| this | 这个 | 表示引用当前对象 |
| super | 超级 | 父类的引用 |
| extends | 继承 | 建立类之间继承的关键字 |
| static | 静态的 | 修饰符，表明变量的属性是静态的，"不可变"的 |
| private | 私有的 | 修饰符，表明变量的属性是私有的，不可被其他类访问的 |
| protected | 受保护的 | 修饰符，表明变量的属性半公开的，同包和子类可访问 |
| public | 公开的 | 修饰符，表明变量的属性是公开的，可被任意访问 |
| package | 包 | 命名空间，贴标签，可以理解为现实的班级划分，用于区分一班的张三，二班的张三 |
| import | 导入 | 用于导入其他的包 |

## 类与对象的概念

1. 类是一种抽象的概念

    现实世界是复杂的，比如要描述*人*这个概念，人有男人、女人，有老、幼，有高、矮、胖、瘦,
    人还会跑、会跳、会说话，我们能用 (int)整形定义**人的年龄**，用(double、float)浮点型定
    义**人的身高体重**，用(String)字符串类型定义**人的性别**，但是我们不能每次要表示人的时
    候都写前面一大串就像你要说一个人学习好，你不会说他语文好、数学好、英语好，而是直接说他
    是学霸，类就是这么来的，基础数据类型已经不足以用来定义一个物质的完整概念时，引入类这个
    新的数据类型来描述一个复杂的事物

2. 类与对象的关系

    * 类是抽象的概念，对象是类的实例化
    比如学霸就是一个类，是一个概念，是学习好的一类人的统称，不指向具体的哪一个人。
    比如张三学习好，我们说张三是学霸，这时候张三就是学霸这个类的具体的一个对象。
    用计算机语言表速就是：`学霸 张三 = new 学霸()`

## 类的基本语法

1. 基础结构

    ``` java
    //定义类
    [修饰符] class 类名 {
        // 字段/成员变量
        [修饰符] 基础数据类型 变量名;
        // 构造方法,方法名与类名一致的方法，只在new一个对象时调用
        [修饰符] 类名（参数）{
            // 初始化代码
        }
        // 成员方法
        [修饰符] 返回类型 方法名（参数）{
            //方法体
        }
    }
    ```
2. 示例

    ``` java
    //公开的  类  圆 
    public class Circle {
        // 成员变量
        // 私有的 浮点型 半径
        private double Radius;

        // 构造方法1,将半径设为 0
        public Circle () {
            this.Radius = 0;
        }
        //构造方法2, 创建对象时设置半径
        public Circle (double r) {
            this.Radius = r;
        }

        // 定义三个方法
        // 获取圆的面积
        public double getArea() {
            return r * r * 3.14;
        }
        // 获取圆的周长
        public double getPerimeter() {
            return 2 * r * 3.14
        }
        // 输出
        public void show() {
            System.out.println("周长:" + getPerimeter + "\n面积:" + getArea)
        }
        public void main(String[] args) {
            //新建一个对象 circle1, 调用无参数的构造方法1
            Circle circle1 = new Circle()
            //新建一个对象 circle2, 设置半径为 2.0, 调用构造方法2
            Circle circle2 = new Circle(2.0)

            // 调用 Circle 类的 show 方法
            circle1.show();
            circle2.show();
        }
    }
    ```

## 构造函数

1. 构造函数特点

  * 与类同名
  * 没有返回类型
  * 在创建对象时自动调用
  * 可以有多个（重载）

2. 构造函数类型

    ``` java
    public class Student {
        private String name;
        private int score;
    
        // 1. 默认构造方法（无参数）
        public Student() {
            this.name = "未知";
            this.score = 0;
        }
        // 2. 带参数构造方法
        public Student(String name) {
            this.name = name;
            this.score = 0;
        }
        // 3. 全参数构造方法
        public Student(String name, int score) {
            this.name = name;
            this.score = score;
        }
        // 4. 拷贝构造方法
        public Student(Student other) {
            this.name = other.name;
            this.score = other.score;
        }
    }
    ```

## 继承

1. 继承的基本概念

    * 子类继承父类的属性和方法
    * 实现代码复用
    * Java只支持单继承
    ``` java
    //父类 
    上面的圆类
    //子类
    public class 
    .......待完成........

