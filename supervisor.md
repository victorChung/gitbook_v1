#####部署使用supervisor+nginx

[supervisor守护进程](https://www.jianshu.com/p/39b476e808d8)

[supervisor参考](http://liyangliang.me/posts/2015/06/using-supervisor/)

#####配置文件所在路径

*    `/etc/supervisor`

######配置tornado

```
; 设置进程的名称，使用 supervisorctl 来管理进程时需要使用该进程名
[program:tornado_dir_struct]
environment=PYTHONPATH='/usr/local/lib/python3.7/site-packages/'
directory=/Users/victor/myProj/python-tornado/dir-struct  ; 执行 command 之前，先切>    换到工作目录
command=python3 server.py
;numprocs=1                 ; 默认为1
;process_name=%(program_name)s   ; 默认为 %(program_name)s，即 [program:x] 中的 x
;user=oxygen                 ; 使用 oxygen 用户来启动该进程
; 程序崩溃时自动重启，重启次数是有限制的，默认为3次
autorestart=true
redirect_stderr=true        ; 重定向输出的日志
stdout_logfile = /var/log/supervisord/tornado_server.log
loglevel=info
```

######配置uwsgi

```
; 设置进程的名称，使用 supervisorctl 来管理进程时需要使用该进程名
[program:python_wxapi]
command=/usr/local/bin/uwsgi /Users/victor/myProj/python-wxapi/uwsgi.ini
;numprocs=1                 ; 默认为1
;process_name=%(program_name)s   ; 默认为 %(program_name)s，即 [program:x] 中的 x
; 程序崩溃时自动重启，重启次数是有限制的，默认为3次
autorestart=true
redirect_stderr=true        ; 重定向输出的日志
stdout_logfile = /var/log/supervisord/python_wxapi_server.log
loglevel=info
```
> ps 如果服务已启动，修改配置文件可用“supervisorctl reload”命令来使其生效

######nginx配置
[参考](https://blog.csdn.net/dragonchow123/article/details/78194212)

```supervisorctl
supervisorctl restart <application name> ;重启指定应用
supervisorctl stop <application name> ;停止指定应用
supervisorctl start <application name> ;启动指定应用
supervisorctl restart all ;重启所有应用
supervisorctl stop all ;停止所有应用
supervisorctl start all ;启动所有应用
supervisorctl status ; 查看应用状态
```