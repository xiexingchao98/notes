渲染元素

使用 `ReactDOM.render(ele, node)` 将元素挂载到指定节点中。

该节点由 React DOM 管理。

条件渲染

常规

```react
let button

if (isLoggedIn) {
    button = <Button>Logout</Button>
} else {
    button = <Button>Login</Button>
}

return <div>{button}</div>
```



内联

逻辑与

```react
isLoggedIn &&
<h2>
	Welcome~
</h2>
```

因为当 `isLoggedIn == true` 时，表达式的值总是为 `expression` 。



三目运算符

简单表达式

```react
<p>{isLoggedIn ? 'user' : 'guest'}</p>
```

复杂表达式

```react
return (
    {isLoggedIn ? (
     <p>user:xxxxx</p>
     ) : (
	 <p>guest</p>	
	)}
)
```

