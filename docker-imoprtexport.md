
#####导出容器

```docker export 1e560fca3906 > ubuntu.tar```

#####导入容器

```cat docker/ubuntu.tar | docker import - test/ubuntu:v1```

* 将快照文件 ubuntu.tar 导入到镜像 test/ubuntu:v1


#####通过指定 URL 或者某个目录来导入

```
docker import http://example.com/exampleimage.tgz example/imagerepo
```