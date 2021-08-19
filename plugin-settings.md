# 插件设置项

插件设置项分为两类. 第一类为服务器设置项,第二类为全局设置项

## 服务器设置项

此设置项为每个服务器专用的. 请添加 `OnGetServerPluginItems` 的插件钩子, 

* 传入 `int`: 服务器ID ; `int`: 用户ID
* 返回 `Dictionary<string,string>`
  * `display`: 前端显示的友好名称
  * `id`: 配置项id
  * `type`: 配置项类型. 
    * `toggle` - 布尔值
    *  `text` - 文本型 
    * `number` - 整数型
    * `select` - 选择器型
    * `radio` - 单选型
    * `checkbox` - 选择框
    * `textarea` - 文本域
    * `date` - 日期选择
    * `time` - 时间选择
  * `noedit`: 是否可编辑 (`true`为不可编辑,否则可编辑)
  * `value`: 值

设置的话会调用 `OnSetServerPluginItem` 钩子

* 传入: `Dictionary<string,string>` key-value
* 传出: 无

