# ftp命令的基本用法

## ftp 连接 ftp 服务器
```
ftp -v -d -i -n -g [hostname]
```
>   -v 显示远程服务器的所有响应信息；
>   -n 限制ftp的自动登录，即不使用；
>   -n etrc文件；
>   -d 使用调试方式；
>   -g 取消全局文件名。 

## 查看ftp的命令
```
?
```
### 查看命令的说明
```
? command
```

## 下载命令
```
get filename path
```
> filename 为当前文件夹下要下载的文件名
> path 为需要保存到local的文件名
