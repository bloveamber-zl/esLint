# ESLint

ESLint是一个插件化的javascript代码检测工具，它可以用于检查常见的JavaScript代码错误，也可以进行代码风格检查，这样我们就可以根据自己的喜好指定一套ESLint配置，然后应用到所编写的项目上，从而实现**辅助编码规范的执行，有效控制项目代码的质量。**

## 安装

你可以使用 npm 来安装 ESLint:

```
npm install eslint -g
```

## 用法

自己写了一个包含几行js代码的文件，保存为demo.js。

```
var a=10,b="haomo"
for(var i=0;i<5;i++){
	a++;
}
console.log(a,b);
```

然后执行`node demo.js`确保它是可以正确运行的（输出结果为`15 'haomo'`）。

接着我们执行以下命令来使用ESLint检查：

```
$ eslint demo.js
```



安装完毕后，接下来新建一个配置文件`.eslintrc.js`，或者使用如下的命令行来自动生成。

```
eslint --init
```

如果项目根目录下没有 `package.json` 文件，它会提示你先使用 `npm init` 来初始化一个 `package.json` 文件。

## 规则

在配置文件中可以设置一些规则。

这些规则的等级有三种：

* "off" 或者 0：关闭规则。
* "warn" 或者 1：打开规则，并且作为一个警告（不影响exit code）。
* "error" 或者 2：打开规则，并且作为一个错误（exit code将会是1）。

例如：

* js 文件

```
// .eslintrc.js
module.exports = {
  rules: {
    eqeqeq: 'off',
    curly: 'error',
  },
};
```

* 注释文件

```
/* eslint eqeqeq: "off", curly: "error" */
/* eslint eqeqeq: 0, curly: 2 */
```

也可以在注释中关闭所有或者某个规则：

```
/* eslint-disable */
/* eslint-enable */

/* eslint-disable no-alert, no-console */
/* eslint-enable no-alert, no-console */
```

## 代码格式化

在ESlint规则列表页面，我们发现有些规则的旁边会带有一个**橙色扳手图标**，表示在执行`eslint`命令时指定`--fix`参数可以**自动修复**该问题。

```
eslint [object] --fix
```

我们可以利用这个特性来自动格式化项目代码，这样就可以保证代码书写风格的统一。

