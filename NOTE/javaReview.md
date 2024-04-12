#Feb 7

*移位运算(Shift Operators)
( << :左移运算符，向左移若干位，高位丢弃，低位补零。x << 1,相当于 x 乘以 2(不溢出的情况下)。
( >> :带符号右移，向右移若干位，高位补符号位，低位丢弃。正数高位补 0,负数高位补 1。x >> 1,相当于 x 除以 2
( >>> :无符号右移，忽略符号位，空位都以 0 补齐。
注意: double & float 不能使用
注意: x<<42等同于x<<10，x>>42等同于x>>10，x >>>42等同于x >>> 10。 不能超过32位

实例
/*
int i = -1;
System.out.println("初始数据：" + i);
System.out.println("初始数据对应的二进制字符串：" + Integer.toBinaryString(i));
i <<= 10;
System.out.println("左移 10 位后的数据 " + i);
System.out.println("左移 10 位后的数据对应的二进制字符 " + Integer.toBinaryString(i));


初始数据：-1
初始数据对应的二进制字符串：11111111111111111111111111111111
左移 10 位后的数据 -1024
左移 10 位后的数据对应的二进制字符 11111111111111111111110000000000
*/

*小补充
1. Java 里使用 long 类型的数据一定要在数值后面加上 L，否则将作为整型解析。
2. char a = 'h'char :单引号，String a = "hello" :双引号。

*自动拆装箱
Integer i = 10; //装箱 等价于 Integer i = Integer.valueOf(10)
int n = i; //拆箱 int n = i.intValue();
要避免频繁拆装箱 会损失性能

*成员变量(field)和局部变量(local variable)

public class VariableExample {
    // 成员变量
    private String name;
    private int age;
    // 方法中的局部变量
    public void method() {
        int num1 = 10; // 栈中分配的局部变量
        String str = "Hello, world!"; // 栈中分配的局部变量
        System.out.println(num1);
        System.out.println(str);
    }
    // 带参数的方法中的局部变量
    public void method2(int num2) {
        int sum = num2 + 10; // 栈中分配的局部变量
        System.out.println(sum);
    }
    // 构造方法中的局部变量
    public VariableExample(String name, int age) {
        this.name = name; // 对成员变量进行赋值
        this.age = age; // 对成员变量进行赋值
        int num3 = 20; // 栈中分配的局部变量
        String str2 = "Hello, " + this.name + "!"; // 栈中分配的局部变量
        System.out.println(num3);
        System.out.println(str2);
    }
}

*字符型常量和字符串常量

public class StringExample {
    // 字符型常量
    public static final char LETTER_A = 'A';
    // 字符串常量
    public static final String GREETING_MESSAGE = "Hello, world!";
    public static void main(String[] args) {
        System.out.println("字符型常量占用的字节数为："+Character.BYTES);
        System.out.println("字符串常量占用的字节数为："+GREETING_MESSAGE.getBytes().length);
    }
}

*方法
1. 无参数无返回值
public void f1() {
    //......
}
// 下面这个方法也没有返回值，虽然用到了 return
public void f(int a) {
    if (...) {
        // 表示结束方法的执行,下方的输出语句不会执行
        return;
    }
    System.out.println(a);
}

2. 有参数无返回值
public void f2(Parameter 1, ..., Parameter n) {
    //......
}

3. 有返回值无参数
public int f3() {
    //......
    return x;
}

4. 有返回值有参数
public int f4(int a, int b) {
    return a * b;
}

*静态方法和实例方法

            class.method
一般建议使用 类名.方法名 的方式来调用静态方法。

public class Person {
    public void method() {
      //......
    }
    public static void 
    staicMethod(){
      //......
    }
    public static void main(String[] args) {
        Person person = new Person();
        object.method
        // 调用实例方法
        person.method();
        // 调用静态方法
        Person. staicMethod()
    }
}

#Feb 8
*面向对象和面向过程的区别
//写个例子玩 面向对象

public class Circle {
    private double radius;
    public Circle(double radius) {
        this.radius = radius;
    }
    public double getArea() {
        return Math.PI * radius * radius;
    }
    public double getPerimeter() {
        return Math.PI * 2 * radius;
    }
    public static void main(String[] args) {
        Circle circle = new circle(3.0);
        circle.getArea();
        circle.getPerimeter();
    }
}

//面向过程

public class Main {
    public static void main(String[] args) {
        double radius = 3.0;
        double area = Math.PI * radius * radius;
        double perimeter = 2 * Math.PI * radius;
    }
}

*对象的相等和引用对象相等的区别

对象的相等一般比较的是内存中存放的内容是否相等。
引用相等一般比较的是他们指向的内存地址是否相等。

//例子

String str1 = "hello";
String str2 = new String("hello");
String str3 = "hello";
// 使用 == 比较字符串的引用相等
System.out.println(str1 == str2);
System.out.println(str1 == str3);
// 使用 equals 方法比较字符串的相等
System.out.println(str1.equals(str2));
System.out.println(str1.equals(str3));

false
true
true
true

*面对对象三大特征
//封装 Encapsulation

public class Student {
    private int id;
    private String name;
    public int getId() {
        return id;
    }
    /////////
}


//继承 Inheritance
//多态 Polymorphic

*接口(Interface)和抽象类(abstract)


*一些String的tips
操作少量数据 用String
单线程操作字符串缓冲区下操作大量数据: 适用 StringBuilder
多线程操作字符串缓冲区下操作大量数据: 适用 StringBuffer

#Feb 11

*Exception 和 Error 的区别

Exception :程序本身可以处理的异常，可以通过 catch 来进行捕获。Exception 又可以分为 Checked Exception (受检查异常，必须处理) 
和 Unchecked Exception (不受检查异常，可以不处理)。
    -Checked 不处理无法编译
    -Unchecked 不处理正常通过编译
Error：Error 属于程序无法处理的错误 ，我们没办法通过 catch 来进行捕获不建议通过catch捕获 。例如 Java 虚拟机运行错误（Virtual MachineError）、虚拟机内存不够错误(OutOfMemoryError)、类定义错误（NoClassDefFoundError）等 。
这些异常发生时，Java 虚拟机（JVM）一般会选择线程终止。

*try-catch-finally 例子 
//no return 
try {
    System.out.println("test");
    throw new RuntimeException("RuntimeException");
} catch (Exception e) {
    System.out.println("Catch Exception -> " + e.getMessage()); //getMesage 输出是你上面的自定义内容 "RuntimeException"
} finally { 
    System.out.println("Finally");
}

*泛型(Generics)

1. 泛型类

public class Generic<T> {
    private T key;
    public Generic(T key) {
        this.key = key;
    }
    public T getKey() {
        return key;
    }
}
Generic<Integer> genericInteger = new Generic<Integer>(123456);

2. 泛型接口

public interface Generator<T> {
    public T method();
}

//不指定类型
class GeneratorImpl<T> implements Generator<T> {
    @Override
    public T method() {
        return null;
    }
}

//指定类型 
class GeneratorImpl<T> implements Generator<String> {
    @Override
    public String method() {
        return "hello";
    }
}

3. 泛型方法
public static <E> void printArray(E[] inputArray) {
    for (E element : inputArray) {
        System.out.printf("%s", element);
    }
}

使用:
Integer[] intArray = {1, 2, 3};
String[] stringArray = {"hello", "world"};
printArray(intArray);
printArray(stringArray);


*反射(Reflection)

*序列化

#Feb 12
#Java 值传递(pass by value)

*实参(Arguments)&形参(Parameters)
实参: 用于传递给函数/方法的参数,必须有确定的值;
形参: 用于定义函数/方法,接收实参,不需要有确定的值;

String hello = "Hello!";
//hello 是实参(Arguments)
sayHello(hello);
//str 是形参(Parameters)
void sayHello(String str) {
    System.out.println(str);
}

*值传递&引用传递
程序设计语言将[实参]传递给方法（或函数）的方式分为两种：
值传递：方法接收的是实参值的拷贝，会创建副本。
引用传递：方法接收的直接是实参所引用的对象在堆中的地址，不会创建副本，对形参的修改将影响到实参。
注: java 中只存在值传递

Ex:
//a、b 相当于 num1、num2 的副本，副本的内容无论怎么修改，都不会影响到原件本身。
public static void main(String [] args) {
    int num1 = 10;
    int num2 = 20;
    swap(num1,num2);
    System.out.println()//.....
}

public static void swap(int a, int b) {
    int temp = a;
    a = b;
    b = temp;
}

Ex2:
//这里传递的还是值，不过，这个值是实参的地址.
public static void main(String[] args) {
    int[] arr = {1,2,3,4,5};
    change(arr);
    Sys
}

public static void change(int[] array) {
    array[0] = 0;
}

#序列化(Serialization)
如果我们需要持久化 Java 对象比如将 Java 对象保存在文件中，或者在网络传输 Java 对象，这些场景都需要用到序列化。

序列化：将数据结构或对象转换成二进制字节流的过程
反序列化：将在序列化过程中所生成的二进制字节流转换成数据结构或者对象的过程

场景:
对象在进行网络传输（比如远程方法调用 RPC 的时候）之前需要先被序列化，接收到序列化的对象之后需要再进行反序列化；
将对象存储到文件之前需要进行序列化，将对象从文件中读取出来需要进行反序列化；
将对象存储到数据库（如 Redis）之前需要用到序列化，将对象从缓存数据库中读取出来需要反序列化；
将对象存储到内存之前需要进行序列化，从内存中读取出来之后需要进行反序列化。

比较常用的序列化协议有 Hessian、Kryo、Protobuf、ProtoStuff，这些都是基于二进制的序列化协议。

#泛型&通配符(Generics)

Ex:
public class GenericMethodTest {
    public static <E> void printArray(E[] inputArray) {
        for (E element : inputArray) {
            System.out.printf("%s", element);
        }
    }
}

Ex2:
public class MaximumTest {
    public static <T extends Comparable<T>> T maximum(T x, T y, T z) {
        T max = x;
        if (y.compareTo(max) > 0) {
            max = y;
        }
        ////////
    }
}

*泛型类
Ex:

public class Box<T> {
    private T t;
    public void add(T t) {
        this.t = t;
    }
    public T get() {
        return t;
    }
}

*通配符
类型通配符一般是使用 ? 代替具体的类型参数。例如 List<?> 
在逻辑上是 List<String>,List<Integer> 等所有 List<具体类型实参> 的父类。

Ex:
public class GenericTest {
    public static void main(String[] args) {
        List<String> name = new ArrayList<String>();
        List<Integer> age = new ArrayList<Integer>();
        getData(name);
        getData(age);
    }
    //因为 getData() 方法的参数是 List<?> 类型的，所以 name，age，number 
    //都可以作为这个方法的实参，这就是通配符的作用。
    public static vod getData(List<s?> data) {
        System.out.println(data.get(0));
    }
}

#反射机制(Reflection)
//说实话不知道是个啥东西
Ex:
package cn.javaguide;

public class TargetObject {
    private String value;
    public TargetObject() {
        value = "xxxxxxxx";
    }
    public void publicMethod(String s) {
        //printxxxx
    }
    public void privateMethod() {
        //printxxx
    }
}

#代理模式(Proxy)
使用代理对象来代替对真实对象(real object)的访问，这样就可以在不修改原目标对象的前提下，提供额外的功能操作，扩展目标对象的功能。

*静态代理
没什么屁用

*动态代理
运用少 但是学习有助于对于框架的理解
-JDK动态代理

#BigDecimal
“浮点数之间的等值判断，基本数据类型不能用 == 来比较，
包装数据类型不能用 equals 来判断。”

BigDecimal a = new BigDeciaml("1.0");
BigDeciaml b = new BigDecimal("0.9");
System.out.println(a.add(b));// 1.9
System.out.println(a.subtract(b));// 0.1
System.out.println(a.multiply(b));// 0.90
System.out.println(a.divide(b, 2, RoundingMode.HALF_UP));// 1.11
-> public BigDecimal divide(BigDecimal divisor, int scale, RoundingMode roundingMode) {
       return divide(divisor, scale, roundingMode.oldMode);
   }
   
a.compareTo(b) : 返回 -1 表示 a 小于 b，0 表示 a 等于 b ， 1 表示 a 大于 b。
BigDecimal a = new BigDecimal("1.0");
BigDecimal b = new BigDecimal("0.9");
System.out.println(a.compareTo(b));// 1

#Unsafe
Unsafe 类使 Java 语言拥有了类似 C 语言指针一样操作内存空间的能力

#SPI
Service Provider Interface

#语法糖(Syntactic Sugar) 



#Java 集合 
*Collection & Map

Collection
主要用于存放单一元素
    -Set, List, Queue
    
Map
存放键值对
    -HashMap, Hashtable, SortedMap

List(对付顺序的好帮手): 存储的元素是有序的、可重复的。
Set(注重独一无二的性质): 存储的元素不可重复的。
Queue(实现排队功能的叫号机): 按特定的排队规则来确定先后顺序，存储的元素是有序的、可重复的。
Map(用 key 来搜索的专家): 使用键值对（key-value）存储，类似于数学上的函数 y=f(x)，"x" 代表 key，"y" 代表 value，key 是无序的、
不可重复的，value 是无序的、可重复的，每个键最多映射到一个值。

List
    -ArrayList, Vector, LinkedList
Set
    -HashSet(无序,唯一)
    -LinkedHashSet
    -TreeSet(有序,唯一)
Queue
    -PriorityQueue(数组来实现小顶堆), DelayQueue, ArrayDeque

*Array & ArrayList
array:
String[] stringArr = new String[] {xxxx}
arrayList:
ArrayList<String> stringList = new ArrayList<>(Arrays.asList("hellos", "world", "!"));
ArrayList 中可以存储任何类型的对象，包括 null 值。不过，不建议向ArrayList 中添加 null 值， null 值无意义，
会让代码难以维护比如忘记做判空处理就会导致空指针异常。

ArrayList插入和删除时间
插入:
    head O(n)
    tail 尾部插入：当 ArrayList 的容量未达到极限时，往列表末尾插入元素的时间复杂度是 O(1)，因为它只需要在数组末尾添加一个元素即可；当容量已达到极限并且需要扩容时，
    则需要执行一次 O(n) 的操作将原数组复制到新的更大的数组中，然后再执行 O(1) 的操作添加元素。
    指定位置插入：需要将目标位置之后的所有元素都向后移动一个位置，然后再把新元素放入指定位置。这个过程需要移动平均 n/2 个元素，因此时间复杂度为 O(n)。
删除:
    头部删除：由于需要将所有元素依次向前移动一个位置，因此时间复杂度是 O(n)。
    尾部删除：当删除的元素位于列表末尾时，时间复杂度为 O(1)。
    指定位置删除：需要将目标元素之后的所有元素向前移动一个位置以填补被删除的空白位置，因此需要移动平均 n/2 个元素，时间复杂度为 O(n)。
    
LinkedList插入和删除时间
头部插入/删除：只需要修改头结点的指针即可完成插入/删除操作，因此时间复杂度为 O(1)。
尾部插入/删除：只需要修改尾结点的指针即可完成插入/删除操作，因此时间复杂度为 O(1)。
指定位置插入/删除：需要先移动到指定位置，再修改指定节点的指针完成插入/删除，因此需要移动平均 n/2 个元素，时间复杂度为 O(n)。

 LinkedList 不支持高效的随机元素访问，而 ArrayList（实现了 RandomAccess 接口） 支持。快速随机访问就是通过元素的序号快速获取元素对象(对应于get(int index)方法)。
 
 
 *注: 我们在项目中一般是不会使用到 LinkedList 的，需要用到 LinkedList 的场景几乎都可以使用 ArrayList 来代替，并且，性能通常会更好！就连 LinkedList 的作者约书亚 · 布洛克（Josh Bloch）自己都说从来不会使用 LinkedList 。
 
 compareTo Ex:
 
 public class Person implements Comparable<Person> {
    private String name;
    private int age;
    public Person(String name, int age) {
        this.name = name;
        this.age = age;
    }
    public getName() {
        return name;
    }
    public setName(String name) {
        this.name = name;
    }
    public getAge() {
        return age;
    }
    public setAge(int age) {
        this.age = age;
    }
    @Override
    public int compareTo(Person o) {
        if (this.age > o.getAge()) {
            return 1;
        } 
        if (this.age < o.getAge()) {
            return -1;
        }
        return 0;
    }
 }
 
 HashSet、LinkedHashSet 和 TreeSet 的主要区别在于底层数据结构不同。HashSet 的底层数据结构是哈希表（基于 HashMap 实现）。LinkedHashSet 的底层数据结构是链表和哈希表，元素的插入和取出顺序满足 FIFO。
 TreeSet 底层数据结构是红黑树，元素是有序的，排序的方式有自然排序和定制排序。
 
 Random shit Ex:
 
 String[] test = {"bag"};
 List<String> myList = ArrayList<>(Arrays.asList(test));
 
 随机练习:
 PriorityQueue->
 优先队列元素是按排序顺序检索的。Comparator 接口自定义元素的顺序
 PriorityQueue<Integer> numbers = new PriorityQueue<>();
 class Main {
    public static void main(String[] args) {
        PriorityQueue<integer> numbers = new PriorityQueue();
        numbers.add(4);//添加方法
        numbers.add(2);
        numbers.offer(1);//[1,2,4]
        numbers.peek();// 1
        Iterator<Integer> iterate = numbers.iterator();
        while(iterate.hasNext()) {
            xxx
        }
        contains;
        size;
        toArray;
    }
 }
 PriorityQueue 比较器(comparator)
 
 import java.util.PriorityQueue;
 import java.util.Comparator;
 class Main {
     public static void main(String[] args) {
 
         //创建优先级队列
         PriorityQueue<Integer> numbers = new PriorityQueue<>(new CustomComparator());
         numbers.add(4);
         numbers.add(2);
         numbers.add(1);
         numbers.add(3);
         System.out.print("PriorityQueue: " + numbers);
     }
 }
 
 class CustomComparator implements Comparator<Integer> {
     @Override
     public int compare(Integer number1, Integer number2) {
         int value =  number1.compareTo(number2);
         //元素以相反的顺序排序
         if (value > 0) {
             return -1;
         }
         else if (value < 0) {
             return 1;
         }
         else {
             return 0;
         }
     }
 }

#Lambda practice
parameter -> expression
(parameter1, parameter2) -> expression
(parameter1, parameter2) -> { code block }

Ex:
public class Main {
    public static void main(String[] args) {
        ArrayList<Integer> numbers = new ArrayList<>();
        numbers.add();//xxx
        numbers.forEach( (n) -> { System.out.print(n)});
    }
}

#IO
InputStream/Reader: 所有的输入流的基类，前者是字节输入流，后者是字符输入流。
OutputStream/Writer: 所有输出流的基类，前者是字节输出流，后者是字符输出流。

#Input output 一般会配合buffer使用
BufferedInputStream bufferedInputStream = new BufferedInputStream(new FileInputStream("input.txt"));
FileOutputStream fileOutputStream = new FileOutputStream("output.txt");
BufferedOutputStream bos = new BufferedOutputStream(fileOutputStream)

注: 字符和字节用不同流因为乱码问题
utf8 :英文占 1 字节，中文占 3 字节，
unicode：任何字符都占 2 个字节，
gbk：英文占 1 字节，中文占 2 字节。

#进程和线程

进程是程序的一次执行过程，是系统运行程序的基本单位，因此进程是动态的.
线程与进程相似，但线程是一个比进程更小的执行单位。一个进程在其执行的过程中可以产生多个线程.

并发(Concurrent) 
并行(Parallel)

如何创建线程:
new Thread().start()


JMM(Java Memory Model):

volatile 证数据的可见性，但不能保证数据的原子性
synchronized 两者都能保证

乐观锁(Optimistic Locking)与悲观锁(Pessimistic Locking)

二次复习:
在 Java 中，JVM 可以理解的代码就叫做字节码(bytecode)（即扩展名为 .class 的文件）
字节码并不针对一种特定的机器，因此，Java 程序无须重新编译便可在多种不同操作系统的计算机上运行

JAVA和C++区别:
Java 不提供指针来直接访问内存，程序内存更加安全
Java 的类是单继承的，C++ 支持多重继承；虽然 Java 的类不可以多继承，但是接口可以多继承
Java 有自动内存管理垃圾回收机制(GC)，不需要程序员手动释放无用内存

单行注释 //
多行注释 /*
        */
文档注释 /**
        */

方法:
无参数(parameter)无返回
public void xx() {
}

// 下面这个方法也没有返回值，虽然用到了 return
public void f(int a) {
    if (...) {
        // 表示结束方法的执行,下方的输出语句不会执行
        return;
    }
    System.out.println(a);
}

有参数无返回值的方法
public void f2(Parameter 1, ..., Parameter n) {
    //......
}

有返回值无参数的方法
public int f3() {
    //......
    return x;
}

有返回值有参数的方法
public int f4(int a, int b) {
    return a * b;
}

重载(Overloading)和重写(Overriding)有什么区别？
重载就是同样的一个方法能够根据输入数据的不同，做出不同的处理
重写就是当子类继承自父类的相同方法，输入数据一样，但要做出有别于父类的响应时，你就要覆盖父类方法



StringBuilder s = new StringBuilder();
s.append();

Exception & Error

Exception 是可以处理的错误
Error 是不可以处理的错误

Generics

ArrayList<E> extends AbstractList<E>

public class Generic<T> {
    private T key;
    public Generic(T key) {
        this.key = key;
    } 
    public T getKey() {
        return key;
    }
}

Generic<Integer> test = new Generic<Integer>(12345);

public static <E> void printArray(E[] inputArray) {
    for (E element : inputArray) {
        System.out.println(""%s" , element);
    }
}

public static void main(String[] args) {
    TreeMap<Person, String> treeMap = new TreeMap<Person, String>(new Comparator<Preson> {
        @Override
        public int compare(Person person1, Person person2) {
            int num = person1.getAge() - person2.getAge;
            return Integer.compare(num, 0);
        }
    });
}

try (InputStream fis = new FileInputStream("input.txt")) {
    System.out.println("number" + fis.available());
    int content;
    long skip = fis.skip(2);
    while (content = fis.read() != -1) {
        System.out.print((char) content);
    }
} catch (IOException e) {
    e.printStackTrace();
}



###一些重点
重载(Overload)和重写(Overwrite)有什么区别

重载就是同样的一个方法能够根据输入数据的不同，做出不同的处理
重写就是当子类继承自父类的相同方法，输入数据一样，但要做出有别于父类的响应时，你就要覆盖父类方法 [外部样子不能改变，内部逻辑可以改变]

面向对象基础
另外，面向对象开发的程序一般更易维护、易复用、易扩展

构造方法(constructor)
名字与类名相同
没有返回值
生成类对象时自动执行
Can not be override but can be overload

面向对象三大特征
封装
Getter & Setter
封装是指把一个对象的状态信息（也就是属性）隐藏在对象内部，不允许外部对象直接访问对象的内部信息

继承
子类拥有父类对象所有的属性和方法（包括私有属性和私有方法），但是父类中的私有属性和方法子类是无法访问，只是拥有
子类可以拥有自己属性和方法，即子类可以对父类进行扩展

多态


接口和抽象类

== 和 equals() 区别
对于基本数据类型来说，== 比较的是值。
对于引用数据类型来说，== 比较的是对象的内存地址
S

String, StringBuffer, StringBuilder

异常
Throwable
Exception   Error

Exception :程序本身可以处理的异常，可以通过 catch 来进行捕获
Error：Error 属于程序无法处理的错误 

try-catch-finally 如何使用

try {
    System.out.println("Try to do something");
    throw new RuntimeException("RuntimeException");
} catch (Exception e) {
    System.out.println("Catch Exception -> " + e.getMessage());
} finally {
    System.out.println("Finally");
}
finally 块里的语句都会被执行。当在 try 块或 catch 块中遇到 return 语句时，finally 语句块将在方法返回之前被执行
不要在 finally 语句块中使用 return

finally 之前虚拟机被终止运行的话，finally 中的代码就不会被执行
程序所在的线程死亡。
关闭 CPU

JAVA pass by value

JAVA garbage collection
但是并不推荐下面做法
大量对象的创建和销毁时，手动触发垃圾回收可以帮助释放内存并提高应用程序的性能


JAVA 集合(Collection)

Collection Framework -> Set List Queue
Map Framework -> Map

List 储存元素有序,可重复
Set 储存元素不可重复
Queue 特定顺序 FIFO
Map Key,Value pair -> KEY non order but not repeatable, VALUE non order can be repeatable

List
ArrayList: Object[]
Vector: Object[]
LinkedList

Set
HashSet
LinkedHashSet
TreeSet

Queue
PriorityQueue: Object[]
DelayQueue
ArrayDeque

Map
HashMap
LinkedHashMap
Hashtable
TreeMap

Array vs ArrayList

ArrayList ->Thread NON safe
Vector ->Thread safe

Map
HashMap and Hashtable
for (Map.Entry<Integer, String> entry : map.entrySet())

list.toArray(new String[0]);
