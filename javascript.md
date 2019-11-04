运算符号中，字符串会隐式的转成数字。

`'8' % 4 (=0)`

在字符串拼接中，数字会隐式的转成字符串。 

`console.log("abc" + 123)`

暂时性死区

https://www.nowcoder.com/questionTerminal/07cb7faf3a4a49e986a1bd7d8da2ed50

基本数据类型

`null, undefined, boolean, string, number, object, symbol(new in es6)`

不支持冒泡的事件

https://www.nowcoder.com/questionTerminal/d1c3e4efb5024d5b9b6fcb84b4f2cc02

拓展运算符

```javascript
let nums = [1,2,3]
function printnums(a,b,c) {
    console.log(a,b,c)
}
printnums(nums[0], nums[1], nums[2])
printnums(...nums)
```

