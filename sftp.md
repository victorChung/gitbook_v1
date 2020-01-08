
#####打开终端，连接远程Linux
*    `sftp user@host`
*    `例如：sftp root@192.168.1.2`


#####上传文件
*    `put local_path remote_path`
*    `例如：put -r /home/share/read.txt /home/root`

#####上传文件夹以文件夹里的所有内容
*    `put -r /home/share/folder/* /home/root/folder`


#####下载文件
*    `get remote_path local_path`
*    `例如：get -r /usr/local/some.zip /home/share`


#####下载文件夹以文件夹里的所有内容
*    `get -r /usr/local/folder/* /home/share/folder`