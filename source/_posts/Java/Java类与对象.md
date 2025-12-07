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

    现实世界是复杂的。当我们描述“人”这个概念时，会涉及许多具体的属性：男或女、
    老或少、高或矮、胖或瘦；人也有各种行为，比如会跑、会跳、会说话。
    在编程中，我们可以用 int 类型表示人的年龄，用 double 或 float 类型表示身高
    体重，用 String 类型表示性别。但这每一个单独的数据类型，都只能描摹人的一个
    侧面。 它们就像散落的碎片，无法构成一个完整的“人”的概念。
    这就像现实中说一个人是“学霸”，你并不会罗列他语文好、数学好、英语好……“学霸”
    这个词本身，就封装了所有这些构成优秀成绩的具体属性。
    “类”（Class）的引入，正是为了解决这个问题。 当基础数据类型已经不足以完整
    地定义一个复杂事物时，我们就需要“类”这种新的数据类型。它将描述事物所需的
    各种属性（变量）和行为（方法）捆绑在一起，形成一个整体的、可复用的模板，
    从而让我们能够用代码更自然地映射和构建现实世界的复杂实体。类型来。

2. 类与对象的关系

    * 类是抽象的概念，对象是类的实例化
    在面向对象编程中，类（Class）是抽象的概念或模板，而对象（Object）是这个类的
    具体实现或实例。我们可以用“学霸”来比喻：“学霸”这个称谓本身是一个“类”。
    它抽象地定义了一类“学习成绩出色”的人，并不指代任何具体的个体。当你说 
    “张三是学霸” 时，“张三”就成了“学霸”这个类的一个具体“对象”。他是这个概念在现
    实中的一个鲜活实例。
    用计算机语言表速就是：`学霸 张三 = new 学霸()`
    ``` java
    // 定义“学霸”这个类（概念模板）
    class 学霸 {
        // ... 定义构成“学霸”的属性和行为
    }
    // 根据“学霸”这个类，创建出一个具体的对象“张三”
    学霸 张三 = new 学霸();
    ```

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

