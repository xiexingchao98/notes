管道通信

半双工通信

线程启动

```java
thread.start()
thread.run()
```

https://www.nowcoder.com/questionTerminal/76ccde3a3e9e435daf2058910d3b4d1b

Stub存根

https://www.nowcoder.com/questionTerminal/8b992ee9de5e40bb84f6fd29e69d842d

字节、字符流

https://www.nowcoder.com/questionTerminal/b59f18ff7d1a49c19aa66886b04ce347

Applet

线程启动、入口

https://www.nowcoder.com/questionTerminal/fefb0691a35444198c36e8ce0d19c8d9

Java与Unicode

Java 一律采用 Unicode 编码，每个字符占用 2 个字节。

Java 虚拟机使用 UTF-16 保存字符。

UTF-8 中中文占 3 个字节，英文占 1 个字节。

https://www.nowcoder.com/questionTerminal/20766232d1eb45c5a37457953438f133

try catch return 问题

finally 会覆盖 try 中的 return 值

https://www.nowcoder.com/questionTerminal/5a6ea98ed42347fe81c950a1a206dc7e

构造函数

JVM 默认提供无参构造函数。

https://www.nowcoder.com/questionTerminal/9c32fe6e1dd545e5af6076b71b42f4d3

Java初始化顺序

父类静态代码块 -> 子类静态代码块 -> 父类普通代码块 -> 父类构造函数 -> 子类普通代码块 -> 子类构造函数

真假数组

内存连续为真数组。否则为假数组。

数组元素在内存中一个接一个线性存放，通过第一个元素就能访问之后的元素，加上下标检测，避免了数据覆盖的可能性。

https://www.nowcoder.com/questionTerminal/a08eff2849b343d3b636f8a370d10d30

Servlet

`Servlet.getInitConfig()` 获取初始化参数

Static 方法

`static` 方法中不存在 `this` 引用。

GC

GC 是自动运行的，不能够强制立刻进行垃圾回收。即垃圾回收不能确定具体的时间。

调用 `System.gc()` 只是能给 `GC` 建议回收垃圾，具体的执行仍然取决于 `GC` 自己的判断。

https://www.nowcoder.com/questionTerminal/4650487daf784a0bbffdeb523dd536b5

垃圾回收在 JVM 中的优先级非常低。

垃圾回收并不能保证不会发生内存溢出。

进入 DEAD 的线程，仍旧可以恢复，之后 GC 也并不会进行回收。



Floor / Round / Ceil 区别

`floor()` 以 `double` 类型返回小于等于输入的整数

`round()` 以 `long` 类型返回最接近输入的值

`ceil()` 以 `double` 类型返回大于等于输入的整数

```java
double a = 1.5;
System.out.println("floor => " + Math.floor(a));
System.out.println("round => " + Math.round(a));
System.out.println("ceil => " + Math.ceil(a));
// floor => 1.0
// round => 2
// ceil => 2.0
```



String / StringBuilder / StringBuffer 区别

String 不可变

StringBuffer 线程安全

StringBuilder 线程不安全，但是单线程情况下比 StringBuffer 要快

> JDK 1.5 新增



集合

Collection 是所有集合中的根接口。集合代表一组对象，或者说拥有一组元素。有些集合允许重复元素，有些不允许。

常见集合：Set、List、Queue

List 是有序列表，允许重复元素。某些情况下，最好使用迭代器来访问每一个元素，如果不了解每种获取元素的防法，这可能会造成性能损耗。

实现了 List 接口：

ArrayList：允许任意类型值，包括 null 值。它是不同步的。

Set 是无序集合，不允许重复元素。

实现了 Set 接口：

HashSet：允许 null 值。

Queue 队列接口。

实现了 Queue 接口：

Deque：读作 'deck' ，双向队列。



跨平台：Java 文件通过 JVM 编译成字节码文件（class），然后其他操作系统将该字节码文件编译成机器码文件执行。



JAR 与 ZIP 文件大同小异，JAR 额外包含 META-INF 文件夹。



子类父类构造

子类构造函数必须调用父类构造防法。当父类中声明有参构造函数后，而子类并未显示调用，此时会抛出编译异常。默认情况下子类只会调用父类的无参构造函数。



final

修饰变量表示常量。

修饰类表示不可继承。

修饰方法表示不可重写。

修饰方法参数表示最终参数（不可变）。

不可修饰接口和抽象类。





ClassLoader

加载顺序如下：

1. Bootstrap ClassLoader 启动类加载器

2. Extention ClassLoader 拓展类加载器

3. App ClassLoader 程序类加载器

装载类时，如果该类不存在，则会抛出异常。





JSP 九大内置对象



异常结构

Throwable

Error

Exception

 



Servlet 生命周期

init()

service()

destroy()



值、引用传递



解决哈希冲突方法

开放地址法、拉链法、再散列法

HashMap 线程不安全，冲突采用拉链法解决。KV均允许 null 值。底层采用数组实现，每个数组元素为一个 Entry ，它包含键、值以及指向下一个元素的指针，相当于链表。



局部变量需要在初始化后使用，否则会抛出异常。

成员变量可以不初始化使用，它包含默认值。



运算符

`^` 为异或运算符。

当两个操作数中均为 byte, short, int, char 之一时，它们均会被转换成 int 类型参与运算。

当两个操作数均被 final 修饰时，会根据等式右边的变量类型自动进行结果转换。  



设计模式

创建型设计模式：

+ 单例模式
+ 工厂模式
+ 原型模式

结构型设计模式：

+ 桥接模式
+ 适配器模式
+ 装饰模式（不用继承便可实现拓展性，非常灵活）
+ 代理模式
+ AOP 模式

行为型设计模式：

+ 观察者模式





反射

`getDeclaredMethods` 获取类中所有已经声明的方法对象，包括 public、private、proetcted、default 修饰的方法，不包括从父类、接口继承实现的方法。

`getMethods` 获取所有公开的方法对象，包括从父类、接口继承实现的方法。 



String

String 底层由 Char 数组构成。 Char 的大小为 2 Byte 。



Socket 通信



JVM 内存区域

off-heap 堆外内存。对象序列化后存储在堆外内存中，它不会被 GC 收集清理，再次使用时需要反序列化。

新生代、老生代。



修饰符

synchronized，修饰代码块或者方法，同一时刻只有一个线程能够执行该段代码。

volatile，修饰的变量每次访问，线程都会从共享内存区域中重新读取值，当该变量的值发生了变化时，会强制线程将心值写入共享内存。以确保不同线程在同一时刻读取到相同的值。

transient，对象序列化时会跳过被该修饰符修饰的变量。





Vector / ArrayList

均实现了 List 接口。Vector 支持同步，ArrayList 不支持同步。非多线程情况下，优先使用 ArrayList 。



Hashtable / HashMap / ConcurrentHashMap

HashMap 实现了 Map 接口，不支持同步。

Hashtable 实现了 Dictonary 接口，支持同步。

ConcurrentHashMap 实现了 Map 接口，支持同步。

非多线程情况下，优先使用 HashMap，高并发场景下使用 ConcurrentHashMap 。



HashSet

HashSet 实现了 Set 接口，不支持同步。



Integer 缓存范围 -128 - 127



JSP 静态、动态包含

静态包含是将文件内容直接并入主文件，再进行翻译，因此不允许同名变量。

动态包含是将 JSP 编译后并入主文件。