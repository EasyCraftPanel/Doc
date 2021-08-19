# 开服器

> 开服器可以管理服务器实际运行程序.

你可以参考 [EasyCraftBasicStarter](https://github.com/EasyCraftPanel/EasyCraftBasicStarter) 和 [Starter-BDSInject](https://github.com/EasyCraftPanel/Starter-BDSInject)

开服器可以让你自定义开服的相关流程.

> 在开服的时候你可以设置 Server.StatusInfo.Status 来设置服务器的运行状态
>
> * 0: 已停止
> * 1: 启动中
> * 2: 已启动
> * 3: 停止中

## 开服器结构

请将所有的静态方法放置在`EasyCraftStarter.Starter`

* InitializeStarter 将返回开服器的相关信息,如果不想加载可以直接throw Exception.

* `ServerStart`: 调用开服器开启服务器

  * 传入:
    *  `ServerBase` 参见 [EasyCraft/ServerBase.cs](https://github.com/EasyCraftPanel/EasyCraft/blob/main/EasyCraft/Base/Server/ServerBase.cs)
    * `string`: program, 核心配置中 `StartInfo` 的 `Program` 项, 已经过服务器变量处理
    * `string`: arguments, 核心 `StartInfo`的`param`项, 已经过服务器变量处理
  * 传出:
    * `bool` 是否成功开服.

* `ServerStop`: 调用开服器关闭服务器

  * 传入: `ServerBase`
  * 传出: `bool` 是否成功关闭

* `OnServerInput`: 输入命令到服务器
  * 传入: `ServerBase`, `string`: 指令
  * 传出: `bool`, 是否成功
* `OnServerForceStop`: 强制停止服务器时
  * 传入: `ServerBse`
  * 传出:`bool`是否成功

  

