## Golang

[Go语言圣经](https://books.studygolang.com/gopl-zh/)

类型断言（Comma:ok）

`val, ok = a.(T)`

`val` 为对应类型的值

`ok` 为该值是否为 `T` 类型

https://blog.csdn.net/MaxCoderLlj/article/details/80105040

https://blog.csdn.net/u012807459/article/details/30050391



并发、并行

并发指的是同时有很多任务，可以选择串行处理或者并行处理。传统的单核CPU上，其实是一种并发，模拟出一种“并行”状态。多核CPU上，任务分配到不同CPU上，从物理上实现真正的并行。

并行指的是同一时刻处理多个任务。

https://www.zhihu.com/question/33515481



进程、线程、协程

进程是操作系统资源分配调度的基本单位。它拥有独立的地址空间，较为稳定，但是切换代价比较大。

线程是CPU分配调度的基本单位。它存在于进程之内，是进程的一个执行单元，与进程共享资源，共享进程内地址空间。

协程是一种更为轻量的线程。

https://www.cnblogs.com/lxmhhy/p/6041001.html



Goroutine

Go 语言中并发执行的单元。

https://books.studygolang.com/gopl-zh/ch8/ch8-01.html



Channel

为并发执行的函数间提供通信方式。

新建 Channel 时方向默认为双向。

eg: `chan <- int（发送）`， `<- chan int（接收） `

Channel 类似一个 `FIFO(First in First out)` 队列。



指针

Go 的指针不支持运算。是能够取地址 `&ptr` 或者取值 `*ptr` 。



this 指针

Go 中没有 this 指针。也就是说方法施加的对象是显式传递。



Vendor 目录

> 1.6 新增

将项目引用的外部源代码放置在项目的 `vendor` 目录下，编译时优先从 `vendor` 下寻找依赖包。

https://blog.csdn.net/hittata/article/details/52122071



import 最后一个元素是路径

`import 'github.com/demo'`

`demo` 是路径，包名指的是 `demo.Parse()` 中的 `demo`



CGO

调用C的模块、静态库、动态库

无法直接支持C++，因其没有 ABI （应用程序二进制接口规范），可以使用 C 封装 C++ 来实现 Golang 对 C++ 的调用。

https://www.nowcoder.com/questionTerminal/820c9fc3db8d4e26b3226a7329e9f2bd



函数返回值的错误设计

失败原因单个，返回 `bool`

失败原因多个，返回 `error`

无失败原因，则不返回 `bool` 或者 `error`

偶尔性、不可知性错误 ，如果可以重试几次得到正确结果，则应避免立即返回 `bool` 或者 `error`



Go vet

检查源代码中静态错误的工具



Struct tag

```go
struct Person {
	Name string `json:"name"`
}

```

在结构体与 `json` 相互转换解析时，维持的一种的映射关系



匿名函数组合实现继承

```go
struct Base {

}

func (*base Base) fun() {

}

struct A {
	Base
}

func (*a A) fun() {

}

func main() {
    a := A{}
    a.Base.fun()
    a.fun()
}
```



内存泄漏

由程序动态分配的内存，后续既不继续使用，也不进行回收（释放），导致的内存资源上的浪费，从而影响程序的运行速度和系统稳定性。

Go 中使用 `pprof` 包来检测内存泄漏。

https://www.nowcoder.com/questionTerminal/1fb0aa0ebbba44c9bf587136550ca64b



nil 值

`nil` 值只能赋值给Slice（切片）、映射（Map）、Interface（接口）、Func（函数）、(*) Func（方法）、Channel（通道） 以及指针变量

![](C:\Users\xiexi\Pictures\242025553_1564399633384_3538CAEF7C819BA4AD8BC262C5D1EE6D.png)

https://www.nowcoder.com/questionTerminal/48bf04398a9e4e5d8133e133f575abfe



Defer 调用顺序

出现多个 Defer ，其执行顺序类似于堆栈，先进后出，后进先出。

```go
defer println("1")
defer println("2")
defer println("3")
println("4")
// output: 4 3 2 1
```



方法

可以给任意自定义类型添加方法

```go
type A int
func (a A) fun() {

}
```



值类型与引用类型区别

值类型内存地址在栈中，由变量直接保存其值

引用类型内存地址在堆中，由变量保存指向其值的地址

https://www.nowcoder.com/questionTerminal/fb4a8445cac742e4b6af69cabe692711



接口查询

本质就是类型断言

只有在运行期间通过反射机制才能够确定其类型和真实值



数据类型转 JSON

Golang 中的大部分数据类型都可以转成有效的 JSON 文本，除了 complex、函数、channel 等。

指针类型也可以转，这取决于它所指向的具体数据类型，在做转换时系统会隐式转换，表面上是序列化指针，其实是序列化指针所指向的对象。

https://www.nowcoder.com/questionTerminal/5f062c4dbd004f37841df3733c7ebb01



匿名变量

如果想忽略函数返回值中的某一个，可以使用 `_` 代替变量名。



Defer 可能触发异常情况

函数结束后执行 `close` 操作，但是此时文件为空不存在，所以无法正常关闭。

```go
链接：https://www.nowcoder.com/questionTerminal/a7d3e8d79145451c9901eb62490fc583
来源：牛客网

file, err := os.Open("/null")
defer func() {
    err := file.Close()
    if err != nil {
        fmt.Println("close error: ", err)
    } else {
        fmt.Println("close no error")
    }
}()
 
if err != nil {
    fmt.Println("open error! ", err)
    return
}
```

https://www.nowcoder.com/questionTerminal/a7d3e8d79145451c9901eb62490fc583



错误和异常

错误指的在可能出现问题（可以预想到问题的发生）的情况。

异常指的是预料之外的情况。

错误属于业务过程中的一部分，异常则不属于。

https://www.nowcoder.com/questionTerminal/1ed1e4ac2dc142f980ef995b4dd973aa



指针

Go 中可以自动解引用（1次），所以可以直接 `ptr.attr` 。

```go
ptr.attr
(*ptr).attr
```

https://www.nowcoder.com/questionTerminal/b5fa6c5f96814072a51b45552ab2802f



结构体序列化和反序列化

小写字母开头的变量在序列化时不会导出，称作未导出变量。

反之亦然，在反序列化时，未导出变量的值为默认的零值。



初始化函数 `init()`

一个包中可以有任意个 init 

init 不可以被显示的调用

main 包中只能有 1 个 main 函数

初始化执行顺序：初始化导入包的常量、变量 -> 初始化本包的常量、变量、 -> 初始化导入包的 init 函数 -> 初始化本包的 init 函数

https://www.nowcoder.com/questionTerminal/46cfb9ebd9a74fba9611cf35c6c2dca9



接口介绍以及类型断言

接口是隐式实现的，无需导入相应的包。只要类型具备了接口定义的所有方法，其就被是做实现了该接口。

https://www.nowcoder.com/questionTerminal/01f4ded3eae745948cba1e04742f5e27

https://golangbot.com/interfaces-part-1/



函数声明

返回参数中，要么都具备返回参数名，要么都不具备（只包含类型）。



内存逃逸（没看懂）

只要存在指针指向/引用一个变量，该变量内存空间就不会被回收。

局部变量的生命周期由该变量是否被引用决定，被引用则创建在堆上，否则创建在栈上。

https://www.nowcoder.com/questionTerminal/3a33e0d0c2c64708b90e72fd806877ab

http://www.agardner.me/golang/garbage/collection/gc/escape/analysis/2015/10/18/go-escape-analysis.html



常量

常量指的是在编译阶段就能够确定数据类型的数值。

常量可以存储布尔值、字符串、数字值（整数、浮点数、复数）。

https://www.nowcoder.com/questionTerminal/a1426491669b4180838c9c5401e97ad6



Select 语句

https://golangbot.com/select/

select 主要用来处理异步 IO 问题。每条 case 语句中的条件未 IO 操作（channel IO ）。

https://www.nowcoder.com/questionTerminal/5d952d55fc154046b626ff5a96ea836f



Channel

ch1 为有缓冲通道， ch2 为无缓冲通道。

有缓冲通道会在缓冲区已满时阻塞。无缓冲通道会一直阻塞，直至传输完成。

```go
ch1 := make(chan int, 1)
ch2 := make(chan int)
```

`nil channel` 为未初始化的 `channel` 。向未初始化的 `channel` 读写数据都会造成永久阻塞。

另外从已经关闭的 `channel` 读取数据只能获得零值。





编译器处理方式

https://www.nowcoder.com/questionTerminal/a8f1231d083a4f3eb253c6a7a0fd6db5



数组

```go
var nums1 []int32
nums2 := []int32{1, 2, 3}
```



字符串不可变

https://www.nowcoder.com/questionTerminal/deffaf9bf23245dda0b512579a164ca3



Make

`make` 用来创建slice、map、channel。

长度参数不可省略，容量参数可省略。

`Attention:` map 使用前必须初始化。

eg:

```go
// wrong
var m map[string]string
m["name"] = "jack"

// correct
var m map[string]string = make(map[string]string, 0)
m["name"] = "jack"

// correct
var m map[string]string = map[string]string{"name": "jack"}
m["email"] = "jack@gmail.com"
```



异常触发情况

空指针解析、下标越界、除数为0、调用panic函数。





Goto

Golang中支持 `goto` 语句。

eg:

```go
goto nxt
fmt.Println("hello 1")
nxt:
fmt.Println("hello 2")
```



自增自减

Golang 中 `++`、`--` 都是后置操作符，并且无返回值。



变量声明与初始化

```go
var a int = 10  // 完整的声明初始化方式
var a = 10  // 类型推断
a := 10  // 此种方式只能存在于函数内
```

https://www.nowcoder.com/questionTerminal/3f24c233ec384afdbbe34dd6913a6638



可变参数列表

`...` 在函数声明中表示可以接收任意数量的参数。

`...` 在调用函数时使用，表示将切片类型转换为多个参数传入。

```go
func add(int...)
add(1,2,3)
add([]int{1,2,3}...)
```

https://www.nowcoder.com/questionTerminal/bf57cb74840d4bc8b9c8a13f44e2f316