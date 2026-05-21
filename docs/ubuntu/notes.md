## 配置git用户信息
```
sudo apt install git

acorus@ubuntu:/data/info/notes$ git config --global user.email "lingyugu9@gmail.com"
acorus@ubuntu:/data/info/notes$ git config --global user.name "acorus"

#ssh连接
acorus@ubuntu:/data/info/notes$ ssh-keygen -t ed25519 -C "lingyugu9@gmail.com"
acorus@ubuntu:~$ ssh -T git@github.com
Hi qi-ci! You've successfully authenticated, but GitHub does not provide shell access.

#绑定GitHub仓库
acorus@ubuntu:/data/info/notes$ git remote add origin git@github.com:qi-ci/mynotes

acorus@ubuntu:/data/info/notes$ git config list
user.name=acorus
user.email=lingyugu9@gmail.com
core.repositoryformatversion=0
core.filemode=true
core.bare=false
core.logallrefupdates=true
remote.origin.url=git@github.com:qi-ci/mynotes
remote.origin.fetch=+refs/heads/*:refs/remotes/origin/*

```
## Obsidian git初始化
```
git init

nano .gitignore
.obsidian/workspace*
.trash/

#创建主分支
acorus@ubuntu:/data/info/notes$ git branch -M main
acorus@ubuntu:/data/info/notes$ git push -u origin main

#提交
acorus@ubuntu:/data/info/notes$ git add .
acorus@ubuntu:/data/info/notes$ git commit -m "initial commit"
#上传
acorus@ubuntu:/data/info/notes$ git push
```
## MkDocs




