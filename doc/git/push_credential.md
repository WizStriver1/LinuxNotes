# 进入根目录
```
cd ~
```
# 创建credential文件
```
touch .git-credentials

vim .git-credentials
```
输入以下内容:
```
https://{username}:{password}@github.com
```
# 添加git config内容
在bash中输入以下内容
```
git config --global credential.helper store
```
执行完之后，会发现出现以下内容：
```
[credential]
    helper = store
```

接下来git push时，只要第一次输入username 和 password 就行了，以后将不需要第二次输入
