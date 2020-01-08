#####Git常用命令

[参考](http://www.ruanyifeng.com/blog/2015/12/git-cheat-sheet.html)

```
# 查看分支 
git branch

# 创建分支 
git branch test（test为分支名）

# 切换分支 
git checkout test

# 基于老分支创建新的分支
git checkout -b 新分支名 老分支名

# 建立追踪关系，在现有分支与指定的远程分支之间
git branch --set-upstream [branch] [remote-branch]

# 合并指定分支到当前分支
git merge [branch]

# 删除分支
git branch -d [branch-name]

# 删除远程分支
git push origin --delete [branch-name]
git branch -dr [remote/branch]

# 查看分支状态 
git status

# 添加全部 
git add .

# 删除文件 
git rm FILENAME

# 放弃修改文件 
git checkout FILENAME

# 提交修改到当前分支 
git commit -m "注释。。。"

```

#####Git 全局设置
```
# 显示当前的Git配置
git config --list

# 设置提交代码时的用户信息
git config --global user.name "xxx"
git config --global user.email "xxx@xxx.cn"
```

