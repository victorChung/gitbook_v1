#####启动mysql服务

*    `mysql.server start`

#####停止mysql服务

*    `mysql.server stop`

#####重启mysql服务

*    `mysql.server restart`

#####查看状态

*    `mysql.server status`


#####root模式
*    `sudo su -`


#####mysql模式
*    `mysql -u root -p`

#####跳过权限表
```mysql
vim /etc/my.cnf
[mysqld]
skip-grant-table
```

#####遇到的问题

错误号 2059

```mysql
>use mysql;
>flush privileges;
>ALTER USER 'root'@'localhost' IDENTIFIED WITH mysql_native_password BY xxx';

```
