# Errors: Peer reports incompatible or unsupported protocol version.

## 问题描述

centos 操作系统
git clone 项目时出现类似如下错误：

> fatal: unable to access 'https://github.com/xxx/xxx.git/':Peer reports incompatible or unsupported protocol version.

## 解决方法

```
# sudo yum update -y nss curl libcurl
```
