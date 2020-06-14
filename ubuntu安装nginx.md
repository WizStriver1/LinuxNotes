# nginx介绍
Nginx发音的“engine x”是一个免费的开源高性能HTTP和反向代理服务器，负责处理互联网上一些最大的网站的负载。 本教程将概述在Ubuntu 18.04机器上安装和管理Nginx的步骤。

# 安装Nginx
Nginx的软件包在Ubuntu默认软件仓库中可用。 安装非常简单，只需键入以下命令：
```
sudo apt update
sudo apt install nginx
```

安装完成后，请检查Nginx服务的状态和版本：
```
$ sudo systemctl status nginx
```
输出：
```
● nginx.service - A high performance web server and a reverse proxy server
   Loaded: loaded (/lib/systemd/system/nginx.service; enabled; vendor preset: enabled)
   Active: active (running) since Mon 2020-06-08 17:20:38 CST; 10min ago
     Docs: man:nginx(8)
  Process: 14347 ExecStart=/usr/sbin/nginx -g daemon on; master_process on; (code=exited, status=0/SUCCESS)
  Process: 14346 ExecStartPre=/usr/sbin/nginx -t -q -g daemon on; master_process on; (code=exited, status=0/SUCCESS)
 Main PID: 14348 (nginx)
    Tasks: 3 (limit: 4915)
   CGroup: /system.slice/nginx.service
           ├─14348 nginx: master process /usr/sbin/nginx -g daemon on; master_process on;
           ├─14349 nginx: worker process
           └─14350 nginx: worker process

Jun 08 17:20:38 server4 systemd[1]: Starting A high performance web server and a reverse proxy server...
Jun 08 17:20:38 server4 systemd[1]: Started A high performance web server and a reverse proxy server.
```
查看版本
```
sudo nginx -v
```
输出：
```
nginx version: nginx/1.14.0 (Ubuntu)
```

# 配置防火墙

如果您正在运行防火墙，则还需要打开端口80和443。
```
sudo ufw allow 'Nginx Full'
// Rules updated
// Rules updated (v6)
```

您可以通过以下方式验证更改：
```
ufw status
```
输出：
```
Status: inactive
```

# 测试安装
在您选择的浏览器中打开http://YOUR_IP，您应该能够看到默认的Nginx登录页面，如下所示：

使用systemctl管理Nginx服务
您可以像任何其他systemd单位一样管理Nginx服务。 要停止Nginx服务，请运行：
```
sudo systemctl stop nginx
```
要再次启动，请键入：
```
sudo systemctl start nginx
```
重新启动Nginx服务：
```
sudo systemctl restart nginx
```
在进行一些配置更改后重新加载Nginx服务：
```
sudo systemctl reload nginx
```
如果你想禁用Nginx服务在启动时启动：
```
sudo systemctl disable nginx
```
并重新启用它：
```
sudo systemctl enable nginx
```

作者：六寸光阴丶
链接：https://www.jianshu.com/p/321bfe01aee4
来源：简书
著作权归作者所有。商业转载请联系作者获得授权，非商业转载请注明出处。