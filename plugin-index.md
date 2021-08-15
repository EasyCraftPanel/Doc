# 插件

> 插件是用于扩展 EasyCraft 功能的. 可以监听 EasyCraft 公开的事件,调用相关的 API 来进行对 EasyCraft 的 功能补充

在开始之前, 你可以参考我们的 [示例插件](https://github.com/EasyCraftPanel/EasyCraftPlugin). 

结合示例, 你将会对插件开发有个更直观的认识.

!> 插件应当区别于 [开服器](/starter-index)

我们将会采用 [C# (.NET 5)](https://dotnet.microsoft.com/download/dotnet/5.0) 进行插件开发. 推荐使用 Rider 或 Visual Studio 进行开发

## 开发规范

首先在开发前,你应该树立这几个观念:

* 开发是为了方便用户,而不是为了盗取用户数据
* 尽量不影响效率,所有耗时操作尽量在另一个线程进行操作
* 开发时应当注意兼容性,用户可能会安装其他插件,不应当出现影响其他插件运行的行为
* 没有什么事情是不能用自己双手解决的! 相信自己一定可以开发成功的

## 开发之前

在开发之前,你应当想好一些东西:

* 插件名称

* 插件ID

  插件 ID 应当区别于其他插件, 同时便于识别和管理. 我们推荐采用 域名反写式. 例如 `top.easycraft.plugin.example`

* 插件简介

* 作者名称

* 插件链接 / 作者链接

* 版本号

