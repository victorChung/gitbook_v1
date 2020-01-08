####场景： 对于某个Git控制下的文件进行了修改，但是改的不满意，想退回到改之前的版本。假定该文件为 src/main/main.c

####解决方法：

* 第一步： 在命令行中输入 git log src/main/main.c 得到该文件的commit 历史。 会得到类似下面的界面

 

* 第二步： 复制需要回退版本的hash，在此假设我们回退到 d98a0f565804ba639ba46d6e4295d4f787ff2949 ,则复制该序列即可

* 第三步：checkout 对应版本。格式为 git checkout <hash> <filename>, 在此即为命令行中输入 git checkout d98a0f565804ba639ba46d6e4295d4f787ff2949 src/main/main.c

* 第四步： commit checkout下来的版本。 如： git commit -m "revert to previous version"

 

 

* 注意： 第三步中不要忘记加 文件属性，即src/main/main.c