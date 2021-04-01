
#### 镜像


##### 查找镜像

1. [https://hub.docker.com/](https://hub.docker.com/)

2. 或```docker search httpd```



##### 获取镜像

```docker pull ubuntu:13.10```

* ubuntu:13.10: 这是指用 ubuntu 13.10 版本镜像为基础来启动容器。


##### 删除镜像

```docker rmi hello-world```




#### 创建镜像

##### 方法1

1. 先创建容器并进入容器内部```docker run -t -i ubuntu:15.10 /bin/bash```

1. 在运行的容器内使用 ```apt-get update``` 命令进行更新。

1. 完成操作之后，输入 exit 命令来退出这个容器

1. 提交容器副本```docker commit -m="has update" -a="runoob" e218edb10161 runoob/ubuntu:v2```

* -m: 提交的描述信息

* -a: 指定镜像作者

* e218edb10161：容器 ID

* runoob/ubuntu:v2: 指定要创建的目标镜像名

* 可以使用 ```docker images``` 命令来查看我们的新镜像 runoob/ubuntu:v2：


##### 方法2

