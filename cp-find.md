###cp目录时排除一个或者多个目录的实现方法

* <kbd>cp -R &#96;find /home/data -type d -path /home/data/e -prune -o -print | sed 1d &#96; /bak</kbd>

####上述命令说明

1. find /home/data -type d 找出该目录下的文件夹，如果是-type f则是找出该目录下的文件。

2. 再加上路径选项：-path /home/data/e 表是找出/home/data指定路径下的文件夹。

3. -prune：使得find命令不进入到当前路径。

4. -o类似于逻辑或运算，find /home/data -type d -path /home/data/e -prune -o -print是find /home/data -type d -path /home/data/e -a -prune -o -print的缩写。

    >其中-a相当于逻辑与&&，-o相当于逻辑或||，上述命令等价于：

    >if -path "/home/data/e" then  

    >-prune  

    >else  

    >-print  

意思就是查找/home/data目录下的文件夹，如果路径是/home/data/e,就执行“-prune”(跳过)操作，如果不是该路径，则执行 “-print”(打印)操作。