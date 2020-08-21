---
title: "为git Bash设置socks5代理，加速GitHub Git Clone"
date: 2020-08-18T18:23:08+08:00
draft: false
--- 

本文假设你已经有了一个 socks5 协议的代理了，也就是说已经有了代理的环境，且能顺利访问404网站。

因为git bash是不走系统的代理的，所以需要单独配置。

要清楚你自己的socks代理地址与端口，通常为 127.0.0.1:1080。

## 一、使用https clone项目
1. 打开git bash依次输入这两条命令，输入之后会在.gitconfig文件内添加这两行配置
    ```
    git config --global http.proxy 'socks5://127.0.0.1:1080'
    git config --global https.proxy 'socks5://127.0.0.1:1080'
    ```
    这就配置好了，现在使用`git clone https://github.com/username/repo.git`方式clone项目就应该很快了，具体与你代理速度有关

2. 查看有没有设置成功用以下命令
    ```
    git config --get --global http.proxy
    git config --get --global https.proxy
    ```

3. 取消代理设置用以上命令
    ```
    git config --global --unset http.proxy
    git config --global --unset https.proxy
    ```


## 二、使用ssh clone项目
1. 在你的.ssh文件夹（路径：C:\Users\n你的电脑用户名\.ssh）添加一个config文件，就新建一个txt文本文件把名字改成config就行，没有后缀，然后把下面的代码复制粘贴，然后保存，记得把ip与端口改为你自己的。
    ```
    Host github.com
    User git
    IdentityFile "C:\Users\Alan\.ssh\id_rsa"
    ProxyCommand connect.exe -S 127.0.0.1:1080 %h %p
    ```

2. 上面代码里面由一个`connect.exe`，这是一个命令行软件，把这个软件下载了后connect.exe文件放在上面说的.ssh文件夹内就行。
[connect下载地址](https://bitbucket.org/gotoh/connect/downloads/)

3. 完成上面设置好后使用`git clone git@github.com:username/repo.git`ssh方式clon应该就很快了