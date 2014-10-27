# 模板

## 模板中的变量和函数

模板中可以使用的函数或者变量来源如下：

    1）Go模板自带的模板函数
    2）xweb内置的模板函数和变量
    3）通过Server.AddTmplVar或者AddTmplVars添加的函数或者变量
    4）通过App.AddTmplVar或者AddTmplVars添加的函数或者变量
    5）通过Action.AddTmplVar或者AddTmplVars添加的函数或者变量
    6）Action的公共变量和公共方法

## Go模板自带模板函数

这个请参见 [https://gowalker.org/text/template](https://gowalker.org/text/template)
   
## xweb内置的模板函数和变量

xweb内置的模板函数和Go模板函数一样，在模板中使用{{funcName ...}}形式调用。内置的变量使用{{.T.}}方式调用。

* `IsNil(a interface{}) bool`
判断一个指针是否为空

* `Add(left interface{}, right interface{}) interface{} `
整数或浮点数加法

* `Subtract(left interface{}, right interface{}) interface{}`
整数或者浮点数减法

* `Now()`
当前时间

* `UrlFor(args ...string) string`
返回一个route对应的url

* `FormatDate(t time.Time, format string) string`
日期格式化，格式方法和Go的格式方法相同

* `Eq(left interface{}, right interface{}) bool`
相等判断，go1.2以上请使用Go自带的eq

* `Html(raw string) template.HTML`
以html格式输出

* `Js(raw string) template.JS`
输出javascript代码

* `StaticUrl(url string) string`
自动为静态文件添加版本标识

* `XsrfName() string`
返回xsrf的cookie名称

* `XsrfFormHtml() template.HTML`
在表单中生成防xsrf的隐藏表单

* `XsrfValue() string`
自动生成的防xsrf随机值

* `session(key string) interface{}`
获取session的值

* `cookie(key string) interface{}`
获取cookie的指


## 通过xweb.AddTmplVar或者AddTmplVars添加的函数或者变量

通过xweb.AddTmplVar或者AddTmplVars添加的函数或者变量在MainServer的RootApp范围内有效，在模板中使用{{funcName ...}}形式调用函数。变量使用{{.T.}}方式调用。

## 通过App.AddTmplVar或者AddTmplVars添加的函数或者变量

通过App.AddTmplVar或者AddTmplVars添加的函数或者变量在此App范围内有效，在模板中使用{{funcName ...}}形式调用函数。变量使用{{.T.}}方式调用。

## 通过Action.AddTmplVar或者AddTmplVars添加的函数或者变量

通过Action.AddTmplVar或者AddTmplVars添加的函数或者变量在此Action范围内有效，在模板中使用{{funcName ...}}形式调用函数。变量使用{{.T.}}方式调用。

## Action的公共变量和公共方法

Action的公共变量，通过{{.xxx}}的方式调用，公共方法通过{{.xxx}}的方式调用


## 模板包含
xweb使用include函数来进行模板包含，而不使用template函数。

* `include(tmpl string) interface{}`
包含另外一个模版

包含方式如下：

```
{{include "head.tmpl"}}
```

在包含时，只有一个模板名参数，此时head.html模板中的变量和函数也自动由当前Action传入。
