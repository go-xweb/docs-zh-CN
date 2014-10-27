# 特性

* 在一个可执行程序中多Server(http,tls,scgi,fcgi)，多App的支持
* 简单好用的路由映射方式
* 静态文件及版本支持，并支持自动加载，默认开启
* 改进的模版支持，并支持自动加载，动态新增模板函数
* session支持
* validation支持

# 安装

在安装之前确认你已经安装了Go语言. Go语言安装请访问 [install instructions](http://golang.org/doc/install.html). 

安装 xweb:

    go get github.com/go-xweb/xweb

# Hello Xweb
先来看一个最简单的示例：
```Go
package main

import (
    "github.com/go-xweb/xweb"
)

type MainAction struct {
    *xweb.Action

    hello xweb.Mapper `xweb:"/(.*)"`
}

func (c *MainAction) Hello(xweb string) error {
    return c.Write("hello %v", xweb)
}

func main() {
    xweb.AddRouter("/", &MainAction{})
    xweb.Run("0.0.0.0:9999")
}
```

## Examples

请访问 [examples](https://github.com/go-xweb/xweb/tree/master/examples) folder

## 案例

* [xorm.io](http://xorm.io) - [github.com/go-xorm/website](http://github.com/go-xorm/website)
* [Godaily.org](http://godaily.org) - [github.com/govc/godaily](http://github.com/govc/godaily)

## 文档

[快速开始](https://github.com/go-xweb/xweb/tree/master/docs/intro.md)

源码文档请访问 [GoWalker](http://gowalker.org/github.com/go-xweb/xweb)