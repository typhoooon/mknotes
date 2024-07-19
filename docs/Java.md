# 1
Java：高级语言

特点：
1. 简单
2. 面向对象：封装、继承、多态
3. 多线程
4. 平台无关性

|---|---|---|
|---|---|---|
|JVM |Java Virtual Machine |Java虚拟机|
|JRE |Java Runtime Environment |Java运行环境|
|JDK |Java Development Kit |Java开发环境|


$JVM\subset JRE\subset JDK$

Java开发步骤
1. 编译 源文件(.java) $\to$ 字节码文件(.class)
```
javac filename.java
```
2. 在运行环境上运行 (.class)
```
java Classname
```
#  eclipse
1. 新建Java project，命名
2. 选中scr，右键新建class，命名（大写字母开头）
3. 示例
```java
public class Name{
	public static void main(String[] args){
		System.out.println("Hello World!");
	}
}
```
# 2
## 标识符
命名规则：
1. 由字母、下划线、$、数字组成，长度不受限制
2. 第一个字符不能是数字
3. 不能是关键字
4. 不能是true、false、null
## 基本数据类型

整数类型

| 类型名   | 占用空间        | 取值范围                 |
| ----- | ----------- | -------------------- |
| byte  | 8bit/1byte  | $-2^7\to2^7-1$       |
| short | 16bit/2byte | $-2^{15}\to2^{15}-1$ |
| int   | 32bit/4byte | $-2^{31}\to2^{31}-1$ |
| long  | 64bit/8byte | $-2^{63}\to2^{63}-1$ |
Java中没有无符号的整型

浮点类型

|类型名|占用空间|取值范围|表达方式|
|---|---|---|---|
|float|4byte|8位有效数字|22.76f,1e-12f|
|double|8byte|16位有效数字|22.76d,22.76,0.05,1e-90($1\times 10^{-90}$)|


字符类型
char  2字节
c语言 1字节


布尔类型 boolean
true
false

## 数据类型转换
char\<int\<float\<double
2   4   4   8

小->大，自动类型转换

大->小，强制类型转换

```java
float f=1.22f//f是强制
float f=(float)1.22
```
## 输入输出
```java
//可以用+拼接变量和字符串
System.out.print()
System.out.println()
//自带换行
System.out.printf()//和C语言一样的
```

```java
import java.util.Scanner;
Scanner reader=new Scanner(System.in);
int a = reader.nextInt()
//使用reader对象调用下列方法，读取输入
nextBoolean();
nextByte();
nextShort();
nextInt();
nextLong();
nextFloat();
nextdouble();

```

# 3
数组
```java
int a[],b[];
int [] a,b;
//以上两句等价

int a[]=new int[100];
Scanner r = new Scanner(System.in);
for(int i=0;i<a.length;i++){
	a[i]=r.nextInt();
}
for(int i=0;i<a.length;i++){
	System.out.println(a[i]);
}

```



## 第三章

## 运算符
1. 赋值：=
2. 算术：+-\*/
3. 关系：>,<,>=,<=,!=,==
4. 逻辑：&&, ||, !
5. 复合：+=, -=, \*=, /=, %=
6. 三目：a>b?a=b
7. 自增：++a, a++, a--, --a

## 表达式
算术>关系>逻辑

## 优先级



## 选择语句
	1. 


