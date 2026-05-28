## docker 
```
# [https://docs.docker.com/engine/install/ubuntu/]
# Add Docker's official GPG key:
sudo apt update
sudo apt install ca-certificates curl
sudo install -m 0755 -d /etc/apt/keyrings
sudo curl -fsSL https://download.docker.com/linux/ubuntu/gpg -o /etc/apt/keyrings/docker.asc
sudo chmod a+r /etc/apt/keyrings/docker.asc

# Add the repository to Apt sources:
sudo tee /etc/apt/sources.list.d/docker.sources <<EOF
Types: deb
URIs: https://download.docker.com/linux/ubuntu
Suites: $(. /etc/os-release && echo "${UBUNTU_CODENAME:-$VERSION_CODENAME}")
Components: stable
Architectures: $(dpkg --print-architecture)
Signed-By: /etc/apt/keyrings/docker.asc
EOF

sudo apt update
sudo apt install docker-ce docker-ce-cli containerd.io docker-buildx-plugin docker-compose-plugin

sudo systemctl status docker
sudo systemctl start docker

```
![](../assets/images/Pasted%20image%2020260528142431.png)
## 下载酒馆 
```
git clone https://github.com/SillyTavern/SillyTavern.git -b release
```
![](../assets/images/Pasted%20image%2020260528142542.png)
## 安装1Panel 
```
su root 
curl -sSL https://resource.fit2cloud.com/1panel/package/quick_start.sh -o quick_start.sh && bash quick_start.sh
```
## 1Panel中部署酒馆 

Node环境 
![](../assets/images/Pasted%20image%2020260528142613.png)
改酒馆配置文件
将 `listen: false` 更改为 `listen: true`  
将 `whitelistMode`: true 更改为 `whitelistMode`: false  
将 `basicAuthMode`: false 更改为 `basicAuthMode`: true  
在 `basicAuthUser` 中，设置 `username(用户名)` 和 `password(密码)`，注意要用英文的双引号包裹  
## 重启Node服务 
![](../assets/images/Pasted%20image%2020260528142628.png)
## 备份酒馆数据
[https://console.bitiful.com/users](https://console.bitiful.com/users) 
把minio添加到1panel 
![](../assets/images/Pasted%20image%2020260528142647.png)
创建备份的计划任务 
![](../assets/images/Pasted%20image%2020260528142658.png)
## API反代 
分体gcli2api-Render版 
![](../assets/images/Pasted%20image%2020260528142708.png)
注册neno数据 
为什么需要数据库？ 
因为Render本身无法持久化存储数据，当gcli2api项目重启或者更新时，你的凭证将会丢失。 
但如果配置了数据库，重启或更新gcli2api项目重启时，数据就不会丢失啦。 
![](../assets/images/Pasted%20image%2020260528142717.png)
在render项目里加入数据库 
![](../assets/images/Pasted%20image%2020260528142726.png)
![](../assets/images/Pasted%20image%2020260528142740.png)
获取凭证 
![](../assets/images/Pasted%20image%2020260528142754.png)