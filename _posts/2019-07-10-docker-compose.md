---
layout: post
category: coding
---

### 安装

docker-compse 同样有官方提供的安装脚本，我们可以使用以下脚本安装

```
curl -L https://github.com/docker/compose/releases/download/1.24.1/docker-compose-`uname -s`-`uname -m` -o /usr/local/bin/docker-compose
chmod +x /usr/local/bin/docker-compose
```



为了维护更新方便，我将官网脚本进行了简单地封装，省去每次更新前的卸载、权限设置。

```
#!/bin/sh
# 用于更新维护docker-compose 提供脚本需要的docker-compose版本号参数
#!/bin/sh
# 用于更新维护docker-compose 提供脚本需要的docker-compose版本号参数
sudo rm /usr/local/bin/docker-compose
echo "卸载docker-compose成功！"
sudo curl -L https://github.com/docker/compose/releases/download/$1/docker-compose-`uname -s`-`uname -m` > /usr/local/bin/docker-compose
echo "安装docker-compose$1成功！"
sudo chmod +x /usr/local/bin/docker-compose
echo "权限设置成功！"
```



脚本非常简陋，使用的方法也很简单，自行检查仓库是否更新发布了[新版本](<https://github.com/docker/compose/releases>)，通过`./up.sh 1.24.1 ` 将需要更新的版本号作为参数执行即可。



## 撰写文件格式
[官方](https://docs.docker.com/compose/compose-file/)目前更新到了 `version 3.8`

| 撰写文件格式    | Docker引擎 |
| --------------- | ---------- |
| 1               | 1.9.0+     |
| 2.0             | 1.10.0+    |
| 2.1             | 1.12.0+    |
| 2.2,3.0,3.1,3.2 | 1.13.0+    |
| 2.3,3.3,3.4,3.5 | 17.06.0+   |
| 2.4             | 17.12.0+   |
| 3.6             | 18.02.0+   |
| 3.7             | 18.06.0+   |
|3.8		  | 19.03.0+   |