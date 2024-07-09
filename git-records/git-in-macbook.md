## 如何在MacBook上配置git环境

### 安装git
+ MacBook自带git，可以在终端中输入git --version进行验证是否安装git。
+ 若不想使用MacBook自带的git，可以自行下载Hoembrew，然后使用Homebrew命令进行安装。


### 配置用户名与邮箱
+ ```
  git config --global user.name "ccc"
  git config --global user.email "userEmail"
  需要注意的是，两行命令需要同时输入后再会车，不然不会生效
  ```
  
### 生成公钥与密钥
+ git服务器使用ssh公钥进行认证，一般来说公钥存储在～/ssh中，可以使用下述命名验证：
+ ```
  open ~/.ssh
  若提示没有该文件表示并没有生成公钥与秘钥，可以使用
  mkdir ~/.ssh进行创建
  创建ssh文件后使用命令生成公钥与秘钥
  ssh-keygen -t rsa -C "your_email"
  输入命令后一直会车即可，不需要输入电脑密码
  ```
+ 公钥与秘钥生成后，会存放在/users/${yourName eg：ccc}/.ssh文件夹下 
    + id_rsa为私钥
    + id_rsa.pub为公钥

### 配置公钥与密钥
+ 使用命令 cat ～/.ssh/id_rsa.pub获取公钥内容配置在GitHub-setting-SSH and GPG keys中，
title自定义即可。


### 本地登录GitHub
+ 使用命令 SSH -T git@github.com 若出现 hi 你的GitHub账号名即登录成功。

### 提交本地代码至GitHub普遍流程
+ 进入本地工程文件夹位置的终端窗口，可以使用com+shift+.快捷健查看该工程中是否有
.git文件，因为在macOS中一般情况下该文件是隐藏的。
+ ```
  若该工程没有.git文件
  git init 若已经存在，跳过该命令
  git add . 添加当前工程所有修改文件到本地暂存区
  git status 查看添加到本地暂存区的文件
  git commit -m "your commit describtion" 将本地暂存区提交到本地仓库
  若是第一次提交代码
  git remote origin add 你需要连接的远程仓库的url
  git remote -v 查看你刚才添加的远程仓库地址
  git branch master 创建master分支
  git push -u origin master 提交本地仓库代码至远程仓库 
  ```