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
		"program": "bedrock-server.exe", // 程序路径
		"param": "" // 参数
	},
	"configs": [ // 目前只支持简单对象的修改
		{
            "file":"server.properties",
			"name": "服务器配置文件",
			"type": "properties", // json , ini , yaml , properties
			"known": [
				{
					"key": "server-name",
					"name": "服务器名称",
					"type": 1, // 0 - 布尔值  1 - 文本型  2 - 选择器型
					"visible": true // 默认为 可视
				},
				{
					"key": "gamemode",
					"name": "游戏模式",
					"type": 2,
					"visible": true,
					"selection":[ // 选择器选项
					{
						"value": "survival", // 值
						"display": "生存" // 显示
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
					"type": 1,
					"force": true, // 是否强制更改
					"value": "{{PORT}}"	// 强制更改的值	
				},
				{
					"key": "max-players",
					"name": "玩家数",
					"visible": false,
					"type": 1,
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

* `program`: 程序路径
* `param`: 参数

## configs

> 你也可以为了减小核心配置体积,将此配置项单独出来放置在一个json文件中, 如 `bds-config.json` ,然后将其放置在 `/data/cores/configs` 目录下. 在 `configs` 处你只需要填写 `bds-config`. 此文件内容格式同`configs` 的格式.

服务器的配置项 

* `file`: 配置文件名
* `name`: 文件友好名称,显示在前端
* `type`: 文件类型 (可选类型 `properties` , `json` , `yaml` , `ini`)
* `known`: 已知的配置项数组

### known

* `key`: 配置项在文件中的名称
* `display`: 配置项的友好名称
* `type`: 配置项类型 ( `0` - 布尔值  `1` - 文本型  `2` - 选择器型)
* `visible`: 是否在前端可视 (默认: `true`)
* `selection`: 选择器选项数组
  * `display`: 友好名称,将会显示到前端
  * `value`: 值
* `force`: 是否强制使用值
* `default`: 是否使用默认值, 如未被设置将会设置
* `value`: 强制使用 / 默认 的值, 可使用 [服务器变量](/core-servervar)
