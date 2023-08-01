---
title: Java面向对象编程
tags: Java
data: 2023-7-31 17:50
cover: https://cdn.jsdelivr.net/gh/czlifetime/img/Java_cover.jpg
---

## 方法

### 什么是方法

+ 方法是程序中最小的执行单元
+ 方法的定义：把一些代码打包在一起

### 方法的格式

```java
public static 返回值类型 方法名（参数）{
    方法体
        return 0；
}
```



### 方法的重载

+ 在同一个类中，定义多个同名的方法
+ 每个方法都有不同的参数类型或参数个数，同名的方法之间就构成了重载关系

```java
public static void rus(int a,int b){
    
}
public static void rus(int a,int b,int c){
    
}
```



### 方法的内存

##### Java内存分配

1. 栈

+ 方法运行时使用的内存，方法进栈运行，运行完毕出栈（先进后出）
+ 变量

2. 堆

+ new出来，并产生地址

3. 方法区：字节码文件加载是进入的内存
4. 本地方法栈
5. 寄存器

## 构造方法

## 1.构造方法有什么作用？

构造方法是一个比较特殊的方法，通过构造方法可以`完成对象的创建，以及实例变量的初始化`。
换句话说：构造方法是用来`创建对象，并且同时给对象的属性赋值`。
**注意**：实例变量没有手动赋值的时候，系统会赋默认值。

## 2.构造方法怎么定义，语法是什么？

```java
[修饰符列表] 构造方法名(形式参数列表){
	构造方法体;
	通常在构造方法体当中给属性赋值，完成属性的初始化。
}

```

**注意：**

1. 第一：修饰符列表目前统一写：`public`。千万不要写public static。
2. 第二：构造方法名和`类名`必须`一致`。
3. 第三：构造方法`不需要`指定`返回值类型`，也不能写void，写上void表示普通方法，就不是构造方法了。

普通方法的语法结构是？

```java
	[修饰符列表] 返回值类型 方法名(形式参数列表){
		方法体;
	}
```

## 3.构造方法怎么调用，使用哪个运算符？

使用`new`运算符来调用构造方法。

## 标准的JavaBean类

1. 类名需要见名知意
2. 成员变量使用private修饰
3. 提供至少两个构造方法
   + 无参构造方法
   + 带全部参数的构造方法

4. 成员方法
   + 提供每一个成员变量对应的`setXxx()/getXxx()`
   + 如果还有其他行为，也需要写上

## 字符串

### String概述

`java.lang.String`类代表字符串，Java程序中所有的字符串文字都为此类

### 注意点

字符串的内容是不会发生改变的，他的对象在创建后不能被改变

### 创建String对象的两种方式

1. 直接赋值

2. 通过new关键字，使用不同的构造方法

   | 构造方法                       | 说明                             |
   | ------------------------------ | -------------------------------- |
   | public String ()               | 创建空白字符串，不含任何内容     |
   | public String(String original) | 根据传入的字符串，创建字符串对象 |
   | public String(char[] chs)      | 根据字符数组，创建字符串对象     |
   | public String (byte[] chs)     | 根据字节数组，创建字符串对象     |

   

3. 字符串赋值

   当双引号直接赋值时，系统会检查该字符串在串池中是否存在

   + 不存在：创建新的
   + 存在：复用

### 字符串比较

1. 比的到底是啥

   + 基本数据类型->数据值
   + 引用数据类型->地址值

2. 比较方法

   + `boolen equal(要比较的字符串)`完全一样结果才是true，否则为false

   + `boolen equalslgnoreCase(要比较的字符串)`忽略大小写的比较

     ```Java
     package CS408;
     
     public class StingText {
         public static void main(String[] args){
             
             String s = new String("abc");
             String s1 = "abc";
     
             boolean rus1 = s1.equals(s);
             boolean rus2 = s1.equalsIgnoreCase(s);
             System.out.print(rus1 + " "+ rus2);
             
         }
     
     }
     ```

     运行：true true

   + 如果

     ```java
     package CS408;
     
     import java.util.Scanner;
     public class StingText {
         public static void main(String[] args){
             Scanner sc  = new Scanner(System.in);
             System.out.print("请输入一个字符串：");
             String str1 = sc.next();//.next()的核心是new出来的
     
             String str2  = "abc";
     
             System.out.print(str1 == str2);
     
         }
     
     }
     
     ```

     `请输入一个字符串：abc
     false
     进程已结束,退出代码0`

### StringBuilder

是一个容器，创建后里面的内容可变

+ 作用：提高字符串的操作效率

#### StringBuilder构造方法

+ `public StringBuilder append () `     添加数据并返回数据本身

+ `public StringBuilder reverse()`     翻转容器中的内容

+ `public int length()`           返回长度

+ `public String toString()`通过toString就可以实现把StringBuilder转换成String

  ```java
  package CS408;
  
  public class StringBuilderText {
      public static void main(String[] args){
          //1. 创建对象
           StringBuilder sb = new StringBuilder("abc");
  
           //2.添加元素
          sb.append(1);
  
          //3.翻转
          sb.reverse();
  
          //4.长度
          sb.length();
  
          //5.将StringBuilder变成字符串
          String str = sb.toString();
          
  
          System.out.println(sb);
      }
  }
  
  ```

  

### 链式编程

当在调用一个方法时，不需要用变量接受他的结果，可以调用其他方法

```java
package CS408;

import java.util.Scanner;
public class lianshibiancheng {
    public static void main(String[] args){
        String s = getString();
        int len = getString().length();
    }

    public static String getString() {
        Scanner sc = new Scanner(System.in);
        System.out.print("请输入一个字符串");
        String str = sc.next();
        return str;
    }
}
```

### `StringJoiner`

##Static

+ 表示静态，是Java中的一个修饰符，可以修饰成员方法，成员变量

+ 被static修饰的成员变量(静态变量)

  1. 特点：
     + 被该类所有对象共享

  2. 调用方式：
     + 类名调用
     + 对象名调用

+ 被static修饰的成员方法(静态方法)

  1. 特点：
     + 多用在测试类，工具类中(注：测试类：用来检查其他的类是否书写正确，带有main方法的类，是程序的入口。工具类：不是用来描述一类事物的，而是帮助我们做一些事情的类。)
     + JavaBean类中很少


    2. 调用方式：
       + 类名调用
       + 对象名调用

+ 注意事项：
  + 静态方法只能访问静态变量和静态方法
  + 非静态方法可以访问所有
  + 静态方法中没用this关键字

## 继承

+ Java中提供一个关键字extends

  `public class Student extends person{}`

+ 好处：

  1. 可以把多个子类中重复的代码抽取到父类中，提高代码的复用性
  2. 子类可以在父类的基础上，增加其他的功能，使子类更强大

+ 特点：支持单继承，不支持多继承，但支持多层继承（每一个类都直接或间接的继承于Object）

![](https://cdn.jsdelivr.net/gh/czlifetime/img/%E5%AD%90%E7%B1%BB%E7%BB%A7%E6%89%BF%E7%88%B6%E7%B1%BB%E4%B8%AD%E7%9A%84%E5%86%85%E5%AE%B9.png)

+ 父类的构造方法不能被子类继承

+ 成员变量：private要有对应的set与get方法

+ 只用父类中的虚方法表才能被子类继承

  

### 成员变量的访问特点

1. 就近原则：谁离我近，我就用谁
2. 如果出现重名：
   + `name`从局部位置开始找
   + `this.name`从本类成员位置开始往上
   + `super.name`从父类成员位置开始往上

### 方法重写

+ 当父类中的方法不能满足子类现在的需求时，需要进行方法重写（子类中的成员方法与父类中的成员方法名一样时）
+ 要写上`@Override`重写注解,检验子类重写时语法是否正确

### 方法重写的本质

+ 将传递中虚方法表中的父类中的方法进行覆盖

### 注意事项

1. 重写方法的名称、形参列表必须与父类中的一致。
2. 子类重写父类方法时，访问权限子类必须大于等于父类（暂时了解∶空着不写<protected < public
3. 子类重写父类方法时，返回值类型子类必须小于等于父类

4. 建议:重写的方法尽量和父类保持一致。
5. 只有被添加到虚方法表中的方法才能被重写

### 继承中，构造方法的访问特点

+ 父类中的构造方法不会被子类继承
+ 子类中所有的构造方法默认先访问父类中的无参构造，在执行自己
+ 调用方式：super()

## 多态

+ 同类型的对象，表现出的不同形态

1. 多态的表现形式：`父类类型 对象名称 = 子类对象`

2. 多态的前提
   + 有继承关系
   + 有父类引用指向子类对象
   + 有方法重写

```java
package CS408.polymorphism;

public class Person {
    private String name;
    private int age;

    public Person() {

    }

    public Person(String name, int age) {
        this.name = name;
        this.age = age;
    }

    public String getName() {
        return name;
    }

    public void setName(String name) {
        this.name = name;
    }

    public int getAge() {
        return age;
    }

    public void setAge(int age) {
        this.age = age;
    }
    public void Show(){
        System.out.println("name" + name +"age" + age);
    }
}

```

```java
package CS408.polymorphism;

public class Student extends Person{

    @Override
    public void Show(){
        System.out.println("学生的信息为：" + getName() + getAge());
    }
}

```

```
package CS408.polymorphism;

public class Teacher extends Person{
    @Override
    public void Show(){
        System.out.println("老师的信息为：" + getName() + getAge());
    }

}
```

```
package CS408.polymorphism;

public class Administrator extends Person{
    @Override
    public void Show(){
        System.out.println("管理员的信息为：" + getName() + getAge());
    }
}
```

```
package CS408.polymorphism;

public class Text {
    public static void main(String[] args) {
        Student s = new Student();
        Teacher t = new Teacher();
        Administrator a = new Administrator();
        s.setAge(19);
        s.setName("张三");
        t.setAge(29);
        t.setName("李老师");
        a.setAge(39);
        a.setName("李管理");


        register(s);
        register(t);
        register(a);
    }
    public static void register(Person P){
        P.Show();
    }
}
```

### 多态调用成员的特点

+ 调用成员变量：编译看左边，运行看左边
+ 调用成员方法：编译看左边，运行看右边

### 多态的优势

+ 在多态的形式下，右边的对象可以实现解耦合，便于拓展和维护
+ 定义方法的时候，使用父类型作为菜蔬，可以接受所有子类对象，体现多态的拓展性与遍历

### 多态的弊端

+ 不能调用子类特有的功能

+ 解决方法:变回子类类型

  `Dog d = (Dog) a;`

### 弊端的解决方法

+ 自动类型转换
+ 强制类型转换
  + 可以转换成真正的子类类型，从而调用子类独有的功能
  + 转换类型与真实对象类型不一致会报错
  + 转换时用`instanceof`关键字进行判断

多态的综合练习: https://www.bilibili.com/video/BV17F411T7Ao?t=17.7&p=132

## final

+ 方法：表明该方法是最终方法，不能被重写
+ 类：表明该类是最终类，不能被继承
+ 变量：常量，只能被赋值一次
  + 修改基本数据类型：记录的值不能发生改变
  + 修改引用数据类型：记录的地址值不能发生改变，内部的属性值还是可以改变的

final练习：https://www.bilibili.com/video/BV17F411T7Ao?t=2216.7&p=133及学生管理系统

## 代码块

+ 局部代码块

```java
punlic class Text{
    public static void main(){
        {
            int a = 10;
            System.out.print(a);
        }
    }
}
```

作用：提前结束变量的生命周期

+ 构造代码块

```java
public class Student{
    private String name;
    private int age;
    {
        System.out.println("开始创建对象了");
    }
    public Student(){
        
    }
    public Student (String name ,int age){
        this.name = name;
        this.age = age;
    }
}
```

1. 构造代码块：写在成员位置的代码块
2. 作用：可以把多个构造方法中重复的代码抽取出来
3. 执行时机：先执行构造代码块再执行构造方法

+ 静态代码块
  1. 格式:`static{}`
  2. 特点：需要通过static关键字修饰，随着累的加载而加载，并且自动触发，只执行一次
  3. 使用场景：在类的加载中，做数据的初始化使用

https://www.bilibili.com/video/BV17F411T7Ao?t=1866.9&p=134学生管理系统

## 抽象类

+ 作用：抽取共性时，无法确定方法体，就把方法定义为抽象的。强制让子类按照某种格式重写。抽象方法所在的类，必须是抽象类。
+ 抽象方法：将共性的行为抽取到父类之后。将共性的行为(方法）抽取到父类之后。由于每一个子类执行的内容是不一样,所以，在父类中不能确定具体的方法体。该方法就可以定义为抽象方法。
+ 抽象类：如果一个类中存在抽象方法，那么该类就必须声明为抽象类

###定义格式

+ 抽象方法：`public abstract 返回值类型 方法名（参数列表）； `
+ 抽象类：`public abstract class 类名{}`

###抽象类和抽象方法注意事项

+ 抽象类不能创建对象
+ 抽象类中不一定有抽象方法，有抽象方法的类一定是抽象类
+ 抽象类可以有构造方法

## 接口

+ 是一种规则，是对行为的抽象

### 如何定义一个接口

+ `public interface 接口名{}`

+ 不能实例化->不能new

+ 接口与类是实现关系，通过implements关键字表示

  + 接口与类是实现关系，可以单实现，也可以多实现

    `public class 类名 implements 接口名1，接口名2{}`

  + 实现类可以继承一个类的同时实现多个接口

    `public class 类名extends implement 接口名1，接口名2{}`

+ 接口的子类（实现类）

  + 要么重写接口中的所用抽象方法，要么是抽象类

### 如何使用一个接口

````java
package CS408.InterfaceText;

public abstract class animal {
    private String name;
    private int age;

    public animal() {
    }

    public animal(String name,int age){
        this.age = age;
        this.name = name;
    }
    public String getName() {
        return name;
    }

    public void setName(String name) {
        this.name = name;
    }

    public int getAge() {
        return age;
    }

    public void setAge(int age) {
        this.age = age;
    }
    public abstract void eat();
}

````

```java
package CS408.InterfaceText;

public interface swim {
    public abstract void swim();
}

```

```java
package CS408.InterfaceText;

public class Rabbit extends animal{

    public Rabbit() {
    }

    public Rabbit(String name, int age) {
        super(name, age);
    }

    @Override
    public void eat() {
        System.out.println("兔子在吃胡萝卜");
    }
}

```

```java
package CS408.InterfaceText;

public class Dog extends animal implements swim{
    public Dog() {
    }
    public Dog(String name,int age){
        super(name, age);
    }
    @Override
    public void eat() {
        System.out.println("小狗在吃骨头");
    }

    @Override
    public void swim() {
        System.out.println("小狗在狗刨");
    }
}

```

```java
package CS408.InterfaceText;

public class Frog extends animal implements swim{

    public Frog() {
    }

    public Frog(String name, int age) {
        super(name, age);
    }

    @Override
    public void eat() {
        System.out.println("青蛙在吃虫子");
    }

    @Override
    public void swim() {
        System.out.println("青蛙在蛙泳");
    }
}

```

```java
package CS408.InterfaceText;

public class Text {
    public static void main(String[] args){
        Frog f = new Frog("呱呱",1);
        System.out.println(f.getAge()+ "," + f.getName());
        f.eat();
        f.swim();

        Rabbit ra = new Rabbit("小白",3);
        System.out.println(ra.getAge()+ "," + ra.getName());
        ra.eat();
    }
}

```

运行：

```java
1,呱呱
青蛙在吃虫子
青蛙在蛙泳
3,小白
兔子在吃胡萝卜
```

### 接口中成员的特点

+ 成员变量
  + 只能是常量
  + 默认修饰符：`public static final`

+ 构造方法
  + 没有
+ 成员方法
  + 只是抽象方法

### 接口和类之间的关系

+ 类与接口的关系
  + 继承关系，只能单继承，不能多继承，但是可以多层继承
+ 接口与类的关系
+ 接口与接口的关系
  + 继承关系，可以单继承，也可以多继承
    + 如果实现类实现了最下面的字接口，就需要重写所有的抽象方法

### 练习

+ 编写带有接口和抽象类的标准`Javabean`类

+ 我们现在有乒乓球运动员和篮球运动员，乒乓球教练和篮球教练。为了出国交流，跟乒乓球相关的人员都需要学习英语。
  请用所有知识分析，在这个案例中，哪些是具体类，哪些是抽象类，哪些是接口?

+ 乒乓球运动员:姓名，年龄，学打乒乓球，说英语
  篮球运动员:姓名，年龄，学打篮球
  乒乓球教练:姓名，年龄，教打乒乓球，说英语

  篮球教练:姓名，年龄，教打篮球

+ ![](https://cdn.jsdelivr.net/gh/czlifetime/img/%E9%9D%A2%E5%90%91%E5%AF%B9%E8%B1%A1Text%E6%80%9D%E8%B7%AF1.png)

+ ![](https://cdn.jsdelivr.net/gh/czlifetime/img/%E9%9D%A2%E5%90%91%E5%AF%B9%E8%B1%A1Text%E6%80%9D%E8%B7%AF2.png)

  + ```java
    package CS408.OopText;
    
    public class Person {
        private String name;
        private int age;
    
        public Person() {
        }
    
        public Person(String name, int age) {
            this.name = name;
            this.age = age;
        }
    
        public String getName() {
            return name;
        }
    
        public void setName(String name) {
            this.name = name;
        }
    
        public int getAge() {
            return age;
        }
    
        public void setAge(int age) {
            this.age = age;
        }
    
    }
    
    ```

  + ```java
    package CS408.OopText;
    
    public abstract class Athlete extends Person {
        public Athlete() {
        }
        public Athlete(String name,int age) {
            super(name,age);
        }
    
        public abstract void study();
    
    }
    
    ```

  + ```java 
    package CS408.OopText;
    
    public abstract class Coach extends Person{
        public Coach() {
        }
    
        public Coach(String name, int age) {
            super(name, age);
        }
    
        public abstract void teach();
    }
    
    ```

  + ```java
    package CS408.OopText;
    
    public class PingpangAthlete extends Athlete implements English{
        public PingpangAthlete() {
        }
    
        public PingpangAthlete(String name, int age) {
            super(name, age);
        }
    
        @Override
        public void study(){
            System.out.println("乒乓球运动员学打乒乓球");
    
        }
        @Override
        public void english(){
            System.out.println("乒乓球运动员学英语");
    
        }
    }
    
    ```

  + ```java
    package CS408.OopText;
    
    public class BasketballAthlete extends Athlete{
        public BasketballAthlete() {
        }
    
        public BasketballAthlete(String name, int age) {
            super(name, age);
        }
        public void study(){
            System.out.println("篮球运动员在学打篮球");
        }
    }
    
    ```

  + ```java
    package CS408.OopText;
    
    public class BasketballCoach extends Coach{
        public BasketballCoach() {
        }
    
        public BasketballCoach(String name, int age) {
            super(name, age);
        }
        public void teach(){
            System.out.println("篮球教练在教打篮球");
        }
    }
    
    ```

  + ```java
    package CS408.OopText;
    
    public interface English {
        public abstract void english();
    }
    
    ```

  + ```java
    package CS408.OopText;
    
    public class Text {
        public static void main(String[] args) {
            PingpangAthlete ppa = new PingpangAthlete("小花",20);
            ppa.study();
            ppa.english();
    
            BasketballAthlete ba = new BasketballAthlete("姚明", 24);
        }
    }
    ```

### 其他接口方法

https://www.bilibili.com/video/BV17F411T7Ao?p=139

## 内部类

+ 在类的里面再定义一个类，这个类教内部类
+ 内部类的访问特点
  + 内部类可以直接访问外部类的成员，包括私有
  + 外部类要访问内部类的成员必须创建对象

### 内部类的分类

+ 成员内部类
  + 写在成员位置，属于外部类成员
+ 静态内部类
+ 局部内部类
+ 匿名内部类
  + 本质：隐藏了名字的内部类
    + 格式：`new 类名或者接口名（）{重写方法}`
  + 包含三个关系：继承\实现，方法重写，创建对象

