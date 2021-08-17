# 快速安装

对于每一个二次开发的组件,都有一个路径来存放:

* 核心: `/data/cores/*`
* 整合包: `/data/packages/*`
* 插件: `/data/plugins/*.dll`
* 开服器: `/data/starter/*.dll`

EasyCraft 在开启时会自动从上述路径加载二次开发组件. 你也可以在 EasyCraft 控制台中输入


* 插件: `relead plugin 插件包名`
* 整合包: `reload package 整合包包名`
* 开服器: `relead starter 开服器包名`
* 核心: `relead core 核心包名`

EasyCraft 并不会在每次 放入/移除 文件夹中组件时加载, 需要你手动 reload

