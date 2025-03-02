# Git 相关异常处理

### 1. 使用 Git 时报错 `Connection reset by xxx.xxx.xxx.xxx port 22`

- 异常报错如下：

``` bash
Connection reset by 20.205.243.166 port 22
fatal: Could not read from remote repository.

Please make sure you have the correct access rights
and the repository exists.
```

- 解决方法：

上述问题通常是电脑代理导致的，需要给 Git 设置代理，即可解决问题：

修改 `C:\Users\.ssh` 目录下的 `config` 文件，添加如下 `ProxyCommand` 相关内容：

``` bash
Host github.com
    port 22
    User git
    HostName github.com
    PreferredAuthentications publickey
    IdentityFile ~/.ssh/id_rsa_github
    # 添加下面这一行，端口号为你开启代理的端口号，这里7890是Clash默认端口号
    ProxyCommand connect -S 127.0.0.1:7890 -a none %h %p
```