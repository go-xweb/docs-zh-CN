# Https

启动https服务可以通过生成config
```Go
config, err := xweb.SimpleTLSConfig("cert.pem", "key.pem")
    if err != nil {
        fmt.Println(err)
        return
    }

    xweb.RunTLS("0.0.0.0:9999", config)
```