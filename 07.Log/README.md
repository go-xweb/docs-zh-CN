# Log

xweb默认使用github.com/go-xweb/log来作为log组件，默认输出到屏幕上，如果希望输出到文件，可以自定义log，比如：
```Go
f, err := os.Create("server.log")
    if err != nil {
        println(err.Error())
        return
    }

logger := log.New(f, "", log.Ldate|log.Ltime)

xweb.AddAction(&MainAction{})
xweb.SetLogger(logger)
```

以上代码将输出log到server.log。