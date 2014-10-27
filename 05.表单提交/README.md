# 变量映射

## 获取Form变量

通过Action的如下方法可以获取变量：

* GetSlice
* GetString
* GetInt
* GetBool
* GetFloat
* GetFile
* GetForm

## 自动映射

通常我们通过http.Request.Form来获得从用户中请求到服务器端的数据，这些数据一般都是采用name，value的形式提交的。xweb默认支持自动将这些变量映射到Action的成员中，并且这种映射支持子Struct。例如：

```Go
type HomeAction struct {
    *Action
    Name string
    User User
}
```

那么当页面为：
```Go
<form>
<input name="name"/>
<input name="user.id"/>
</form>
```
时，变量会自动映射到`HomeAction`的成员`Name`和`User`上。

如果希望关闭
那么可以在`Actions`的`Init()`方法中通过`Action.Option.AutoMapForm = false`来进行关闭。

## 手动映射

如果希望手动进行映射，那么，可以通过`Action.MapForm`方法来进行映射，例如：

```Go
type User struct {
    Id   int64
    Name string
    Age  float64
}
func (c *MainAction) Init() {
    c.Option.AutoMapForm = false
    c.Option.CheckXrsf = false
}
func (c *MainAction) Parse() error {
    if c.Method() == "GET" {
        return c.Write(page)
    } else if c.Method() == "POST" {
        var user User
        err := c.MapForm(&user, "")
        if err != nil {
            return err
        }
        return c.Write("%v", user)
    }
    return nil
}
```

如果在提交的表单中有一个key为name的键值对，则对应的value就会自动赋值到Name这个filed中，这种命名也可以通过`.`来进行传递。如：上述代码中的User结构体可以通过user.id的key来对期成员赋值。
