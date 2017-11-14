# Webpack 3.0
## 主要特性
* 依赖解析, 打包合并
* 支持异步模块, 按需加载
* 预编译代码, 通过loaders处理es6, jsx, less, sass等格式的模块
* 多任务处理, 通过plugins提供代码混淆、压缩、样式提取等功能
* 支持 ES6 & commonJS 模块
* 支持 sourcemap

## 主要流程
webpack构建时, 从入口文件开始, 循环的解析依赖, 并将项目所需要的依赖, 打包成一个或多个文件输出

生成compiler -> 处理入口模块 -> 解析模块依赖 -> 调用loader加载模块 -> 打包文件, 拆分异步chunks -> 调用插件处理文件内容 -> 输出模块文件

## 核心概念
* 入口文件 (Entry) 构建项目和解析依赖关系的入口
* 输出文件 (Output) 打包后文件的输出格式和位置
* 加载器 (Loaders) 针对不同格式模块的预处理器, 可以替换或转义代码内容
* 插件 (Plugins) 代码打包输出前的最后处理, 如压缩和混淆等操作

## 升级 3.0
此次从1.0升级到3.0, 带来了许多新的功能点

* 支持ES6模块, 如import, export等语法(v2)
* 针对ES6模块, 提供动态加载方法`import()`(v2), 并通过注释定义模块信息(v3)
* 基于ES6模块的静态结构, 提供Tree shaking功能, 移除未被使用的模块输出(v2)
* 作用域提升/合并, 通过启用插件`webpack.optimize.ModuleConcatenationPlugin`, 减少模块打包后产生的闭包数量, 优化代码执行速度和打包体积(v3)
* 集成常用loader, 如less, sass, CoffeeScript, TypeScript等

