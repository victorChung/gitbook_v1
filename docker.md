#####启动容器

```docker run -itd -h abc.def.gh -p 80:80 --name docker/getting-started```

* -i : 交互式操作
* -t : 终端
* -d : 不进入容器，让容器在后台运行
* -p : 端口映射，  宿主机端口：容器内部端口，例如8080:80
* -P : 将容器内部使用的网络端口随机映射到我们使用的主机上
* -i : 交互式操作
* --name : 定义容器名字（不定义则随机）


#####查看容器

```docker ps```

* 默认只显示存在运行中的容器
* -a : 全部容器


#####查看容器配置

```docker inspect a9f5968fabb7 ```

* 可以是容器ID或容器名字


#####停止容器

```docker stop a9f5968fabb7 ```

* 可以是容器ID或容器名字


#####已经停止的容器，使用docker start 来启动

```docker start a9f5968fabb7 ```


#####正在运行的容器，使用docker restart 来重启

```docker restart a9f5968fabb7 ```


#####删除容器

```docker rm -f a9f5968fabb7 ```

* 删除容器时，容器必须是停止状态




#####查看端口映射

```
docker port a9f5968fabb7
5000/tcp -> 0.0.0.0:5000
```

* 可以是容器ID或容器名字


#####查看日志

```docker logs -f [ID或者名字]```

* 可以是容器ID或容器名字


#####查看容器内部运行的进程

```docker top docker/getting-started```