
# 测试方法

## 客户端建立

+ 建立Curl客户容器
```bash
sudo docker run -itd --name=client_setup ubuntu bin/bash
sudo docker attach client_setup
```
+ 进入 容器Shell后运行命令修改镜像源
```bash
sed -i 's/archive.ubuntu.com/mirrors.aliyun.com/g' /etc/apt/sources.list
apt-get update
apt-get install curl        #curl 访问
apt-get install net-tools   #ifconfig 可以查看IP地址
#CTRL+P CTRL+Q 推出容器Shell
```

+ 保存成Image

```bash
sudo docker stop client_setup
sudo docker commit client_setup client_img
```

## 建立Apache2服务端容器

+ 建立Docker
```bash
sudo docker run -itd --name=server_setup ubuntu /bin/bash
sudo docker attach server_setup
```

+ 安装apache2 net-tools

```bash
sed -i 's/archive.ubuntu.com/mirrors.aliyun.com/g' /etc/apt/sources.list
apt-get update
apt-get install apache2
apt-get install net-tools
#CTRL+P CTRL+Q 推出容器Shell
```

+ 保存Image

```bash
sudo docker stop server_setup
sudo docker commit server_setup server_img
```




