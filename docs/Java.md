# Java Notes

## 第一章 初识Java

### 1. Java：高级语言

三大版本

1. JavaSE：标准版，用来做电脑上运行的软件

2. JavaEE：企业版，用来做网站

3. JavaME：微型版，用来做手机软件


### 2. Java特点：

1. 简单

2. 面向对象：封装、继承、多态

3. 多线程

4. 平台无关性

| 简写 | 全称                     | 意思         |
|------|--------------------------|--------------|
| JVM  | Java Virtual Machine     | Java虚拟机   |
| JRE  | Java Runtime Environment | Java运行环境 |
| JDK  | Java Development Kit     | Java开发环境 |


$JVM\subset JRE\subset JDK$

### Java开发步骤

1. 编译 源文件(.java) $\to$ 字节码文件(.class)
```
javac filename.java
```
2. 在运行环境上运行 (.class)
```
java Classname
```
### eclipse

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

## 第二章 基本数据类型与数组

### 标识符

命名规则：

1. 由字母、下划线、`$`、数字组成，长度不受限制

2. 第一个字符不能是数字

3. 不能是关键字

4. 不能是`true`、`false`、`null`

### 基本数据类型

* 整数类型

| 类型名 | 占用空间    | 取值范围             |
| -----  | ----------- | -------------------- |
| byte   | 8bit/1byte  | $-2^7\to2^7-1$       |
| short  | 16bit/2byte | $-2^{15}\to2^{15}-1$ |
| int    | 32bit/4byte | $-2^{31}\to2^{31}-1$ |
| long   | 64bit/8byte | $-2^{63}\to2^{63}-1$ |

Java中没有无符号的整型

* 浮点类型

| 类型名 | 占用空间 | 取值范围     | 表达方式                                        |
|--------|----------|--------------|-------------------------------------------------|
| float  | 4byte    | 8位有效数字  | 22.76f, 1e-12f                                  |
| double | 8byte    | 16位有效数字 | 22.76d, 22.76, 0.05 , 1e-90($1\times 10^{-90}$) |


* 字符类型
char  2字节

*c语言的char是 1字节*


* 布尔类型 boolean

true
false

### 数据类型转换
1. 大小比较

char < int < float < double

2 <  4 < 4 < 8

2. 自动类型转化

从低精度到高精度转，最小只能只能转到`int`

3. 强制类型转化

从高精度到低精度转：类型 变量 = （类型）转化的数或变量

小->大，自动类型转换

大->小，强制类型转换

```java
int a = (int) 3.14;

float f=1.22f//f是强制类型转换
float f=(float)1.22
```

### 输入输出
```java
//可以用+拼接变量和字符串
System.out.print()
System.out.println()
//自带换行
System.out.printf()//和C语言的printf一样的
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

### 数组

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

## 第三章 运算符、表达式和语句

### 运算符

1. 赋值：`=`

2. 算术：`+-\*/`

3. 关系：`>,<,>=,<=,!=,==`

4. 逻辑：`&&, ||, !`

5. 复合：`+=, -=, \*=, /=, %=`

6. 三目：`a>b?a=b`

7. 自增：`++a, a++, a--, --a`

### 表达式

1. 算术表达式：用算术运算符和变量（操作数）组合起来的式子，如a + b， a - b

2. 关系表达式：用关系运算符和变量（操作数）组合起来的式子，如a > b， a! = b

3. 逻辑表达式：用逻辑运算符和变量（操作数）组合起来的式子，如a && b， a || b

### 优先级

算术 > 关系 > 逻辑

### 语句
#### 选择语句
1. `if`语句（单分支选择结构）
```java
if(表达式){
    语句; //若表达式成立（表达式为true），则执行语句
}
```

2. `if`-`else`语句（双分支选择结构）
```java
if(表达式){
    语句 1 ; //若表达式成立（表达式为true），则执行语句 1
}
else{
    语句 2 ; //若不成立，则执行语句 2
}
```

3. `if` -`else if` - `else`语句 （多分支选择结构）

```java
if(表达式 1 ){
    语句 1 ; //若表达式 1 成立（表达式为true），则执行语句 1
}
else if(表达式 2 ){
    语句 2 ; //若表达式 2 成立（表达式为true），则执行语句 2
}
else if(表达式 3 ){
    语句 3 ; //若表达式 3 成立（表达式为true），则执行语句 3
}
......
else{
    语句n; //若不成立，则执行语句n
}
```

4. switch 语句
```java
switch(表达式){
    case 常量 1 : 语句 1 ; break;
    case 常量 2 : 语句 2 ; break;
    case 常量 3 : 语句 3 ; break;
    ...
    default: 语句n;
}
```

#### 循环语句
**我并不认为把这几种类型的翻译名称记下来是一件多么高明的事情**

1. while语句（当型循环）
```java
while(表达式){
    语句;  //若表达式成立（表达式为true），则进入循环，执行语句
}
```

2. do while语句（直到型循环）
```java
do{
    语句； //先执行语句，再判断表达式是否成立，若表达式成立,则进入循环
}while(表达式);
```

3. for语句（计数型循环）
```java
for(表达式 1 ; 表达式 2 ; 表达式 3 ){ 
//表达式 1 ：循环的起点；表达式 2 ：循环的终点； 表达 式 3 ：循环的过程
    语句 4 ; //执行过程：1243243243243243.....
}
```

#### 其他语句

* break 语句
1. 用于switch中，结束某一分支的执行
2. 用于循环语句中，结束本重循环

* continue 语句
1. 用于循环体中，结束本次循环，开始下一次循环


## 补充章 方法(函数)

### 1. 方法的定义
```java
方法类型 方法名称(形式参数){
    方法体
    return 表达式;
}
```
注意：
1. 方法类型和 return 的表达式一致
2. 方法类型决定了返回值类型

### 2. 方法的调用
```java
 (方法类型 返回值名) = 方法名称(实际参数);
```

### 3. 方法的分类

#### 1. 无参数无返回值
```java
//方法的定义
void sum(){
    int a = 3 ;
    int b = 5 ;
    int res = a + b;
    System.out.println("a + b = " + res );
}
//方法的调用
sum();
```

#### 2. 无参数有返回值
```java
    int sum(){
    int a = 3 ;
    int b = 5 ;
    int res = a + b;
    return res;
}
//方法的调用
int s = sum();
```

#### 3. 有参数无返回值

```java
void sum(int a, int b){
    int res = a + b;
    System.out.println("a + b = " + res);
}
//方法的调用
sum( 3 , 5 );
```

#### 4. 有参数有返回值

```java
//方法的定义
void sum(int a, int b){
    int res = a + b;
    System.out.println("a + b = " + res);
}
//方法的调用
sum(3, 5);
```

## 第四章 类与对象

### 1. 类：是对象的抽象
```java
class 类名{
    共有属性 -> 成员变量
    对属性的操作 -> 成员方法
}

class Circle{
    double radius;  //成员变量
    double getArea(){  //成员方法
        return 3.14 * radius * radius;
    }
}
```

### 2. this关键字

作用：使用被隐藏的**成员变量**

用法：`this.成员变量`

### 3. 对象的创建

`类名 对象名 = new 类名()`

```java
Circle cc = new Circle();
Scanner rr = new Scanner(System.in);
```

通过对象调用成员变量：`cc.radius = 100`

通过对象调用成员方法：`double area = cc.getArea()`

### 4. 类的UML图

分为三层：

1. 最顶层 放 **类名**

2. 中间层 放 **成员变量**
                       
3. 最底层 放 **成员方法**

### 5. 方法的重载

定义：

1. 成员方法 名相同

2. 成员方法的参数 个数或类型不同

```java
//第一种
int sum(int a, int b){
    return a + b;
}

//第二种
float sum(float a, float b){
    return a + b;
}

//第三种
int sum(int a, int b, int c){
    return a + b + c;
}

//第四种
double sum(int a, float b, double c){
    return a + b + c;
}
```

### 6. 构造方法

定义：是类中的一种特殊方法，是在创建对象的时候调用构造方法

构造方法的**重点**

1. 构造方法名与类名一致

2. 构造方法没有方法类型，即没有返回值

* 默认构造方法 ==> 由系统给定 Circle(){ }
* 自定义构造方法 ==> 类名(形式参数)

 （如果要自定义构造方法，那就把默认构造方法要一起加上去）
```java
class Circle{
    double radius;  //成员变量
    
    //默认构造方法
    Circle(){ }
    
    //自定义构造方法
    Cirlce(double r){
        this.radius = r;
    }
    
    double getArea(){  //成员方法
        return 3.14 * radius * radius;
    }
}

//使用构造方法创建对象
Circle cc1 = new Circle();
Circle cc2 = new Cirlce(6.66);
```

构造方法的作用： 初始化成员变量，开辟内存空间


### 7. 对象的引用和实体

1. 声明对象
 
`Circle cc; `

2. 为声明的对象分配内存

`cc = new Circle();`

**重点： cc (对象)是一个引用**

3. 对象的实体

```java
Circle cc1 = new Circle();
Circle cc2 = new Circle();
cc1 = cc2; //cc1和cc2具有相同的实体
```

### 8. 类与程序的结构

* Java程序从主类的 main 开始运行

* 当一个源文件中有多个类时，有且只有一个`public`类，且文件的名称与`public`类名称一致

* 一个源文件编译后产生一个字节码文件

### 9. 对象的组合

* 依赖关系

    定义：A类中的成员方法的参数是B类的对象，称为A依赖于B

* 关联关系

    定义：A类中的成员变量是B类的对象，称为对象的组合

### 10. 实例成员和类成员

* 实例成员变量和类成员变量

    1. 实例成员变量：普通的成员变量

    2. 类成员变量：成员变量前加`static` $\to$ 静态变量

* 实例成员方法和类成员方法

    1. 实例成员方法：普通的成员方法

    2. 类成员方法：成员方法前加`static` $\to$ 静态方法

* 实例成员和类成员的访问形式

    1. 实例成员访问：*只能*通过 `对象.成员变量` 或者 `对象.成员方法`

    2. 类成员访问：可以通过 `对象.类变量` 或者 `对象.类方法`
还可以通过 `类名.类变量` 或者 `类名.类方法`

### 11. 访问权限

1. 公有的：`public` 无条件对外开放，同包不同包都可见

2. 私有的：`private` 不对外开放，同包不同包都不可见

3. 受保护的：`protected` 有条件对外开放，同包可见，不同包不可见

4. 友好的： `缺省的` 有条件对外开放，同包可见，不同包不可见


### 12. getter方法和setter方法

#### getter 方法

作用：用于获取对象的私有属性的数值

命名规范：以 get 开头，后面跟着属性名（首字母大写）

```java
public class Person {
    private String name;
    
    public String getName() {
        return this.name;
    }
}
//getName()方法用于获取 name 属性的值。
```

#### setter 方法

作用：用于设置对象的私有属性的数值

命名规范：以 set 开头，后面跟着属性名（首字母大写）

```java
public class Person {
    private String name;
    
    public void setName(String name) {
        this.name = name;
    }
}
// setName(String name) 方法用于设置 name 属性的值
```

## 第五章 子类与继承

### 1. 继承

```java
class 子类名称 extends 父类名称{
    1. 成员变量
        * 父类那里继承过来的
        * 自己独有的
    2. 成员方法
        * 父类那里继承过来的
        * 自己独有的
}
```

### 2. 成员的可继承性

1. public $\to$ 同包继承，不同包也继承

2. private $\to$ 同包不同包都不可继承

3. protected $\to$ 同包可继承，不同包也可继承

4. 缺省的 $\to$  同包可继承，不同包不可继承

### 3. 成员的覆盖

* 成员变量的覆盖

    子类的成员变量和父类的成员变量名字一样

* 成员方法的覆盖

    子类的成员方法和父类的成员方法名字一样，参数的个数和参数类型也都一样

    **重点：方法的覆盖也被称为方法重写（`override`）**

### 4. super关键字

来源：由于继承关系，子类覆盖了父类中的同名成员变量或者成员方法，因此，想要访问父类中的成
员，需要使用`super`关键字。

```java
//1. 调用父类成员变量
super.父类成员变量

//2. 调用父类成员方法
super.父类成员方法(实参)

//3. 调用父类的无参构造方法
super()

//4. 调用父类的有参构造方法
super(实参)
```

### 5. 子类的生成过程

示例 类：Student

```java
Student s = new Student();
```
1. 使用`new`运算符创建子类对象`s`时，调用的是子类的构造方法；

2. 子类的构造方法总是先调用父类的构造方法；

3. 父类的成员变量初始化，申请内存空间；

4. 子类的成员变量初始化，申请内存空间

### 6. final关键字

1. 修饰**类**：这个类不能被继承

2. 修饰**成员变量**，这个成员变量不能被修改

3. 修饰**成员方法**，这个成员方法不能被重写

### 7. 上转型对象

* 示例

    父类：Parent

    子类：Child

```java
Child c = new Child();
Parent p = c; //子类的对象赋值给父类的变量
```

p就被称为上转型对象

* 上转型对象的特点：

    1. 上转型兑现更只能访问父类的成员变量和成员方法，不能访问子类新增的成员变量和成员方法

    2. **子类重写了父类的某个方法，上转型对象调用子类的重写方法**

### 8. 继承中的多态

定义：同一个方法呈现不同的行为或者状态

产生过程：

1. 继承，子类继承了父类

2. 方法的重写，子类重写了父类继承过来的方法

3. 对象的上转型

因此，**上转型对象调用子类的重写方法 $\to$ 多态**

```java
//父类

class Animal{
    public void makeSound(){
        System.out.println("dididi");
    }
}

//子类
class Cat extends Animal{
    public void makeSound(){
        System.out.println("喵喵喵");
    }
}

class Dog extends Animal{
    public void makeSound(){
        System.out.println("汪汪汪");
    }
}

//主类
public class Main{
    public static void main(String[] args){
        //对象的向上转型
        Cat c = new Cat(); //子类的对象
        Animal a;  //父类的变量
        a = c; //子类的对象赋值给父类的变量
        a.makeSound(); //上转型对象调用子类的重写方法：喵喵喵
        
        Dog d = new Dog();
        a = d;
        a.makeSound(); //上转型对象调用子类的重写方法：汪汪汪
    }
}
```

### 9. 抽象类与抽象方法

关键字：`abstract`

**抽象方法**：用`abstract`修饰，只有方法头，没有方法体

抽象方法的特点：只许声明，不许实现

```java
public abstract void sum();
```
**抽象类** ：在`class`的前面加上`abstract`来修饰

抽象类的特点：

1. 抽象类中一定有抽象方法

2. 抽象类不能创建对象，即不能`new`

3. 抽象类中可以有非抽象方法

4. 非抽象子类必须重写抽象类中的抽象方法



## 第六章 接口与多态

### 1. 接口的声明
```java
interface 接口名称{
    1. 成员变量
        默认会加上 public static final
    2. 成员方法
        默认会加上 public abstract
}
```

### 2. 接口的实现

```java
class 类名 implements 接口名称{

    重写接口中的所有成员方法

}
```

### 3. 接口与抽象类的比较

* 相同点

1. 接口与抽象类都有抽象（`abstarct`）方法

2. 接口与抽象类都不能创建对象，即不能`new`

* 不同点

1. 抽象类当中可以有非抽象（`abstract`）方法，而接口中只能有`abstract`方法和静态变量

2. 接口里面的方法都是`public`的，而抽象类里面的方法不一定是

3. 实现类可以实现多个接口，而子类只能继承单个抽象类

### 4. 接口的回调

定义：实现类的对象赋值给接口变量


```java
interface Person{  //Person称为接口
    // 成员变量
    // 成员方法
}

//实现类
class Student implements Person{  //Student成为实现类
    //重写Person接口中的所有成员方法
}

Person p;                   //接口的变量
Student s = new Student();  //实现类的对象
p = s;                      //接口回调
```

### 5. 接口中的多态

定义：同一个方法呈现不同的行为或者状态

产生过程：

1. 实现类实现了某个接口

2. 实现类重写了接口中的抽象方法

3. 接口的回调（实现类的对象赋值给接口变量）

因此，**接口变量调用实现类的重写方法**

```java
//接口
interface Animal{
    public abstract void makeSound();  //抽象方法
}

//实现类：Dog
class Dog implements Animal{
    public void makeSound(){
        System.out.println("狗狗，汪汪汪！");
    }
}

//实现类：Cat
class Cat implements Animal{
    public void makeSound(){
        System.out.println("猫猫，喵喵喵！");
    }
}

//主类:Main
public class Main{
    public static void main(String[] args){
        Animal a; //接口变量
        Dog dog = new Dog();  //实现类的对象
        a = dog;  //接口回调
        a.makeSound();  //多态
        
        Cat cat = new Cat();  //实现类的对象
        a = cat;  //接口回调
        a.makeSound();  //多态
    }
}
```





# 第七章 内部类与异常类

## 1. 内部类

### 内部类是指定义在一个类内部的类。

### 内部类的特点：

### 1. 内部类可以直接访问外部类的成员变量和成员方法

### 2. 内部类只能由外部类的对象进行创建

```java
//外部类
class OutClass{
    //成员变量
    private int outValue = 10;
    //成员方法
    public void outMethod(){
        System.out.println("我是外部类的方法");
    }
    //内部类
    public class InClass{
        public void inMethod() {
            //内部类访问外部类的成员变量
            System.out.println("我是内部类里的方法, 外部类的成员变量的值是："+ outValue);
            //内部类访问外部类的成员方法
            outMethod();
        }
    }
}

//主类
public class Task {
    public static void main(String[] args) {
        OutClass out = new OutClass(); //创建外部类的对象
        OutClass.InClass in = out.new InClass();  //外部类的对象创建内部类的对象
        in.inMethod();
    }
}
```

### 2. 匿名类

匿名类是指一个子类的类体来创建一个对象

匿名类的**特点**：

1. 匿名类是子类或者实现类

2. 匿名类创建对象时使用父类的构造方法

3. 匿名类无法声明变量

```java
//继承中的匿名类
abstract class Dad{
    abstract void MakeMoney();
}

public class Niming {
    public static void main(String[] args) {  //子类的类体
        Dad dad = new Dad(){
            void MakeMoney() {
                System.out.println("写代码");
            }
        };
        dad.MakeMoney();
    }
}

//接口中的匿名类
interface Speakable{
    void sayHello();
}

//主类
public class Task {
    public static void main(String[] args) {
        Speakable p1 = new Speakable() { //实现类的类体
            public void sayHello() {
                System.out.println("你好");
            }
        };
        p1.sayHello();
    }
}
```


### 3. 异常类

异常：程序运行时可能出现的一些错误

异常处理机制：
```java
try{
    //可能会发生异常的代码
}
catch(Exception e){
    //异常处理
}
```

`finally`子语句

```java
try{
    //可能会发生异常的代码
}
catch(Exception e){
    //异常处理
}
finally{
    //不管报没报错，这里的语句一定会执行
}
```

* 自定义的异常类

原因：程序在遇到某些特殊的业务逻辑时，能够抛出异常，这样可以统一异常处理流程

编写流程：

1. 继承`Exception`类来编写自定义的异常类

2. 在可能发生异常的方法声明中用关键字`throws`抛出自定义的异常类

3. 使用`throw`抛出自定义异常类的对象

4. 在调用异常方法时，使用`try-catch`来捕获可能产生的异常


## 第八章 常用实用类(String类)

### 1. 构造方法

```java
//1.利用字符串构造

String string1 = new String("hello");
System.out.println("string1 = " + string1);

//2.利用字符串的对象构造
String string2 = new String(string1);
System.out.println("string2 = " + string2);

//3.利用字符数组进行构造
char c[] = {'w', 'o', 'r', 'l', 'd'};
String string3 = new String(c);
System.out.println("string3 = " + string3);

//4. 直接赋值
String string4 = "hello world";
```

### 2. 常用方法

```java
public boolean equals(String str):          //功能是比较两个字符串对象的内容是否相等
public int length():                        //功能是返回字符串的长度
public char charAt(int index):              //功能是返回字符串中指定索引处的字符
public String substring(int beginIndex, int endIndex)://功能是返回从beginIndex到endIndex之间的子字符串（不包括endIndex）
public String concat(String str):           //功能是将指定字符串连接到该字符串的末尾
public String toLowerCase():                //功能是将字符串转换为小写
public String toUpperCase():                //功能是将字符串转换为大写
public String trim():                       //功能是去除字符串首尾的空白字符
public int indexOf(String str):             //功能是返回指定子字符串在字符串中第一次出现的索引
public int lastIndexOf(String str):         //功能是返回指定子字符串在字符串中最后一次出现的索引
public boolean startsWith(String prefix):   //功能是判断字符串是否以指定前缀开头
public char[] toCharArray():                //功能是用于将字符串转换为字符数组
public byte[] getBytes():                   //功能是将字符串转换为字节数组
```

### 3. 与其他类型的转换

1. 与基本数据类型之间的互相转化
```java
float f = Float.parseFloat("123.456")           //将字符串转单精度浮点型
String s = String.valueOf(123.456);             //将单精度浮点型转字符串

int i = Integer.parseInt("123")                 //将字符串转整型
String s = String.valueOf( 123 );               //将整型转字符串

double d = Double.parseDouble("123.456789")     //将字符串转双精度浮点型
String s = String.valueOf(123.456789);          //将双精度浮点型转字符串
```

2. 与类（对象）之间的互相转化

    所有类的祖先类是`Object`

    `Object`类有一个`toString()`方法，可获得对象的字符串表示。

    `Object`类的子类可以重写`toString()`方法

### 4. 正则表达式

作用：用于字符串的匹配

```java
\\d //代表0-9之间的任意一个数字
\\D //代表任意一个非数字字符
[abc] 代表a,b,c中的任意一个
[^abc] 代表除了a,b,c之外的任意一个字符
[a-z] 代表任意一个小写字母
X? X出现 0 次或 1 次
X* X出现 0 次或多次
X+ X出现 1 次或多次
X{n} X适好出现n次
X{n,} X至少出现n次
X{m,n} X出现n到m次
```

正则表达式的常用方法：

```java
public boolean matches(String regex)（是否与表达式匹配）

public String replaceAll(String regex, String replacement)（替换）

public String[] split(String regex)（字符串分解）
```

## 第九章 输入/输出流

### 1. File类

作用：Java提供 File 类来获取 文件 信息，并实现一些操作

* 构造方法：
```java
//第一种方式

File f = new File("文件路径+文件名"); // 注意路径使用"\\"

//第二种方式
File f = new File("文件路径", "文件名");
```

* 常用的成员方法：
```java
public boolean exists() //判断该对象对应的文件（夹）是否存在
public boolean isFile() //判断该对象是否是文件
public boolean isDirectroy()  //判断该对象是否是文件夹
public String getName() //获得该文件的文件名
public String getAbsolutePath() //获得该文件的绝对路径文件名
public String getParent() //获得该对象的父目录
public long getFreeSpace()  //获得该文件所在盘的剩余空间
public long getTotalSpace() //获得该文件所在盘的总空间
public long length()  //获取文件的长度，即文件的字节数
public boolean canExecute() //用于检查当前文件是否可执行
public boolean canWrite() //用于检查当前文件(夹)是否可写入
public boolean canRead()  //用于检查当前文件(夹)是否可读取
public boolean isHidden() //用于检查当前文件是否被隐藏
public boolean mkdir()  //创建文件夹
public boolean createNewFile()  //创建新文件
public boolean delete() //删除文件（夹）
public File[] listFiles() //返回目录下的全部文件（夹）
```


### 2. 流

* 概念：**流**是一组*有顺序的*，有*起点*和*终点*的数据集合，是对数据传输的总称或抽象。

即数据在两设备间的传输称为流，可以把流理解为传输数据的管道。

* 注意：

1. 流的方向及远端对象

2. 读/写时的数据基本单位（字节/字符）

| 与文件有关的流 | 输入流类        | 输出流类         |
|----------------|-----------------|------------------|
| 文件字符流     | FileReader      | FileWriter       |
| 缓冲字符流     | BufferedReader  | BufferedWriter   |
| 文件字节流     | FileInputStream | FileOutputStream |

### 3. 文件字符流

1. FileReader类

* 构造方法

```java
FileReader(File file)           //使用文件对象作为参数
FileReader(String fileName)     //使用文件名作为参数
```

* 成员方法：字符读取

```java
//从输入流中读取一个字符，即返回该字符对应的编码，若流中没有数据则返回-1。
public int read()

//把输入流中的数据读取到字符数组中
public int read(char[] buffer)
```

2. FileWriter类

* 构造方法
 
```java
FileWriter(File file)                   //使用文件对象作为参数
FileWriter(String fileName)             //使用文件名作为参数
FileWriter(File file, boolean append)   //是否保留原来的内容
```

* 成员方法：字符写入

```java
public void write(char c)               //把单个字符写到输出流中
Public void write(char[] buffer)        //把字符数组写到输出流中
public void write(char[] buffer, int offset, int count)  //功能：把字符数 组buffer中，下标从offset开始的count个字符写入流中
```

### 4. 缓冲字符流

1. BufferedReader类

* 构造方法
```java
BufferedReader(FileReader in) //使用字符输入流对象作为参数
```
* 成员方法：字符读取
```java
public int read()
public int read(char[] buffer)
public String readLine()  //功能：从缓冲字符输入流中读取一行，若流中已经 没有数据，则返回null
```

2. BufferedWriter类

* 构造方法

```java
BufferedWriter(FileWriter out)  //使用字符写入类对象作为参数
```

* 成员方法：字符写入

```java
public void newLine()       //写缓冲字符流输出换行符
public void write(String s) //写缓冲字符流输出字符串s
public void flush()         //把已写入流中的数据更新到文件中
```

### 5. 文件字节流

1. FileInputStream类

* 构造方法

```java
FileInputStream(File file)          //使用文件对象作为参数
FileInputStream(String fileName)    //使用文件名作为参数
```

* 成员方法：字节读取
```java
public int read()               //从输入流中读取一个字节，即返回该字节对应的编 码值，若流中没有数据则返回-1。
public int read(byte[] buffer)  //从输入流中读取数据到字节数组
```

2. FileOutputStream类

* 构造方法

```java
FileOutputStream(File file)                         //使用文件对象作为参数
FileOutputStream(String fileName)                   //使用文件名作为参数
FileOutputStream(File file, boolean append)         //是否保留原来的内容
FileOutputStream(String fileName, boolean append)   //使用文件名作为参数，是 否保留原来的内容
```
* 成员方法：字节写入

```java
public void write(byte c)                               //把单个字节写到 输出流中
Public void write(byte[] buffer)                        //把字节数组写到 输出流中
public void write(byte[] buffer, int offset, int count) //功能：把字节数 组buffer中，下标从offset开始的count个字节写入流中
```

