# Docker

windows镜像目录：

C:\Users\wa1tzy\AppData\Local\Docker\wsl\data

## 0、常用命令

```
# 查看当前运行的容器
docker ps
# 查看全部容器
docker ps -a
# 查看全部容器的id和信息
docker ps -a -q
# 查看全部容器占用的空间
docker ps -as
# 查看一个正在运行容器进程，支持 ps 命令参数
docker top
# 查看容器的示例id
sudo docker inspect -f  '{{.Id}}' [id]
# 检查镜像或者容器的参数，默认返回 JSON 格式
docker inspect
```

## 1、docker run -p 

```
docker run -v /data/shanxi/:/data/shanxi -p 18806:18806 -p 10089:10089 -it shanxi_system:v1 env LANG=C.UTF-8 /bin/bash
```

加了--net=host以后就不需要再做端口映射了

```
docker run -it --net=host yolov5:latest /bin/bash
```

## 2、添加环境变量

```
docker run -it yolov5_infer:latest env LANG=C.UTF-8 /bin/bash
```

## 3、--restart=always

与容器一同启动

如果已经过运行的项目
如果已经启动的项目，则使用update更新：

```java
docker update --restart=always 容器id或name
```

## 4、mysql启动

-e MYSQL_ROOT_PASSWORD=123456：初始化 root 用户的密码。 

-d mysql:5.6 : 后台程序运行mysql5.6

```
docker run --restart=always -p 3306:3306 -e MYSQL_ROOT_PASSWORD=123456  -v D:\MySoft\mysqld.cnf:/etc/mysql/conf.d/mysqld.cnf  --name mysql -d mysql:5.7
```

## 5、Docker镜像推送到Docker Hub

```
登录
docker login
tag命令修改为规范的镜像：docker push 注册用户名/镜像名
docker tag wa1tzy/ubuntu:base
推送镜像
docker push wa1tzy/ubuntu:base
搜索发布镜像
docker search wa1tzy/ubuntu:base
拉取镜像
docker pull wa1tzy/ubuntu:base
```

## 6、dockerfile

```
which python 结果-->/usr/local/bin/python
python
import os
print(os.sys.path)
```

```
ENV LC_ALL=C.UTF-8
ENV LANG=C.UTF-8
ENV LANGUAGE=C.UTF-8
```



```
FROM jiucuo:v090302
EXPOSE 18688
WORKDIR /home/pycorrector/examples
ENV PYTHONPATH /usr/local/lib/python3.7/dist-packages
CMD ["/usr/local/bin/python","base_demo.py"]
```

```
FROM pdserving_cpu:v0428
WORKDIR /home/PaddleOCR-release-2.4/deploy/pdserving
ENV /usr/local/lib/python3.7/site-packages
EXPOSE 9999
CMD ["/usr/local/bin/python3.7","web_service.py"]
```

## 7、docker修改镜像源

```
vim /etc/docker/daemon.json
# 重启docker
sudo systemctl daemon-reload 
sudo systemctl restart docker
```

## 8、重命名容器

```
sudo docker rename old_container_name  new_container_name
```

9、

```
docker 启动报端口不可用解决方案
Ports are not available: exposing port TCP 0.0.0.0:xxxxx -> 0.0.0.0:0: 
listen tcp 0.0.0.0:xxxxx: bind: An attempt was made to access a socket 
in a way forbidden by its access permissions.
```

```
2、以管理员身份打开PowerShell，

1) 先停止winnat

net stop winnat
2) 再重启winnat

net start winnat

```

##  10、docker attach 与exec

```
#进入当前容器后开启一个新的终端，可以在里面操作。（常用）
docker exec

#进入容器正在执行某个命令的终端，不能在里面操作；多个窗口同时attach到同一个容器时，所有窗口同步显示；当某个窗口因命令阻塞，其他窗口也无法操作
docker attach
```

```
 docker exec：进入容器并开启一个新的bash终端。 退出容器终端时，不会导致容器的停止。
 docker attach：进入正在执行容器，不会启动新的终端， 退出容器时，会导致容器的停止。
```

## 11、退出容器，不停止容器

```
退出时，使用[ctrl + D]，这样会结束docker当前线程，容器结束，可以使用[ctrl + P][ctrl + Q]退出而不终止容器运行
```

## 12、退出的容器让其always运行

```
docker container update --restart=always 1a7a3b5112fd
```

## 13、不使always运行的容器运行

```
docker container update --restart=no 1a7a3b5112fd
```

## 14、重启docker服务

```
systemctl restart docker 
```

## 15、Docker: Error response from daemon: Ports are not available 端口没被占用，却显示被占用

```
cmd进管理员
net stop winnat
net start winnat
```

## 16、Docker Desktop一直starting

```
wsl --unregister docker-desktop
wsl --unregister docker-desktop-data
```

![image](https://github.com/wa1tzy/test20240822/blob/master/imgs/image-20230308223358526.png)

## 17、容器脚本乱码

```
https://www.cnblogs.com/gaogaoxingxing/p/15465284.html
```

```
vim /root/.vimrc  或 vim ~/.vimrc
```

```
set termencoding=utf-8
set encoding=utf8
set fileencodings=utf8,ucs-bom,gbk,cp936,gb2312,gb18030
```

```
:wq!
```

