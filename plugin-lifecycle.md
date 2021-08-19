# 插件交互流程

插件与 EasyCraft 之间可以进行交互. EasyCraft 将通过反射调用插件中 `EasyCraftPlugin.Plugin`下的相关方法

!> 请不要轻易反射 EasyCraft, 否则可能在之后的版本不被支持

## 加载

在 EasyCraft 开启的时候,会调用插件的 `OnLoad` 函数. 

传入参数:

* `EasyCraft.PluginHandler`的反射类型
* 与 EasyCraft 交互的 `key`

在接受到传入之后,你应当将这两个参数存储起来作为与 EasyCraft 交互的依据. 同时,此方法应当尽快进行返回.

返回值:

* `Dictionary<string,string>` 

  * `PluginInfo`
    * id: 插件ID
    * name: 插件名称
    * author: 作者名称
    * description: 插件简介
    * link: 插件相关链接
    
  * `Hooks`: 一个 `Dictionary`, 内容为 <Hook的接口,优先级> (具体接口可查看 [插件钩子](/plugin-hooks))
  
  * `Request`: 要申请的权限
  
  * `ApiHooks`: API的钩子,一个Dictionary,内容为 <API路径,调用的方法名称> 
  
    请在插件下存在静态的方法名称函数,参数为 `HttpContext`



## 被启用

在插件被启用的时候会调用 `OnEnable`

传入参数: 无

返回: 无

你可以在这里做一些插件初始化的事情
