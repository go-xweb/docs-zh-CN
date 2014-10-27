
## 模板事件

* BeforeRender方法
* AfterRender方法

# Action事件

* Init方法
* Before方法
* After方法

Action的方法可以有不同的返回值。不同的返回值所对应的输出也不相同：

1. 如果返回值为error，则检查error是否为nil，如果不为nil，则输出错误信息
2. 如果返回值为string，则将string写到body
3. 如果返回值为[]byte，则输出二进制数据。