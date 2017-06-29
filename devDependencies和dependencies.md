# devDependencies和dependencies

在使用npm install 安装模块或插件的时候，有两种命令把他们写入到 package.json 文件里面去，比如：

--save-dev

--save

在 package.json 文件里面提现出来的区别就是，使用 --save-dev 安装的 插件，被写入到 devDependencies 对象里面去，而使用 --save 安装的插件，责被写入到 dependencies 对象里面去。

devDependencies  里面的插件只用于开发环境，不用于生产环境，而 dependencies  是需要发布到生产环境的。