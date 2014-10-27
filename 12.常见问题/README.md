# 常见问题

* 问：为什么post提交时会出现xsrf error的错误显示？
   答：因为默认开启了防xsrf措施，因此必须在表单中加入`{{XsrfFormHtml}}`才可以，或者将`app.AppConfig.CheckXrsf = false`

* 如果开启了静态文件自动加载和模板文件自动加载，则请确保再启动服务之前调用过 ulimit -n 将最大文件打开数目调整到了一个合适的数值。
