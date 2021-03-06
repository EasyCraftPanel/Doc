# 主题语法

目前主题支持的简单语法:

* 简单的 if 语句 (不支持嵌套)
* 简单的引用 (include)
* 简单的变量输出

下面我会一一举例说明

## if语法

if 语法是在特定条件下渲染部分页面内容的语法,语句非常简单,我们先从一个简单的例子入手

```html
<h1>Example of if</h1>
{if:var.user.login}
<h2>
    You Are Logined
</h2>
{else}
<h2>
    You are not logined, plz Login
</h2>
{endif}

{if:!var.user.login}
<div>This is a login form</div>
{endif} 
```

if 有两个关键部分

```
{if:要判断的变量}
...
{endif}
```

假如说要判断的变量为真(true),将会显示被包裹的语句,否则将会不显示任何东西

同此理,`{else}`的用途已经很明显了

!> 由于技术原因,暂不支持嵌套if语句,不过你可以通过调用 component 来进行伪嵌套,我们将会在发布后收取此需求的急迫性

### 作者注

下面是一些神奇的特性,作者原以为会报错,然而事实是带来了一些神奇的特性

* `{if:}`将会被判断为`false`,同理,`{if:!}`将会判断为`true`

## include 语法

一个简单的include将会引用component文件夹下的html来渲染,同时,你也可以传递一些参数

```
{include:header var.title="登录",var.islogin="false" }
```

其中,`header`为`component`文件夹下的一个组件样式文件名,后面的为传递的参数,每个参数和对应的值以逗号分割,前后的空格将会自动忽略

此时,`header.html`中就可以写 (以下仅为参考)

```html
<html>
    <head>
        <title>{var.title} - {if:var.islogin}已登录{else}未登录{endif}</title>
    </head>
    ........
```

?> 请注意,传递入的参数的编译顺序为从前往后,其中后方如果定义了前文已定义的参数,将会自动忽略,可见下方说明:

```
{include:header var.title="登录", var.title="2233" }
```

最终的`var.title`将会是登录而不是2233

## 变量输出

你可以通过`{变量名}` 来输出变量,请注意,只有以`var.`开头的变量(以及传入的参数)才支持输出

```html
<h1>你已经登录,欢迎{var.user.username}!</h1>
```

如此处,具体的内定变量表可见[主题变量大全](theme-vars.md)

## 变量定义

你现在可以在任意页面/组件定义变量以及他的值. 你也可以将他的值设置为另一个变量的值(非指针) 

但是,定义的变量的优先级低于已定义变量(主题变量表中的变量),且此变量不会传递给下一个include的页面.

下面是示例:

```
{set:var.easycraft.good = "true" }

{set:var.easycraft.myname = var.user.username }
```

?> 假如说是 布尔值(Boolean) 请使用双引号括起来

## Foreach 遍历

新语法!你可以通过foreach来遍历我们提供给你的某些变量(变量表会标注)

