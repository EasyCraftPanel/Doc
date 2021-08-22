# 核心配置

每一个核心都需要一个专门的配置文件,这个配置文件应包含 *核心名称*,*核心版本*,*核心启动指令*等内容

核心采用 JSON 格式编码, 以下是一个核心的示例:

```json
{
	"id": "com.mojang.bds.1.17.11.01",
	"info": {
		"device": 1,
		"branch": "BDS",
		"name": "[BDS] 1.17.11.01"
	},
	"startinfo": {
        "windows":{
            "program": "{{SERVERDIR}}/bedrock-server.exe",
			"param": ""
        }
	},
	"configs": [
		{
            "file":"server.properties",
			"name": "服务器配置文件",
			"type": "properties",
			"known": [
				{
					"key": "server-name",
					"name": "服务器名称",
					"type": "text",
					"visible": true
				},
				{
					"key": "gamemode",
					"name": "游戏模式",
					"type": "select",
					"visible": true,
					"selection":[
					{
						"value": "survival",
						"display": "生存"
					},
					{
						"value": "creative",
						"display": "创造"
					},
					{
						"value": "adventure",
						"display": "冒险"
					},
					
					]
				},
				{
					"key": "server-port",
					"name": "服务器端口",
					"visible": false,
					"type": "text",
					"force": true,
					"value": "{{PORT}}"
				},
				{
					"key": "max-players",
					"name": "玩家数",
					"visible": false,
					"type": "text",
					"force": true,
					"value": "{{PLAYER}}"
				}
			]
		}
	]
}
```

## info

* `device`: 核心允许的 MC 设备类型. `0` 为 PC 端, `1` 为 基岩端, `2` 为双端

* `branch`: 服务器核心分支名称. 如之前已经发布过此类资源请参考之前的值. 否则你可以进行命名. 命名按照原名称进行 

  !> 特别的: `Bedrock Dedicated Server` (基岩服务端) => `BDS`

* `name`: 显示在前端的名称

## startinfo

此参数为启动类型, 将会在开启前传递给开服器进行开服. 此处的参数允许使用 [服务器变量](/core-servervar)

* `key`: 系统版本 (`windows`,`linux`)

  在开服时若不包含当前运行系统将不会开服

* `program`: 程序路径
* `param`: 参数

## configs

> 你也可以为了减小核心配置体积,将此配置项单独出来放置在一个json文件中 
>
> 如 `bds-config.json` ,然后将其放置在 `/data/cores/configs` 目录下. 
>
> 在 `configs` 处你只需要填写 `bds-config`
>
> 此文件内容格式同`configs` 的格式.

服务器的配置项 

* `file`: 配置文件名
* `name`: 文件友好名称,显示在前端
* `type`: 文件类型 (可选类型 `properties` , `json` , `yaml` , `ini`,`linearray`, `jsonarray`,`yamlpure`)
* `known`: 已知的配置项数组

### known

* `key`: 配置项在文件中的名称

  * 当文件类型为 `properties` 时,请输入配置项名称
  * 当文件类型为 `json` 时,请输入 [JSONPath](https://goessner.net/articles/JsonPath/)
  * 当文件类型为 `ini`时, 请输入 `[配置节]配置项`
  * 当文件类型为 `linearray`时, 请输入 `$index`
  * 当文件类型为 `jsonarray`时,请将设置为 `{"项key":"友好名称"}` 此时将默认 `type` 为 `text`
  * 当文件类型为 `yaml`时,请输入其转换为 JSON 后的 [JSONPath](https://goessner.net/articles/JsonPath/)
  
  

!> 由于对 `yaml`的不完全支持, 我们将会把 Yaml 转换为JSON进行处理. 在后期版本我们将会对 yaml 进行适配

> 如果你想要使用真实的`yaml`,请将文件类型设置为 `yamlpure`. 请确保你的 `yml` 文件为 
>
> 节点一 
>
> &nbsp;&nbsp;&nbsp;&nbsp;子节点 : 值.  
>
> &nbsp;&nbsp;&nbsp;&nbsp;子节点 : 值

* `display`: 配置项的友好名称
* `type`: 配置项类型 ( `toggle` - 布尔值  `text` - 文本型  `select` - 选择器型)
* `visible`: 是否在前端可视 (默认: `true`)
* `selection`: 选择器选项数组
  * `display`: 友好名称,将会显示到前端
  * `value`: 值
* `force`: 是否强制使用值
* `default`: 是否使用默认值, 如未被设置将会设置
* `value`: 强制使用 / 默认 的值, 可使用 [服务器变量](/core-servervar)
