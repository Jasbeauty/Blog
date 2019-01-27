## 面向对象和面向过程的区别
#### 面向对象
* 其模块单位是类：类是数据类型，对象是类的实例
* 将数据及对数据的操作行为放在一起，作为对象；再通过抽象找出同一类型对象，形成类
* 封装性、抽象性、继承性、多态性

#### 面向过程
* 是一种自顶向下的功能分解法
* 其程序单位是过程或函数
* 可复用性差

## Java 语言有哪些特点
* 简单性
* 面向对象
* 平台无关性
* 可移植性
* 解释性
* 高性能
* 动态性
* 可靠性和安全性
* 多线程
* 分布式处理

## 什么是JDK什么是JRE什么是JVM 三者之间的联系和区别
#### JDK
Java Development Kits <==> Java开发工具包
开发的核心
#### JRE
Java Runtime Environment <==> Java运行环境（运行时类库）
#### JVM
Java Virtual Machine <==> Java虚拟机
跨平台的核心
###### 联系
一层层的嵌套关系：JDK > JRE > JVM
JDK = JRE + JVM + 其它

## 什么是字节码 采用字节码的最大好处是什么
字节码 Bytecode（.class 文件）：是一种介于Java（用户语言）和机器语言之间的中间语言；是 Java代码部署的最小单元（二进制）

Java编译器将Java源程序编译为JVM字节码；通过Java解释器就可以运行程序

JVM是Java平台无关的基础

Java程序运行环境：
```
Java源程序（.java文件）
=> Java编译器 
=> Java Bytecode（.class文件）
=> Bytecode装载 
=> 字节码校验器 
=> Bytecode解释 
=> 系统执行平台
```
###### 好处
确保了Java的平台无关性；通过JVM保证数据类型的一致性

## Java和C++的区别
Java去掉了C++语言的复杂性和二义性成分，更加安全和可移植，也更简单，文件尺寸小，不需要显式进行内存管理

Java中没有析构函数、指针、运算符重载
> 析构函数：用来释放对象占用的空间
> 特点：名字与类名相同、在前面加上“～”、无参数和返回值、一个类最多只有一个析构函数

> 运算符重载：运算符与类结合，产生新的含义

> 指针：指针 `type *var-name` 是一个变量，其值为另一个变量的地址，即内存位置的直接地址

## 什么是Java程序的主类 应用程序和小程序的主类有何不同
Java程序有四种基本类型：应用程序application、小应用程序applet、servlet、bean

main方法所在的类叫主类：`public static void main(String args[])`

小程序不能直接运行，必须嵌入在网页中

## 字符型常量和字符串常量的区别
#### 字符型常量
用单引号括起来的单个字符
#### 字符串常量
用双引号括起来的多个字符（可以是0个）
> Java中字符串是String类的对象

可以使用 `+` 把两个或更多的字符串常量连接在一起

## 构造器 Constructor 是否可以被override
* 构造器也叫构造方法
* 构造方法一般用于为类新建的对象分配内存空间和进行变量的初始化
* 构造方法只能在创建对象时用new命令调用
* 构造方法必须与其类名相同
* 构造方法没有返回类型
* 可以有参数，可以被重载
* 不能被重写

## 重载和重写的区别
#### 重载
* 重载是在一个类里面，方法名字相同，而参数必须不同；返回类型可以相同也可以不同
* 被重载的方法必须改变参数列表(参数个数、类型、顺序不一样)
* 方法能够在同一个类中或者在一个子类中被重载
#### 重写
* 子类对父类允许被访问的方法进行重新编写, 返回值和形参都不能改变
* 访问权限不能比父类中被重写的方法访问权限更低
* 父类的成员方法只能被它的子类重写：`super .父类同名方法(...)`
* 声明为final的方法不能被重写
* 声明为static的方法不能被重写，但是能够被再次声明
* 构造方法不能被重写

## Java面向对象编程三大特性：封装、继承、多态
#### 封装
* 把对象的全部属性和全部操作结合在一起，形成一个不可分割的独立单位
* 尽可能隐蔽对象的全部细节，只保留有限的对外接口
* 提高程序的可复用性和可维护性；保护了私有数据
#### 继承
* 类只支持单继承，接口支持多继承
* 
``` java
[类的修饰符] class 子类名 extends 父类名 {
      成员变量定义;
      成员方法定义;
}
```
* 在创建子类对象时，必须先调用直接父类的构造方法，然后才调用子类本身的构造方法；finalize调用顺序与此相反
* 抽象类必须被继承，抽象方法必须被重写
#### 多态
* 在继承层次结构中，父类可以定义为抽象类或接口，通过在子类中实现父类中的抽象方法，从而实现对象的多态性

## String、StringBuffer、StringBuilder区别是什么 & String为什么是不可变的
#### String类
* 在java.lang包中
* 值在创建后不能被更改
> * 原因：
>     * String类本身是final的，不可被继承
>     * String类内部通过private final char value[]实现，从而保证了引用的不可变和对外的不可见
>     * String内部通过良好的封装，不去改变value数组的值
> * 优势：
>     * 安全性
>     * 效率高
###### 常用方法
* `compareTo(String anotherString)`：按字典顺序比较两个字符串，如果此字符串的字典大小超过字符串参数，则值大于0 ==> `int`
* `concat(String str)`：将指定的字符串连接到该字符串的末尾 ==> `new String`
* `endsWith(String suffix)`：测试此字符串是否以指定的后缀结尾 ==> `boolean`
* `equals(Object anObject)`：将此字符串与指定对象进行比较 ==> `boolean`
* `String.format("hi,%s", "jas")`：返回格式化的字符串 `hi,jas`
* `a.hashCode()`：返回此字符串的哈希码 ==> `int`
* `String.join("-","java","is","cool")`：返回一个新的字符串 `java-is-cool`
* `length()` ==> `int`
* `replace(char oldChar, char newChar)` ==> `new String`
* `split(String regex)` ==> `String[]`
* `trim()`：返回一个字符串，其值为此字符串，并删除任何前导和尾随空格 ==> `new String`
* `charAt(int index)`：返回当前字符串的某一指定位置的字符 ==> `String`
* `toCharArray()`：将String对象转换为字符型数组 ==> `char[]`

#### StringBuffer、StringBuilder类
* 字符串内容可以变化
* 在java.lang包中
###### 常用方法
* `append()`
* `delete(int start, int end)`：删除从start为开始索引到end-1索引之间的字符串
* `insert()`
* `replace()`
* `reverse()`：颠倒StringBuffer对象的内容
* `length()`
* `setCharAt(int index, char ch)`：将指定索引处的字符设置为参数ch中的字符

## 自动装箱与拆箱
* 自动装箱就是Java自动将原始类型值转换成对应的对象，比如将int的变量转换成Integer对象，这个过程叫做装箱，反之将Integer对象转换成int类型值，这个过程叫做拆箱
> 原始类型`byte,short,char,int,long,float,double`和boolean对应的封装类为`Byte,Short,Character,Integer,Long,Float,Double,Boolean`
* 自动装箱时编译器调用valueOf将原始类型值转换成对象，同时自动拆箱时，编译器通过调用类似intValue(),doubleValue()这类的方法将对象转换成原始类型值

## 在一个静态方法内调用一个非静态成员为什么是非法的










