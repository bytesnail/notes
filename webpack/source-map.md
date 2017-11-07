# Source Map
在webpack配置中, 有两种方式设置sourcemap
1. devtool: 'source-map'
2. plugin: SourceMapDevToolPlugin/EvalSourceMapDevToolPlugin

两种不能同时使用, 设置devtool属性时, webpack会自动添加plugin.

| devtool | build | rebuild | quality |
| --- | --- | --- | --- |
| (none) | +++ | +++ | bundled code |
| eval | +++ | +++ | generated code |
| cheap-eval-source-map | + | ++ | transformed code (lines only) |
| cheap-module-eval-source-map | o | ++ | original source (lines only) |
| eval-source-map | -- | + | original source |
| cheap-source-map | + | o | transformed code (lines only) |
| cheap-module-source-map | o | - | original source (lines only) |
| inline-cheap-source-map | + | o | transformed code (lines only) |
| inline-cheap-module-source-map | o | - | original source (lines only) |
| source-map | -- | -- | original source |
| inline-source-map | -- | -- | original source |
| hidden-source-map | -- | -- | original source |
| nosources-source-map | -- | -- | without source content |

上图表格展示了soucemap的类型、编译&重编译速度、编译结果类型等信息, 具体含义如下:

### 编译速度
编译所用时间: +++ (super fast) < ++ (fast) < + (pretty fast) < o (medium) < - (pretty slow) < -- (slow)

### 编译结果
`bundled code` - 编译、混淆、压缩后的代码, 不保留源代码格式, 按入口模块和异步bundle合并打包成文件

`generated code` - 编译、混淆后的代码; 按模块拆分, 保留原文件结构 (以下均是)

`transformed code` - 编译后的代码, 保留原始变量名称, 转义 ES6 & JSX 语法

`original source` - 原始代码

`(lines only)` - sourcemap的简化处理, 按行转义源码 (默认是按声明语句); 调试时只能在每一行上加断点, 行内的多个语句无法单独调试
