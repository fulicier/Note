### 常见数据类型长度

| 类型 | 位长/b | 取值范围 |
| ----- | ---| ------- |
| boolean | 8 | -128~127 |
| char | 16  | 0~65535  |
| short  | 16  | -32768~32767  |
| int  | 32  | -2^31~2^31-1  |
| float  | 32  | 3.4e-38~3.4e38  |
| double  | 64  | 1.7e-208~1.7e308  |

>Java中的常量值是用文字串表示的，它区分为不同的类型，如整型常量123，实型常1.23，
字符常量‘a’，布尔常量true、false以及字符串常量“This is a constant string”。   
Java 的常量用final说明，约定常量名一般全部使用大写字母，如果是多个单词组合在一起的，单词之间用下划线连接，常量在程序执行时不可更改。    
final还可以用于修饰类和方法。
```java
public class HelloWorld{
  public void main(){
    final int i = 1;
    i = 10;  //i在之前已经被赋值过了，所以这里会出现编译错误
  }
  public void method(final int j){
    j = 1;  //j在方法调用时已被赋值，所以这里会报错
  }
}
```

<br>
>String类型其实并不是基本类型，但是它是如此广泛的被使用，常常被误以为是一种基本类型。<br>
String类型是Immutable的，一旦创建就不能够被改变。

** <font color='#97CBFF'>String, StringBuffer, StringBuild区别</font> **
+ String: 字符串常量，为不可变对象
  - 每次对String类型进行改变时，都等同于生成新的String对象，然后将原来的指针指向新的String对象。
  - 经常改变内容的字符串最好不要用 String ，因为每次生成对象都会对系统性能产生影响，特别当内存中无引用对象多了以后，JVM的GC就会开始工作，那速度是一定会相当慢的。
+ StringBuffer: 字符串变量(线程安全)
  - 每次结果都会对 StringBuffer 对象本身进行操作，而不是生成新的对象，再改变对象引用。
+ StringBuild: 字符串变量(非线程安全)
  - 此类提供一个与 StringBuffer 兼容的 API，但不保证同步。该类被设计用作 StringBuffer 的一个简易替换，用在字符串缓冲区被单个线程使用的时候（这种情况很普遍）。
  - 如果可能，建议优先采用该类，因为在大多数实现中，它比 StringBuffer 要快。两者的方法基本相同。

>在某些特别情况下，String 对象的字符串拼接其实是被 JVM 解释成了 StringBuffer 对象的拼接，所以这些时候 String 对象的速度并不会比 StringBuffer 对象慢，而特别是以下的字符串对象生成中，String 效率是远要比 StringBuffer 快的：<br>
`String S1 = “This is only a” + “ simple” + “ test”;`<br>
`StringBuffer Sb = new StringBuilder(“This is only a”).append(“ simple”).append(“ test”);`<br>

### 数据类型转换
变量与存储器有着直接关系，定义一个变量就是要编译器分配所需要的内存空间，分配多少空间，这就是根据我们所定义的变量类型所决定的。变量名实际上是代表所分配空间的内存首地址。
![](assets/001/20180507-ac7fee1d.png)

### 运算符

** <font color='#97CBFF'>逻辑运算符</font> **    

| 运算符 | 结果 | 说明 |
| :--- | :--- | :--- |
| ~  | 按位非(NOT, 一元运算)  | 对每一位取反 |
| &  | 按位与(AND)  | |
| &#124; | 按位或(OR)  | |
| ^  | 按位异或(XOR)  | |
| >>  | 右移  | |
| >>>  | 无符号右移(左边空出的位以0填充)  | |
| <<  | 左移  | |
| &=  | 按位与赋值  | |
| &#124;=  | 按位或赋值  | |
| ^=  | 按位异或赋值  | |
| >>=  | 右移赋值  | |
| >>>=  | 无符号右移赋值(左边空出的位以0填充)  | |
| <<=  | 左移赋值  | &nbsp; |

### 数组
