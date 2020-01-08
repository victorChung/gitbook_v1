*    [uwsgi官方文档](https://uwsgi-docs-zh.readthedocs.io/zh_CN/latest/WSGIquickstart.html)

######参考

*    [使用nginx + uwsgi socket的方式来部署Django项目](https://blog.csdn.net/kuangshp128/article/details/78768025)
*    [uwsgi使用介绍](https://www.jianshu.com/p/c3b13b5ad3d7)
*    [uwsgi ini 配置](https://www.cnblogs.com/teachen/articles/9117190.html)

###不用ini文件

#####http启动方式
*    `uwsgi --http :9796 --wsgi-file app.py`

    > 该命令启动成功后可以直接通过http://127.0.0.1:9796访问
    
######配置到nginx
    
```nginx
server {
    server_name py.bnv.com;
    listen 80;

    location / {
        proxy_pass http://127.0.0.1:9796; # 直接通过代理的方式
    }
}
```
#####socket启动方式
*    `uwsgi --socket :9796 --wsgi-file app.py`

######socket启动方式还要配置nginx
    
```nginx
upstream uwsgi_py {
    server 127.0.0.1:9796;
}

server {
    server_name py.bnv.com;
    listen 80;

    location /{
        include uwsgi_params;
        uwsgi_pass uwsgi_py; # socket方式
    }
}
```
######或者

```nginx
server {
    server_name py.bnv.com;
    listen 80;

    location /{
        include uwsgi_params;
        uwsgi_pass 127.0.0.1:9796; # socket方式
    }
}
```
######uwsgi_params文件：
```
uwsgi_param  QUERY_STRING       $query_string;
uwsgi_param  REQUEST_METHOD     $request_method;
uwsgi_param  CONTENT_TYPE       $content_type;
uwsgi_param  CONTENT_LENGTH     $content_length;

uwsgi_param  REQUEST_URI        $request_uri;
uwsgi_param  PATH_INFO          $document_uri;
uwsgi_param  DOCUMENT_ROOT      $document_root;
uwsgi_param  SERVER_PROTOCOL    $server_protocol;
uwsgi_param  HTTPS              $https if_not_empty;

uwsgi_param  REMOTE_ADDR        $remote_addr;
uwsgi_param  REMOTE_PORT        $remote_port;
uwsgi_param  SERVER_PORT        $server_port;
uwsgi_param  SERVER_NAME        $server_name;
```


###使用ini文件

*    `uwsgi --ini uwsgi.ini`

```
[uwsgi]
#http = 0.0.0.0:9796
socket = 0.0.0.0:9000
wsgi-file = ./server.py
```

***
* http通过ip可以直接访问，socket要配置ng
* 要注意ng权限，如果不是管理员则启动时要加上sudo

***

######更多的详细请参考[官方文档](https://uwsgi-docs-zh.readthedocs.io/zh_CN/latest/WSGIquickstart.html)

*    `重启 uwsgi --reload uwsgi.pid`
*    `关闭 uwsgi --stop uwsgi.pid`
*    `停止所有 sudo pkill -f uwsgi -9`

######ini文件里设置pidfile，通过该pid文件可以控制uwsgi的重启和停止
```
chdir=/xxx/   #当前项目的绝对路径
pidfile=%(chdir)/uwsgi/uwsgi.pid
stats=%(chdir)/uwsgi/uwsgi.status
```
###实时动态查看状态 - uwsgitop
```
pip3 install uwsgitop
uwsgitop uwsgi/uwsgi.status
```