# nginx 学习笔记

## nginx 运行

ubutun 下安装 nginx:

```bash
apt-get install nginx
```

指定配置文件运行 nginx

```bash
nginx -p ./ -c conf/nginx.conf
```

启动参数解释

> -p 运行工作路径
>
> -c 配置文件路径

立即停止

```bash
nginx -s stop
```

从容停止

```bash
nginx -s quit
```

重新加载

```bash
nginx -s reload
```

http 模块参数解释

- default_type: 默认返回类型
- return port content: 返回状态码+内容
- root: 静态文件代理路径
- index: 默认欢迎界面
- server_name: 相同端口下根据host分发
- add_header: 添加头
- proxy_hide_header: 隐藏头

https配置

生产ssl证书

```bash
# 生成一个RSA私钥
genrsa -des3 -out server.key 2048

# 生成CSR（证书签名请求）
openssl req -new -key server.key -out server.csr  

# 生成CRT证书
openssl x509 -req -days 3650 -in server.csr -signkey server.key -out server.crt

# 生成没有密码的key
openssl rsa -in ./server.key -out ./server_nopassword.key
````
