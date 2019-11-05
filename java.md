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



synchronized 代码块



