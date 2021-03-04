---
title: Java常用类
updated: '`r format(Sys.time(), ''%d %B, %Y'')`'
tags:
  - java笔记
  - java基础
categories:
  - java
  - 笔记
top_img: 'https://cdn.jsdelivr.net/gh/zerohk/blogpic@pics/img/class_top.jpeg'
cover: 'https://cdn.jsdelivr.net/gh/zerohk/blogpic@pics/img/class_cover.jpeg'
abbrlink: 3742615103
date: 2021-03-04 12:06:53
sticky:
password:
abstract:
message:
wrong_pass_message:
wrong_hash_message:
keywords:
description:
comments:
toc:
toc_number:
auto_open:
copyright:
copyright_author:
copyright_author_href:
copyright_url:
copyright_info:
mathjax:
katex:
aplayer:
highlight_shrink:
---

# Scanner类

## 功能

可以实现键盘输入数据到程序中。

### 引用类型的一般使用步骤：

#### 1、导包：

​	`import 包路径.类名称`

​	如果需要使用的目标类和当前类位于同一个包，则可以省略导包语句。只有java.lang包下的内容不需要导包，其他的包都需要import语句

#### 2、创建：

​	`类名称 对象名 = new 类名称(参数列表);`

#### 3、使用：

​	对象名.成员方法名()

## 使用

- 导包：`import java.util.Scanner`

- 构造方法：`Scanner sc = new Scanner(System.in);//没有无参构造，参数System.in表示从键盘读取输入`

- 成员方法：
	- `sc.nextInt();//读入键盘输入的整数值`
	- `sc.next();//读入键盘输入的字符串`

## 代码演示

### 1.求和

> 键盘录入两个数据并求和

```java
package cn.shenzc.java;
import java.util.Scanner;
public class ScannerSum {
    public static void main(String[] args) {
        System.out.println("请输入第一个整数：");
        Scanner sc = new Scanner(System.in);
        int a = sc.nextInt();
        System.out.println("请输入第二个整数：");
        int b = sc.nextInt();
        int sum = a + b;
        System.out.println(a + "+" + b + "的和是：" + sum);
    }
}
```

![image-20210301224741217](https://cdn.jsdelivr.net/gh/zerohk/blogpic@pics/img/image-20210301224741217.png)

### 2.求三个数中最大值

> 键盘录入三个数据并获取最大值

```java
package cn.shenzc.java;

import java.util.Scanner;

public class MaxInThree {
    public static void main(String[] args) {
        Scanner sc = new Scanner(System.in);
        System.out.println("请输入第一个数：");
        int a = sc.nextInt();
        System.out.println("请输入第二个数：");
        int b = sc.nextInt();
        System.out.println("请输入第三个数：");
        int c = sc.nextInt();
        int max = (a > b) ? a : b;
        max = (max > c) ? max : c;
        System.out.println("最大值是:" + max);
    }
}
```

![image-20210301224959292](https://cdn.jsdelivr.net/gh/zerohk/blogpic@pics/img/image-20210301224959292.png)

# 匿名对象

## 概念

创建对象时，只有创建对象的语句，却没有把对象地址值赋值给某个变量。虽然是创建对象的简化写法，但是应用
场景非常有限。

## 格式

```java
new 类名(参数列表);
```

比如：`new Scanner(System.in);`

## 应用场景

1. 创建匿名对象直接调用方法，没有变量名。

	```java
	new Scanner(System.in).nextInt();
	```

2. 一旦调用两次方法，就是创建了两个对象，造成浪费，请看如下代码。

	```java
	new Scanner(System.in).nextInt();
	new Scanner(System.in).nextInt();
	```

	> 一个匿名对象，只能使用一次。

3. 匿名对象可以作为方法的参数和返回值。

	- 作为参数

		```java
		class Test {
		public static void main(String[] args) {
		// 普通方式
		Scanner sc = new Scanner(System.in);
		input(sc);
		//匿名对象作为方法接收的参数
		input(new Scanner(System.in));
		}
		public static void input(Scanner sc){
		System.out.println(sc);
		}
		}
		```

		![image-20210301230616695](https://cdn.jsdelivr.net/gh/zerohk/blogpic@pics/img/image-20210301230616695.png)

	- 作为返回值

		```java
		class Test2 {
		public static void main(String[] args) {
		// 普通方式
		Scanner sc = getScanner();
		}
		public static Scanner getScanner(){
		//普通方式
		//Scanner sc = new Scanner(System.in);
		//return sc;
		//匿名对象作为方法返回值
		return new Scanner(System.in);
		}
		}
		```

		![image-20210301231514922](https://cdn.jsdelivr.net/gh/zerohk/blogpic@pics/img/image-20210301231514922.png)

	

# Random类

## 功能

此类的实例用于生成伪随机数。

## 使用

- 导包：`import java.util.Random`

- 构造方法：

	- `public Random()`:

	- `public Random(long seed)`:同一种子生成随机数是一样的

- 成员方法：

	- `public int nextInt()`:返回伪随机整数。
	- `public int nextInt(int n)`:返回一个伪随机数，范围在0（包括）和指定值n（不包括）之间的
		int 值。

## 代码演示

### 1.生成三个十以内的整数

```java
package cn.shenzc.java;

import java.util.Random;

public class TestRandom2 {
    public static void main(String[] args) {
        Random random = new Random();
//        System.out.println("第一个十以内随机整数" + random.nextInt(10)) ;
//        System.out.println("第二个十以内随机整数" + random.nextInt(10)) ;
//        System.out.println("第三个十以内随机整数" + random.nextInt(10)) ;
        for(int i = 1;i <= 3;i++) {
            System.out.println("第" + i + "个十以内随机整数:" + random.nextInt(10));
        }
    }
}
```

![image-20210303202621072](https://cdn.jsdelivr.net/gh/zerohk/blogpic@pics/img/image-20210303202621072.png)

### 2.猜数字小游戏

> 游戏开始时，会随机生成一个1-100之间的整数`number` 。玩家猜测一个数字`guessNumber` ，会与`number`作比
> 较，系统提示大了或者小了，直到玩家猜中，游戏结束。

```java
package cn.shenzc.java;

import java.util.Random;
import java.util.Scanner;

public class TestRandom3 {
    public static void main(String[] args) {
        //生成一个随机数
        Random random = new Random();
        int number = random.nextInt(100) + 1;
        System.out.println("生成的随机数是:" + number);

        Scanner sc = new Scanner(System.in);
        int guessNumber;
        while (true) {
            System.out.println("请输入你认为的数字:");
            guessNumber = sc.nextInt();
            // 如果用户猜测小于随机数
            if (guessNumber < number) {
                System.out.println("你猜的数小了。");
                continue;
            }
            // 如果用户猜测大于随机数
            if (guessNumber > number) {
                System.out.println("你猜的数大了。");
                continue;
            }
            // 如果用户猜测等于随机数
            if (guessNumber == number) break;
        }
        System.out.println("恭喜你，猜对了！");
    }
}
```

![image-20210303205932148](https://cdn.jsdelivr.net/gh/zerohk/blogpic@pics/img/image-20210303205932148.png)

# ArrayList集合类

## 引入---对象数组

使用学生数组，存储三个学生对象，代码如下：

```java
// Student
package cn.shenzc.java;

public class Student {
    private String name;
    private int age;

    public Student() {
    }

    public Student(String name, int age) {
        this.name = name;
        this.age = age;
    }

    public void setName(String name) {
        this.name = name;
    }

    public void setAge(int age) {
        this.age = age;
    }

    public String getName() {
        return name;
    }

    public int getAge() {
        return age;
    }
}

```

```java
package cn.shenzc.java;

public class ObjectArray {
    public static void main(String[] args) {
        Student s1 = new Student("刘备",18);
        Student s2 = new Student("关羽",19);
        Student s3 = new Student("张飞",20);

        Student[] students = new Student[3];
        students[0] = s1;
        students[1] = s2;
        students[2] = s3;

        for(int i = 0;i < students.length;i++) {
            System.out.println(students[i].getName() + "---" + students[i].getAge());
        }
    }
}
```

![image-20210303212335559](https://cdn.jsdelivr.net/gh/zerohk/blogpic@pics/img/image-20210303212335559.png)

到目前为止，我们想存储对象数据，选择的容器，只有对象数组。而数组的长度是固定的，无法适应数据变化的需
求。为了解决这个问题，Java提供了另一个容器`java.util.ArrayList` 集合类,让我们可以更便捷的存储和操作对
象数据。

## 什么是ArrayList

`java.util.ArrayList` 是大小可变的数组的实现，存储在内的数据称为元素。此类提供一些方法来操作内部存储的元素。  ArrayList 中可不断添加元素，其大小也自动增长。

数组的长度不可以发生改变，但是ArrayList集合的长度是可以随意变化的。

![Screenshot_20200624_164629](https://cdn.jsdelivr.net/gh/zerohk/blogpic@pics/img/Screenshot_20200624_164629.png)

上图的 `<E>` 表示泛型。

泛型只能是**引用类型**，不能是基础类型。

泛型就是定义一种模板，例如`ArrayList<T>`，然后在代码中为用到的类创建对应的`ArrayList<类型>`

```java
public class ArrayList<T> {
    private T[] array;
    private int size;
    public void add(T e) {...}
    public void remove(int index) {...}
    public T get(int index) {...}
}
```

```java
// 创建可以存储String的ArrayList:
ArrayList<String> strList = new ArrayList<String>();
// 创建可以存储Float的ArrayList:
ArrayList<Float> floatList = new ArrayList<Float>();
// 创建可以存储Person的ArrayList:
ArrayList<Person> personList = new ArrayList<Person>();
```

对于ArrayList来说，直接打印得到的不是地址值，而是其中的内容；如果ArrayList为空，则得到的是:**[]**

## 使用

- 导包：`java.util.ArrayList`
- 构造方法：`public ArrayList() `
	- `ArrayList<E> list = new ArrayList<E>();`
	- 在JDK 7后,右侧泛型的尖括号之内可以留空，但是<>仍然要写。简化格式：
		- `ArrayList<E> list = new ArrayList<>();`
- 成员方法：见下

## 常用方法

### 方法定义

`public boolean add(E e):`向集合中添加元素。参数类型和泛型一致。

​		**对于ArrayList的add方法来说，添加元素一定是成功的，返回值可用可不用，但是对于其他集合来说，添加元素不一定成功**

`public E  get(int index):`从集合中获取元素，参数是索引编号。

`public E  remove(int index):`从集合中删除元素。

`public int size():`获取集合的尺寸长度，返回值时集合中元素个数。

### 代码演示

```java
package cn.shenzc.java;

import java.util.ArrayList;

public class TestArrayList2 {
    public static void main(String[] args) {
        ArrayList<String> list = new ArrayList<>();
        // 添加元素
        list.add("Java");
        list.add("is");
        list.add("interesting");
        list.add("interesting");
        for (String s : list) {
            System.out.println(s);
        }
        // 获取集合大小
        int size = list.size();
        System.out.println(size);

        // 删除元素
        String rmStr = list.remove(0);
        System.out.println(rmStr);
        // 获取集合大小
        size = list.size();
        System.out.println(size);

        // 获取索引元素
        System.out.println(list.get(1));
    }
}
```

![image-20210303221044643](https://cdn.jsdelivr.net/gh/zerohk/blogpic@pics/img/image-20210303221044643.png)

## 如何存储基本数据类型

ArrayList对象不能存储基本类型，只能存储引用类型的数据。类似<int> 不能写，但是存储基本数据类型对应的
包装类型是可以的。所以，想要存储基本类型数据， <> 中的数据类型，必须转换后才能编写，转换写法如下：

| 基本类型 | 基本包装类型 |
| :------: | :----------: |
|   byte   |     Byte     |
|  short   |    Short     |
|   int    |   Integer    |
|   char   |  Character   |
|   long   |     Long     |
|  float   |    Float     |
|  double  |    Double    |
| boolean  |   Boolean    |

## 代码演示

### 1.数值添加到集合

> 生成6个1~33之间的随机整数,添加到集合,并遍历

```java
package cn.shenzc.java;

import java.util.ArrayList;
import java.util.Random;

public class TestArrayList3 {
    public static void main(String[] args) {
        // 生成6个1-33的随机整数，并添加到集合
        Random random = new Random();
        ArrayList<Integer> numbers = new ArrayList<>();
        int number;
        for (int i = 0; i < 6; i++) {
            number = random.nextInt(33) + 1;
            numbers.add(number);
        }

        // 遍历集合
        for (Integer num : numbers) {
            System.out.println(num);
        }
    }
}
```

![image-20210304113328560](https://cdn.jsdelivr.net/gh/zerohk/blogpic@pics/img/image-20210304113328560.png)

### 2.对象添加到集合

> 自定义4个学生对象,添加到集合,并遍历

```java
package cn.shenzc.java;

import java.util.ArrayList;

public class TestArrayList4 {
    public static void main(String[] args) {
        // 自定义4个学生对象
        Student s1 = new Student("唐僧", 18);
        Student s2 = new Student("孙悟空", 500);
        Student s3 = new Student("猪八戒", 1500);
        Student s4 = new Student("沙和尚", 800);

        // 创建ArrayList
        ArrayList<Student> students = new ArrayList<>();
        students.add(s1);
        students.add(s2);
        students.add(s3);
        students.add(s4);

        // 遍历集合
        for (Student student : students) {
            System.out.println(student.getName() + "---" + student.getAge());
        }
    }
}

```

![image-20210304113830425](https://cdn.jsdelivr.net/gh/zerohk/blogpic@pics/img/image-20210304113830425-1614831522073.png)