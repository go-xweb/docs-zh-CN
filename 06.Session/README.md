# Session

## 基础应用

默认Xweb的Session支持是开启的，如果需要关闭Session支持，可以：
```Go
xweb.RootApp().AppConfig.SessionOn = false
```

开启了Session支持后，可以通过Action的方法`SetSession`，`GetSession`，`DelSession`来对Session操作。同时，如果在模板中，可以调用`{{session "sessionId"}}`来获取Session中的内容。

## 高级应用

Session组件是引用的github.com/go-xweb/httpsession，支持一些自定义方式。
