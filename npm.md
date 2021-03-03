#####强制清理缓存
*    `npm cache clean  --force`

#####安装淘宝镜像 cnpm

`npm install -g cnpm --registry=https://registry.npm.taobao.org`


#####设置仓库地址
*    `官方地址： npm config set registry https://registry.npmjs.org/`

*    `淘宝镜像： npm config set registry https://registry.npm.taobao.org/`


#####使用本地模块

*    `在模块目录执行 npm link`

*    `在项目目录执行 npm link module_name`
>  module_name为模块package.json里的name


#####解除link

*    `解除项目和模块link，在项目目录执行 npm unlink module_name `

*    `解除模块全局link，在模块目录执行 npm unlink module_name `



#####发布模块

1. `设置仓库地址为官方的npm config set registry https://registry.npmjs.org/`

1. `npm adduser`

1. `在模块目录执行 npm publish`