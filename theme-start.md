* # 快速开始编写主题

  在编写主题时,你应当确认以下信息

  * 主题名称
  * 独一无二的主题ID

  ## 1. 创建目录结构

  创建文件夹 panel/themes/{主题ID}/  在其中创建文件夹及文件,使它看起来像下面这样

  ```
  themeid
  |
  |-- assets
  |-- component
  |-- page
  |-- config (待定)
  |-- manifest.json (待定)
  ```

  ## 2. 各目录作用

  * **assets** 存放主题可能会引用的CSS,JS,图片文件

    ?> 我们建议您使用 CDN (例如 [BootCDN](https://www.bootcdn.cn/) )来访问一些公开的CSS,JS以减少服务器开销

  * **components** 内存放主题页面需要引用的组件 扩展名为*html*

  * **pages** 存放控制面板的页面样式文件,扩展名为*html*,用户访问 http://域名/page/* 将会被定向至此处 (主页会重定向到 `http://域名/page/index`)

  * **config** 存放可以引用的配置文件, 扩展名为*json* (待定)

  * **manifest.json** 声明了主题的关键信息,如名称等. (待定)