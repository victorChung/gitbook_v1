


#####查看进程占用

*    `lsof -i`
*    `lsof -i:8080`
*    `lsof -i tcp:8080`
    
    > 该命令会显示占用8080端口的进程，有其 pid ,可以通过pid关掉该进程


#####杀死进程 

*    `kill pid`


#####查看绝对路径
*    `pwd`

#####让配置文件改变生效
*    `source ~/.zshrc`


#####找到uwsgi命令执行位置
*    `find / -name uwsgi`

#####找到mysql命令安装位置
*    `find /usr/ -iname "mysql"`


#####建立软链接
*    `ln -s /usr/local/python27/bin/uwsgi /usr/bin/uwsgi`

*    `sudo ln -s /usr/local/bin/python3 /usr/bin/python`a
#####删除软链接
*    `rm uwsgi`


#####查找命令所在的路径
*    `which node`
    
    > node所在目录
    
---   
#####⌘ + 数字在各 tab 标签直接来回切换    
#####选择即复制 + 鼠标中键粘贴，这个很实用
#####ctrl + u 清空当前行，无论光标在什么位置
#####⌘ + r 清屏

#####输入开头命令后 按 ⌘ + ; 会自动列出输入过的命令

#####⌘ + shift + h 会列出剪切板历史

---

#####删除目录下的所有文件
*    `rm -rf folder/`

#####复制文件
*    `cp source_file dest_file`

#####复制目录下的所有文件
*    `cp -r source_folder/* dest_folder`

---

#####压缩解压
*    gzip:

	>压缩命令：`gzip 1.js`  // 压缩目录的时候加上-r，目录中的每个文件都进行压缩
	
	>解压命令：`gzip -d 1.js.gz` // gzip -d 要解压的文件
	

*    bzip2:

	>压缩命令：`bzip2 1.js` // bzip2 要压缩的文件
	
	>解压命令：`bzip2 -d 1.js.bz2` // bzip2 -d 要解压的文件
	
	

*    zip:

	>压缩命令：`zip 1.js.zip 1.js` // zip 压缩后的文件 源文件
	
	>解压命令：`unzip 1.js.zip` // unzip 要解压的文件
	
*    rar:

	>压缩：rar a FileName.rar DirName

	>解压：unrar x FileName.rar

---

#####tar打包

* 只能用其中一个

	>-c: --create建立压缩档案
	
	>-x: --extract解压tar文件`
	
	>-t: --list查看tarfile中的文件(内容)
	
	>-r: --append向压缩归档文件末尾追加文件
	
	>-u: --update更新原压缩包中的文件
	
* 可选参数

	>-f: --file使用档案名字，切记，这个参数是最后一个参数，后面只能接档案名。
	
	>-z: --gzip，--gunzip，--ungzip 调用gzip执行压缩或解压缩
	
	>-j: --bzip2，调用bzip2执行压缩或解压缩
	
	>-Z: --compress，--uncompress 调用compress执行压缩或解压缩
	
	>-v: --verbose 压缩过程中显示文件，但是不建议用在背景执行过程。
	
	>-O:将文件解开到标准输出

* 示例 ！！！tar只是打包，不是压缩

	>打包：`tar cvf FileName.tar DirName`
	
	>解包：`tar xvf FileName.tar`

* 如果加z参数，则以.tar.gz 或.tgz来代表 gzip 压缩过的 tar file。

	>压缩：`tar zcvf FileName.tar.gz DirName`
	
	>解压：`tar zxvf FileName.tar.gz`

* 如果加 j 参数，则以 .tar.bz2 来作为附档。

	>压缩：`tar jcvf FileName.tar.bz2 DirName`
	
	>解压：`tar jxvf FileName.tar.bz2`


---

#####wd命令

*    `wd add web`

	>这个命令相当于给当前目录做了一个标识，标识名叫做  web ， 

*    我们下次如果再想进入这个目录，只需输入：

	>`wd web` // 这样就可以完成目录切换了。
	
*    删除已有的映射

	>`wd rm web`
	
*    查看现有的映射

	>`wd list`	