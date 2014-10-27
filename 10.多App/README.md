# App

xweb支持在一个应用程序里存在多个App，每个App有自己独立的配置，不同的根路径，独立的Session管理等等。

## 创建App

App在创建时调用`NewApp`时必须指定此app的映射规则，挂载到服务器的路径
```Go
app := xweb.NewApp("/main")
```

## 获取系统默认App
默认的系统已经创建了一个App，并且指向/目录，获取默认App可用如下代码：
```Go
app := xweb.RootApp()
```