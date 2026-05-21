## 配置用户信息
```
sudo apt install git

acorus@ubuntu:/data/info/notes$ git config --global user.email "lingyugu9@gmail.com"
acorus@ubuntu:/data/info/notes$ git config --global user.name "acorus"
acorus@ubuntu:/data/info/notes$ git remote add origin git@github.com:qi-ci/mynotes.git

acorus@ubuntu:/data/info/notes$ git config --list
user.name=acorus
user.email=lingyugu9@gmail.com
core.repositoryformatversion=0
core.filemode=true
core.bare=false
core.logallrefupdates=true
remote.origin.url=git@github.com:qi-ci/mynotes.git
remote.origin.fetch=+refs/heads/*:refs/remotes/origin/*
```
## Obsidian git初始化
```
git init

nano .gitignore
.obsidian/workspace*
.trash/
```




