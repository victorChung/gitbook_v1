####git修改提交作者和邮箱

#####主动配置
```
// 设置全局
git config --global user.name "Author Name"
git config --global user.email "Author Email"

// 或者设置本地项目库配置
git config user.name "Author Name"
git config user.email "Author Email"
```

#####修改最近一次提交
```
git commit --amend --author="NewAuthor <NewEmail@address.com>"
```