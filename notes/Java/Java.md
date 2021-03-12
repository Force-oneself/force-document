# Java基础知识

## 重载和重写

​	**重载：**发生在同一个类中,方法名必须相同,参数类型不同,个数不同,顺序不同,方法返回值和访问修饰符可以不同,发生在编译期。

​	**重写：**发生在父子类中，方法名、参数列表必须相同，返回值范围小于等于父类 ，抛出的异常范围小于等于父类，访问修饰符范围大于等于父类，如果父类方法访问修饰符为private则子类不能重写该方法。

## String、StringBuilder和StringBuffer

### 可变性

​	简单来说：String类中使用final关键字字符数组来保存字符串，``` private final char value[]```，所以String对象是不可变的，而StringBuilder与StringBuffer都继承自AbstractStringBuilder类，在这个类中也是使用字符数组保存字符串``` char[] value ```但是没有用final关键字修饰，所以这两种对象都是可变的。

​	AbstractStringBuilder.java

``` java
abstract class AbstractStringBuilder implements Appendable, CharSequence {
    char[] value;
    int count;
    AbstractStringBuilder() {
    }
    AbstractStringBuilder(int capacity) {
        value = new char[capacity];
    }
```

### 线程安全

 	String中的对象是不可变的，也就可以理解为常量，线程安全。AbstractStringBuilder是StringBuilder与StringBuffer的公共父类，定义了一些字符串的基本操作，如expandCapacity、append、insert、indexof等公共方法。StringBuffer对方法加了同步锁或者对调用的方法加了同步锁，所以线程是安全的。StringBuilder并没有对方法进行加同步锁，所以是非线程安全的。

### 性能

​	每次对String类型进行改变的时候，都会生成一个新的String对象，然后将指针指向新的String对象。StringBuffer每次都会对StringBuffer对象本身进行操作，而不是生成新的对象并改变对象引用，相同情况下使用StringBuilder相比使用StringBuffer仅能获得10%-15%左右的性能提升，但却要冒多线程不安全的风险。

### 总结

​	1.操作少量数据=String

​	2.单线程操作字符串缓冲区操作大量数据=StringBuilder

​	3.多线程操作字符串缓冲区操作大量数据=StringBuffer

## 自动装箱与拆箱

​	**装箱：**将基本类型用它们对应的引用类型包装起来；

​	**拆箱：**将包装类型装换为基本数据类型。

## ==与equals

​	**==：**它的作用是判断两个对象的地址是不是相等。即判断两个对象是不是同一个对象。（基本数据类型比较的是值，引用类型比较的是内存地址）。

​	**equals：**它的作用也是判断两个对象是否相等，但它一般有两种情况：

	+ 情况1：累没有覆盖equals()方法，则通过equals比较该类的两个对象时，等价于通过“==”比较两个对象。

 + 情况2：类覆盖了equals()方法，我们都是覆盖了该方法来比较两个对象的内容相等；若他们的内容相等，则返回true。

## final

​	对于一个fifinal变量，如果是基本数据类型的变量，则其数值一旦在初始化之后便不能更改；如果是引用类型的变量，则在对其初始化之后便不能再让其指向另一个对象。

​	当用fifinal修饰一个类时，表明这个类不能被继承。fifinal类中的所有成员方法都会被隐式地指定为fifinal方法。

​	使用fifinal方法的原因有两个。第一个原因是把方法锁定，以防任何继承类修改它的含义；第二个原因是效率。在早期的Java实现版本中，会将fifinal方法转为内嵌调用。但是如果方法过于庞大，可能看不到内嵌调用带来的任何性能提升（现在的Java版本已经不需要使用fifinal方法进行这些优化了）。类中所有的private方法都隐式地指定为fianl。

## Object类常用方法

``` java
//native方法，用于返回当前运行时对象的Class对象，使用了 final关键字修饰，故不允许子类重写。
public final native Class<?> getClass() 
//native方法，用于返回对象的哈希码，主要使用在哈希表中，比如JDK中的 HashMap。 
public native int hashCode()
//用于比较2个对象的内存地址是否相等，String类对该方法进行了重写用户 比较字符串的值是否相等。 
public boolean equals(Object obj)
//naitive方法，用于创建并返回 当前对象的一份拷贝。一般情况下，对于任何对象 x，表达式 x.clone() != x 为true，x.clone().getClass() == x.getClass() 为true。Object本身没有实现Cloneable接口，所以不重写clone方法并且进行调用的话会发生 CloneNotSupportedException异常。 
protected native Object clone() throws CloneNotSupportedException
//返回类的名字@实例的哈希码的16进制的字符串。建议Object所有的子类都重写这个方 法。
public String toString()
//native方法，并且不能重写。唤醒一个在此对象监视器上等待的线程(监视 器相当于就是锁的概念)。如果有多个线程在等待只会任意唤醒一个。
public final native void notify()
//native方法，并且不能重写。跟notify一样，唯一的区别就是会唤醒 在此对象监视器上等待的所有线程，而不是一个线程。 
public final native void notifyAll()
//native方法，并且不能 重写。暂停线程的执行。注意：sleep方法没有释放锁，而wait方法释放了锁 。timeout是等待时间。
public final native void wait(long timeout) throws InterruptedException 
//多了nanos参数， 这个参数表示额外时间（以毫微秒为单位，范围是 0-999999）。 所以超时的时间还需要加上nanos毫秒。
public final void wait(long timeout, int nanos) throws InterruptedException	
//跟之前的2个wait方法一样，只不过该方法一直等 待，没有超时时间这个概念
public final void wait() throws InterruptedException 
//实例被垃圾回收器回收的时候触发的操作
protected void finalize() throws Throwable { }
```

## 异常处理

​	在 Java 中，所有的异常都有一个共同的祖先java.lang包中的 **Throwable****类**。Throwable： 有两个重要的子类：

​	**Exception**和 **Error**，二者都是 Java 异常处理的重要子类，各自都包含大量子类。

​	**Error**是程序无法处理的错误，表示运行应用程序中较严重问题。大多数错误与代码编写者执行的操作无关，而表示代码运行时 JVM（Java 虚拟机）出现的问题。例如，Java虚拟机运行错误（Virtual MachineError），当JVM 不再有继续执行操作所需的内存资源时，将出现 OutOfMemoryError。这些异常发生时，Java虚拟机（JVM）一般会选择线程终止。

​	这些错误表示故障发生于虚拟机自身、或者发生在虚拟机试图执行应用时，如Java虚拟机运行错误、类定义错误等。这些错误是不可查的，因为它们在应用程序的控制和处理能力之 外，而且绝大多数是程序运行时不允许出现的状况。对于设计合理的应用程序来说，即使确实发生了错误，本质上也不应该试图去处理它所引起的异常状况。在 Java中，错误通过Error的子类描述。

​	**Exception**:是程序本身可以处理的异常。Exception 类有一个重要的子类 RuntimeExceptionRuntimeException 异常由Java虚拟机抛出。NullPointerException（要访问的变量没有引用任何对象时，抛出该异常）ArithmeticException（算术运算异常，一个整数除以0时，抛出该异常）和ArrayIndexOutOfBoundsException （下标越界异常）。

​	**注意：**异常和错误的区别：异常能被程序本身可以处理，错误是无法处理。

### Throwable类常用方法

+ public string getMessage():返回异常发生时的详细信息
+ public string toString():返回异常发生时的简要描述
+ public string getLocalizedMessage():返回异常对象的本地化信息。使用Throwable的子类覆盖这个方法，可
  以声称本地化信息。如果子类没有覆盖该方法，则该方法返回的信息与getMessage（）返回的结果相同
+ public void printStackTrace():在控制台上打印Throwable对象封装的异常信息

### 异常处理总结

+ try 块：用于捕获异常。其后可接零个或多个catch块，如果没有catch块，则必须跟一个finally块。

+ catch 块：用于处理try捕获到的异常。

+ finally 块：无论是否捕获或处理异常，finally块里的语句都会被执行。当在try块或catch块中遇到return语句
  时，finally语句块将在方法返回之前被执行。

  在以下4种特殊情况下，finally块不会被执行：

1. 在finally语句块中发生了异常。
2. 在前面的代码中用了System.exit()退出程序。
3. 程序所在的线程死亡。
4. 关闭CPU

## 获取用键盘输入常用的的两种方法

### Scanner

``` java
Scanner input = new Scanner(System.in);
String s = input.nextLine(); 
input.close();
```

### BufferedReader

``` java
BufferedReader input = new BufferedReader(new InputStreamReader(System.in)); 
String s = input.readLine();
```

## 接口与抽象类

1. 接口的方法默认是 public，所有方法在接口中不能有实现(Java 8 开始接口方法可以有默认实现），抽象类可以有非抽象的方法
2. 接口中的实例变量默认是 fifinal 类型的，而抽象类中则不一定
3. 一个类可以实现多个接口，但最多只能实现一个抽象类
4. 一个类实现接口的话要实现接口的所有方法，而抽象类不一定
5. 接口不能用 new 实例化，但可以声明，但是必须引用一个实现该接口的对象 从设计层面来说，抽象是对类的抽象，是一种模板设计，接口是行为的抽象，是一种行为的规范。

**备注:**在JDK8中，接口也可以定义静态方法，可以直接用接口名调用。实现类和实现是不可以调用的。如果同时实现

两个接口，接口中定义了一样的默认方法，必须重写，不然会报错。(详见

issue:https://github.com/Snailclimb/JavaGuide/issues/146)

## ArrayList与LinkedList

1. **是否保证线程安全：** ArrayList 和 LinkedList 都是不同步的，也就是不保证线程安全；
2. **底层数据结构：** Arraylist 底层使用的是Object数组；LinkedList 底层使用的是双向链表数据结构（JDK1.6之前为循环链表，JDK1.7取消了循环。注意双向链表和双向循环链表的区别：）；
3. **插入和删除是否受元素位置的影响：** ① **ArrayList** **采用数组存储，所以插入和删除元素的时间复杂度受元素**位置的影响。 比如：执行 add(E e) 方法的时候， ArrayList 会默认在将指定的元素追加到此列表的末尾，这种情况时间复杂度就是O(1)。但是如果要在指定位置 i 插入和删除元素的话（ add(int index, E element) ）时间复杂度就为 O(n-i)。因为在进行上述操作的时候集合中第 i 和第 i 个元素之后的(n-i)个元素都要执行向后位/向前移一位的操作。 ② **LinkedList** **采用链表存储，所以插入，删除元素时间复杂度不受元素位置的影响，都是**近似**O**（1）而数组为近似**O**（n）。
4. 是否支持快速随机访问：LinkedList 不支持高效的随机元素访问，而 ArrayList 支持。快速随机访问就是通过元素的序号快速获取元素对象(对应于 get(int index) 方法)。
5. **内存空间占用：** ArrayList的空 间浪费主要体现在在list列表的结尾会预留一定的容量空间，而LinkedList的空间花费则体现在它的每一个元素都需要消耗比ArrayList更多的空间（因为要存放直接后继和直接前驱以及数据）