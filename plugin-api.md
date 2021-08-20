# 插件 API

我们提供了一些插件 API, 方便插件随时调用

如果你还有想要开放的API可以 [发起Issue](https://github.com/EasyCraftPanel/EasyCraft/issues/new/choose) 或者 进行 Pull Request.

!> 请在 Auth 中传入你需要调用的 API, 否则在调用的时候将不会返回

* `FastConsole.PrintInfo`: 控制台输出 INFO 信息
  * 传入: `string`:输出内容
  * 返回: 无

* `FastConsole.PrintTrash`: 控制台输出 Verbose 调试
  * 传入: `string`:输出内容
  * 返回: 无

* `FastConsole.PrintWarning`: 控制台输出 Warning 警告
  * 传入: `string`:输出内容
  * 返回: 无

* `FastConsole.PrintError`: 控制台输出 Error 错误
  * 传入: `string`:输出内容
  * 返回: 无

* `FastConsole.PrintFatal`: 控制台输出 Fatal 致命
  * 传入: `string`:输出内容
  * 返回: 无

* `Server.GetInfo`: 获取服务器基本信息
  * 传入: `int`: 服务器ID

  * 返回: `ServerInfoBase`: 服务器基本数据 

    (参考 EasyCraft [ServerBaseInfo](https://github.com/EasyCraftPanel/EasyCraft/blob/main/EasyCraft/Base/Server/ServerBaseInfo.cs))

* `Server.GetStatus`: 获取服务器状态

  * 传入: `int`: 服务器ID

  * 返回: `int`: 服务器状态

    (0 - Stopped    1 - Starting     2 - Started     3 - Stopping)

* `Server.GetConsoleMessage`: 获取服务器控制台信息

  * 传入: `int`: 服务器ID

  * 返回: `List<ConsoleMessage>`

    可以使用dynamic来获取ConsoleMessage, 参考: [ServerStatusInfo](https://github.com/EasyCraftPanel/EasyCraft/blob/main/EasyCraft/Base/Server/ServerStatusInfo.cs)

* `User.GetBasicInfo`: 获取用户基本信息

  * 传入: `int`: 用户ID

  * 返回: `UserInfoBase`: 用户信息

    可用 dynamic获取,参见 [UserInfoBase](https://github.com/EasyCraftPanel/EasyCraft/blob/main/EasyCraft/Base/User/UserInfoBase.cs) 请注意: 你无法直接更改此项且密码为MD5加密

* `User.GetUserIdByName`: 通过用户名获取用户ID

  * 传入: `string`: 用户名
  * 返回: `int`: 用户ID

* `User.CheckUserPassword`: 检测用户密码是否正确 

  * 传入:
    * `string`: 用户名
    * `string`: 密码 with MD5
  * 返回: `bool`: 是否正确

* `User.GetUserIdByAuth`: 通过`HttpContext`中的`auth`获取用户ID

  * 传入: `string`: auth
  * 返回: `int`: 用户ID