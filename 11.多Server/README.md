# Server

默认的Server为mainServer，这是一个全局变量。

如果我们只需要一个server和一个app，则可以直接调用
```Go
xweb.AddAction
xweb.AutoAction
xweb.AddRouter
xweb.Run
```
即可运行服务器。