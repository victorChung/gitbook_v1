
####启动方式

#####cd到项目目录

*    `python3 -m venv venv`

#####进入venv环境

*    `. venv/bin/active`

#####退出环境 

*    `deactivate `


#####安装tornado

*    `pip3 install tornado`

#####启动

*    `python server.py`


#####进入venv后的自动重启（不设置settings里的autoreload）

*    `python -m tornado.autoreload server.py`




#####部署使用supervisor+nginx

[使用supervisor支持python3](https://www.cnblogs.com/andy-0212/p/9999639.html)

######supervisor配置

```supervisor
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


######nginx配置
[参考](https://blog.csdn.net/dragonchow123/article/details/78194212)

```ngix
upstream tornado_py {
	server 127.0.0.1:9010;
}

server {
	server_name tornado.bnv.com;
	listen 80;
	
	location / {
		proxy_pass_header Server;
		proxy_set_header Host $http_host;
		proxy_set_header X-Real-IP $remote_addr;
		proxy_set_header X-Scheme $scheme;
		proxy_pass http://tornado_py;
	}
}
```
