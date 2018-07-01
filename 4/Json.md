# <center><font face="微软雅黑">Json
2018/6/30 13:40:34 

##JSON介绍
JSON: JavaScript Object Notation(JavaScript 对象表示法)

JSON 是轻量级的文本数据交换格式。

JSON 独立于语言：JSON 使用 Javascript语法来描述数据对象，但是 JSON 仍然独立于语言和平台。JSON 解析器和 JSON 库支持许多不同的编程语言。 目前非常多的动态（PHP，JSP，.NET）编程语言都支持JSON。

JSON 具有自我描述性，更易理解

##JSON语法

###规则

- 数据在名称/值对中
- 数据由逗号分隔
- 大括号保存对象
- 中括号保存数组

###json名称/值对
    "name" : "value"

###json值
- 数字（整数或浮点数）
- 字符串（在双引号中
- 逻辑值（true 或 false）
- 数组（在中括号中）
- 对象（在大括号中）
- null

###json对象
    {
		"name" : "百度",
		"url" : "www.baidu.com"
	}

###json数组
    {
		"sites" : [
			{
				"name" : "百度",
				"url" : "www.baidu.com"
			},
			{
				"name" : "谷歌",
				"url" : "www.google.com"
			}
		]
	}

###json使用js语法
    let sites = [
		{
			"name" : "百度",
			"url" : "www.baidu.com"
		}
	];

###JSON.parse()

JSON 通常用于与服务端交换数据。

在接收服务器数据时一般是字符串。

我们可以使用 JSON.parse() 方法将数据转换为 JavaScript 对象。

####语法

    JSON.parse(text[, reviver])

- text:必需， 一个有效的 JSON 字符串。
- reviver: 可选，一个转换结果的函数， 将为对象的每个成员调用此函数。

###JSON.stringify()

JSON 通常用于与服务端交换数据。

在向服务器发送数据时一般是字符串。

我们可以使用 JSON.stringify() 方法将 JavaScript 对象转换为字符串。

####语法
    JSON.stringify(value[, replacer[, space]])

- value: 必需， 一个有效的 JSON 对象。
- replacer: 可选。用于转换结果的函数或数组。如果 replacer 为函数，则 JSON.stringify 将调用该函数，并传入每个成员的键和值。使用返回值而不是原始值。如果此函数返回undefined，则排除成员。根对象的键是一个空字符串：""。如果 replacer 是一个数组，则仅转换该数组中具有键值的成员。成员的转换顺序与键在数组中的顺序一样。当 value 参数也为数组时，将忽略 replacer 数组。
- space: 可选，文本添加缩进、空格和换行符，如果 space 是一个数字，则返回值文本在每个级别缩进指定数目的空格，如果 space 大于 10，则文本缩进 10 个空格。space 有可以使用非数字，如：\t。