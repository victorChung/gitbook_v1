####场景：如果想恢复到之前某个提交的版本，且那个版本之后提交的版本我们都不要了，就可以用这种方法。

[参考](https://blog.csdn.net/yxlshk/article/details/79944535)


* 查看版本号(commit的hash)

```
git log
```

* 版本回退

```
git reset --hard 目标版本号
```

* 提交更改

```
git push -f
```