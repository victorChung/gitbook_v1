#####创建新版本库
```
git clone git@xxx.com:xxx/xxx.git
cd proj_folder
touch README.md
git add README.md
git commit -m "add README"
git push -u origin master
```

#####已存在的文件夹
```
cd existing_folder
git init
git remote add origin git@xxx.com:xxx/xxx.git
git add .
git commit -m "Initial commit"
git push -u origin master
```

#####已存在的 Git 版本库
```
cd existing_repo
git remote rename origin old-origin
git remote add origin git@xxx.com:xxx/xxx.git
git push -u origin --all
git push -u origin --tags
```