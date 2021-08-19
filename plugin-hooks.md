# 插件钩子

EasyCraft 提供了一些插件钩子, 如果你还有想要开放的钩子可以 [发起Issue](https://github.com/EasyCraftPanel/EasyCraft/issues/new) 或者 进行 Pull Request.

请在 `EasyCraftPlugin.Plugin`下保留你想要监听的接口的同名静态方法.

* OnServerWillStart

  服务器将要开启

  * 传入: `id`: 服务器ID

  * 返回: `bool` 是否允许开服, 如不允许建议在服务器 ConsoleMessages 输出原因

* OnServerWillStop

  服务器将要停止

  * 传入: `id`: 服务器ID
  * 返回: `bool` 是否允许关服, 如如不允许建议在服务器 ConsoleMessages 输出原因.

* OnServerStarted

  服务器已开启

  * 传入: `id`: 服务器ID
  * 返回: 无

* OnServerStopped

  服务器已关闭

  * 传入: `id`: 服务器ID
  * 返回: 无

  

  

## Api 请求

  接收到 API 请求

  * 传入: `HttpContext`
  * 返回: Dictionary<string,object>()
    * block: 不再调用原本的 EasyCraft API 请求
    * status: 是否成功
    * msg: 返回信息
    * data: 返回数据

