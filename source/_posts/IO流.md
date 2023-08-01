---
title: I/O流
tags: Java
cover: https://raw.githubusercontent.com/czlifetime/img/master/Java.png
---

# I/O流

## 文件

### 概念

1、文件

保存数据的地方

2、 文件流

+ 流：数据在数据源(文件)和程序(内存)之间的路径
+ 输入流：将磁盘中的文件写入内存
+ 输出流：将内存中的内容写入磁盘

### 文件操作

+ 创建文件对象相关的构造器和方法
  + `new File(String pathname)`根据路径创建一个File对象
  + `new File(File parent,String chil)`根据父目录文件+子路径构建
  + `new File(String parent,String child)`根据父目录+子路径构建
  + createNewFile创建新文件
+ 获取文件的相关信息
  + getName、getAbsolutePath、getParent、length、exists、isFile、isDirectory
+ 目录操作和文件删除
  + 创建一级目录：mkdir
  + 创建多级目录：mkdirs
  + 删除空目录或文件：delete

## IO流原理及流的分类

+ Java IO原理

  1. IO流是input、output的缩写，用于处理数据传输，如读写文件、网络通信
  2. 在Java程序中，对于数据的输入。输出以“流(stream)”的方式进行
  3. java.io包下提供了各种“流”的类和接口，用于获取不同种类的数据，并通过方法输入或输出数据

+ 流的分类

  1. 操作数据单元：字节流、字符流

  2. 数据流的流向：输入流、输出流

  3. 流的角色：节点流、处理流(字符流)

     ![](https://raw.githubusercontent.com/czlifetime/img/master/img//img/IO%E6%B5%81%E5%A4%A7%E7%BA%B2.png)

## *输入流

### InputStream

#### FileInputStream

![](https://raw.githubusercontent.com/czlifetime/img/master/FileInputStream.png)

### Reader(字节输入流)

+ 关系图

![](https://raw.githubusercontent.com/czlifetime/img/master/FileReader关系图.png)

#### FileReader

1. 相关方法
   + `new FileReader(File/String)`
   + `read`:每次读取单个字符，返回该字符，如果到文件末尾，返回-1
   + `read(char[])`:批量读取多个字符到数组，返回读取到的字符数，如果到文件末尾，返回-1
2. 相关API
   + `new String(char[])`:将char[]转成String
   + `new String(char[],off,len)`:将char []的指定部分转换成String

## *输出流

### OutputStream(字节)

#### FileOutputStream

![](https://raw.githubusercontent.com/czlifetime/img/master/FileInputStream.png)

#### ObjectOutputStream

### Writer(字符)

#### FileWriter

1. 常用方法
   + new FileWriter(File/String):覆盖模式，相当于流的指针在首段
   + new FileWriter(File/String,true):追加模式，相当于流的指针在尾端
   + write(int):写入单个字符
   + write(char[]):写入指定数组
   + write(char[],off,len):写入指定数组的指定部分
   + writer(string):写入指定字符串
   + writer(string,off,len):写入指定字符串放入指定部分
2. 相关API
   + String类
   + toCharArray:将String转换成char[]

![](https://raw.githubusercontent.com/czlifetime/img/master/FileWriter关系图.png)

+ 注意：FileWriter使用后，必须关闭(close)或刷新(flush)，否则写入不到指定文件

#### OutputStreamWriter

### 节点流和处理流

1. 节点流可以从一个特定的数据源读取数据，如FileReader、FileWriter
   + 文件节点流：FileInputStream、FileOutputStream、FileReader、FileWriter
   + 数组节点流：ByteArrayInputStream、ByteArrayOutStream、CharAttayReader、CharArrayWriter
   + 访问管道、访问字符流
2. 处理流(包装流)是"连接"在已存在的流(节点流或处理流)之上，为程序提供更为强大的读写功能，更加灵活，如BufferedReader、BufferedWriter
3. 节点流与处理流的区别与联系
   + 节点流是底层流/低级流，直接跟数据源相接
   + 处理流包含节点流，及可以消除不同节点流的实现差异，也可以提供更方便的方法来完成输入输出
   + 处理流对节点流进行包装，使用了修饰器设计模式，不会直接与数据源相连

![](https://raw.githubusercontent.com/czlifetime/img/master/字节流与处理流.png)

4. 标准输入输出流

   |                    | 类型(编译类型) | 类型(运行类型)      | 默认设备 |
   | ------------------ | -------------- | ------------------- | -------- |
   | System.in标准输入  | InputStream    | BufferedInputStream | 键盘     |
   | System.out标准输出 | PrintStream    | PrintStream         | 显示器   |

5. 转换流-InputStreamReader和OutputStreamWriter

   + 解决文件乱码问题

6. 打印流-PrintStream和PrintWriter

   + 打印流只有输出流
   + PrintStream(字节流)
   + PrintWriter(字符流)

### 序列化与反序列化

1. 序列化：在保存数据时，保存数据的值和数据类型
2. 反序列化：在恢复数据时，恢复数据的值和数据类型
3. 需要让某个对象支持序列化机制，则必须让其类是可序列化的(实现接口：Serializable或Externalizable)
   + Serializable:标记接口，没有方法
   + Externalizable:该接口有方法需要实现



##Properties类

1. 专门用于读取配置文件的的集合类
   + 配置文件格式：键=值
2. 注意：键值对不需要有空格，值不需要用引号括起来。默认类型是String
3. 常见方法：
   + load：加载配置文件的键值对到Properties对象
   + list：将数据显示到指定设备
   + getProperty(key):根据键获取值
   + setProperty(key,value):设置键值对到Properties对象
   + store:将Properties中的键值对存储到配置文件中，在idea中，保存信息到配置文件，如果含有中文，会存储为UNICode码

作用：存储和读取数据

I：input

O：output

流：像水流一样传输数据

## IO流的分类

![](https://github.com/czlifetime/img/blob/1.0/img/IO流.png?raw=true)

![](https://raw.githubusercontent.com/czlifetime/img/master/字节流.png)

### 字节流

#### FileOutputStream

操作本地文件的字节输出流，可以把程序中的数据写到本地文件中

```java
public class ByteStreamText{
    public static void main(String[] args) throws IOException{ //抛出异常
        //步骤：
        //1.创建对象
        FileOutputStream fos = new FileOutputStream("myio\\a.txt")//创建对象的路径
        //2.写出数据
        fos.write(97);
        //3.释放资源
        fos.close();
    }
}
```

运行结果：a

+ 创建对象细节：
  + 参数是字符串表示的路径或者是File对象都是可以的
  + 如果文件不存在会创建一个新的文件，但是要保证父级路径是存在的。
  + 如果文件已经存在,则会清空文件
+ 写出数据细节：
  + write方法的参数是整数，但是实际上写到本地文件中的是整数在ASCII上对应的字符
+ 释放资源细节：
  + 每次使用完流之后都要释放资源

```java
void write(int b)						//一次写一个字节数据
void write(byte[] b)					//一次写一个字节数组数据
void write(byte[] b,int off,int len)	//一次写一个字节数组的部分数据
```

#### FileInputStream

操作本地文件的字节输入流，可以把本地文件中的数据读取到程序中来

```java
public class ByteStreamText{
    public static void main(String[] args) throws FileNotException{
        //步骤：
        //1.创建对象
        FileInputStream fis = new FileInputStream("myio\\a.txt");
        //2.读取数据
        int b1 = fis.read();
        System.out.println(b1);
        //3.释放资源
        fis.close();
    }
}
```

+ 创建对象细节：如果文件不存在，直接报错

+ 读取数据细节：

  + 一次读取一个字节，读出来的就是数据在ASCII上对应的数字
  + 读到文件末尾，read方法返回-1

+ 释放资源细节：每次使用完流之后都要释放资源

  

#### 字节输入流循环读取

```````java
import java.io.FileInputStream;
import java.io.IOException;

public class ByteStreamText{
    public static void main(String[] args) throws IOException{
        FileInputStream fis = new FileInputStream("myio\\a.tet");
        int b;
        while((b = fis.read()) != -1){
            System.out.println((char)b);
        }
        fis.close();
    }
}
```````

#### 文件拷贝

```java
import java.io.FileInputStream;
import java.io.FileNotFoundException;
import java.io.FileOutputStream;

public class BytestreamText{
    public static void main(String[] args) throws FileNotFoundException{
        FileInputStream fis = new FileInputStream("D:\\原路径.mp4");
        FileOutStream fos = new FileOutputStream();
    }
 }
```

