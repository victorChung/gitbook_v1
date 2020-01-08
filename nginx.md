#####配置文件位置

```
#mbp
/usr/local/etc/nginx/

#centOS
/usr/local/nginx/
```

#####安装目录  
*    `open /usr/local/Cellar/nginx`

#####启动   
*    `nginx`

#####查看配置   
*    `cat /usr/local/etc/nginx/nginx.conf`


#####html目录   
*    `/usr/local/var/www`

#####查看进程
*    `ps -ef|grep nginx`
*    `ps aux|grep nginx`

#####监测配置是否能通过检查 
*    `nginx -t`


#####重新加载配置
*    `nginx -s reload`

#####关闭nginx
*    `nginx -s stop`

#####等所有请求结束后关闭服务
*    `kill -QUIT  nginx主进程号`

#####立刻关闭nginx进程
*    `kill -TERM nginx主进程号`

#####强制停止
*    `kill -9 nginx主进程号`