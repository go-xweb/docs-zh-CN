# Filter

如果要对每次请求都进行过滤，那么可以采用Filter来进行，Filter是一个接口，接口定义如下：
```Go
type Filter interface {
    Do(http.ResponseWriter, *http.Request) bool
}
```
如果返回true，则filter不会中断会继续执行下去，如果返回false，则会中断执行，输出到浏览器。

系统已经内置了一个LoginFilter，可以满足简单的登录需求。LoginFilter使用方法如下：
```Go
filter := xweb.NewLoginFilter(xweb.RootApp(), "userSessionId", "/login")
xweb.AddFilter(filter)
```
