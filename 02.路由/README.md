# Action
xweb中最重要的struct是Action，绝大部分工作都围绕Action展开。

一个最简单的Action如下，这里需要注意必须是*xweb.Action，而不是xweb.Action
```
type MainAction struct {
    *xweb.Action

    hello xweb.Mapper
}

func (a *MainAction) Hello() error {
    return a.Write("Hello world!")
}

```

如上代码定义了一个简单的Action，实现了对`/login`请求的响应。当访问这个url时，会返回
`Hello world!`。更详细的讲解后面再继续，我们先看下如何来运行这个Action。

# 路由

添加路由主要由三个函数可以使用：

* AddRouter
添加一个路由到App下，并指定一个根路径。

```Go
xweb.AddRouter("/", new(MainAction))
```

* AddAction
添加一个Action的所有Mapper到App的父路径，相当于`AddRouter("/", new(MainAction))`，但是可以同时添加多个Action。

```Go
xweb.AddAction(new(MainAction), new(LoginAction))
// 相当于以下两句
// xweb.AddRouter("/", new(MainAction))
// xweb.AddRouter("/", new(LoginAction))
```

* AutoAction
AutoAction和AddAction稍微有一点区别，即以Action的前缀作为Router来添加，如：

```Go
xweb.AutoAction(new(MainAction), new(LoginAction))
// 相当于以下两句
// xweb.AddRouter("/main", new(MainAction))
// xweb.AddRouter("/login", new(LoginAction))
```

## Action路由映射

Mapper的路由规则有两种形式：

* 按照Mapper的命名

这时，这个路由即为Mapper的名字，对应执行的方法名为Title（mapper变量名）；如：
```Go
type MainAction struct {
    xweb.Action
    
    login xweb.Mapper
}

func (this *MainAction) Login() {

}
```
这时如果访问/login，就会执行Login方法。

* 按照Field对应的Tag语法

Tag语法用空格分为如下几部分：
GET|POST        方法名，多个方法中间用|分隔
/(.*)           路径名，可以采用正则表达式

```Go
type MainAction struct {
    xweb.Action
    
    hello xweb.Mapper `xweb:"GET|POST /(.*)`
}

func (this *MainAction) Hello(world string) {

}
```
这个时候，对任何地址的GET和POST请求才会调用Login方法，并且，正则表达提取的内容会以参数的形式传给Login方法。