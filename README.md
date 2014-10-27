# xweb介绍

xweb是一个基于web.go开发的web框架，目前它和Java框架Struts有些类似。

# 技术支持

QQ群：369240307

# 更新日志

* **v0.2.1** : 自动Binding新增对jquery对象，map和array的支持。
* **v0.2** : 新增 validation 子包，从 [https://github.com/astaxie/beego/tree/master/validation](http://https://github.com/astaxie/beego/tree/master/validation) 拷贝过来。
* **v0.1.2** : 采用 [github.com/go-xweb/httpsession](http://github.com/go-xweb/httpsession) 作为session组件，API保持兼容；Action现在必须从*Action继承，这个改变与以前的版本不兼容，必须更改代码；新增两个模板函数{{session "key"}} 和 {{cookie "key"}}；Action新增函数`MapForm`
* **v0.1.1** : App新增AutoAction方法；Action新增AddTmplVar方法；Render方法的模版渲染方法中可以通过T混合传入函数和变量，更新了[快速入门](https://github.com/go-xweb/xweb/tree/master/docs/intro.md)。
* **v0.1.0** : 初始版本

# License
BSD License
[http://creativecommons.org/licenses/BSD/](http://creativecommons.org/licenses/BSD/)
