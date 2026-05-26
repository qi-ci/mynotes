## refrences
[下载与安装 - Obsidian 中文帮助](https://obsidian.md/zh/help/install)

## Obsidian
```
flatpak install flathub md.obsidian.Obsidian
flatpak run md.obsidian.Obsidian
```
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
#修改仓库 git remote set-url origin <新的仓库地址>
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
```
acorus@ubuntu:/data/info/notes$ python3 -m venv .venv
acorus@ubuntu:/data/info/notes$ source .venv/bin/activate
(.venv) acorus@ubuntu:/data/info/notes$ pip install mkdocs mkdocs-material mkdocs-literate-nav

#Obsidian + MkDocs自动同步结构
(.venv) acorus@ubuntu:/data/info/notes$ pip install mkdocs-awesome-nav
(.venv) acorus@ubuntu:/data/info/notes$ nano mkdocs.yml 

site_name: My Notes

theme:
  name: material

plugins:
  - search
  - awesome-nav

(.venv) acorus@ubuntu:/data/info/notes$ mkdocs serve

```

## Obsidian图片路径设置
![](../assets/images/Pasted%20image%2020260522175412.png)
## 部署到github pages
```
(.venv) acorus@ubuntu:/data/info/notes$ echo "site/" >> .gitignore 
(.venv) acorus@ubuntu:/data/info/notes$ mkdocs gh-deploy
```
![](../assets/images/Pasted%20image%2020260521220506.png)
## pages页面不刷新
```
git push origin --delete gh-pages
mkdocs gh-deploy --clean --force
```
