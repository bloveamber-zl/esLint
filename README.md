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

可以看到，输出了错误信息。这是因为我们没有指定任何的配置。所以我们先用`eslint --init`进行配置。根据提示配置完毕会自动生成名为`.eslintrc.js`的配置文件。

```
eslint --init
```

配置好的`eslint --init`大致是这样的

```
module.exports = {
    "env": {
        "browser": true,
        "node": true
    },
    "extends": "eslint:recommended",
    "rules": {
        "indent": [
            "error",
            4
        ],
        "linebreak-style": [
            "error",
            "windows"
        ],
        "quotes": [
            "error",
            "single"
        ],
        "semi": [
            "error",
            "never"
        ]
    }
};
```

如果项目根目录下没有 `package.json` 文件，它会提示你先使用 `npm init` 来初始化一个 `package.json` 文件。

重新执行`eslint merge.js`可以看到输出了以下错误：

      1:12  error  Strings must use singlequote                      quotes
      3:1   error  Expected indentation of 4 spaces but found 1 tab  indent
      3:5   error  Extra semicolon                                   semi
      5:1   error  Unexpected console statement                      no-console
      5:17  error  Extra semicolon                                   semi

    ✖ 5 problems (5 errors, 0 warnings)
      4 errors, 0 warnings potentially fixable with the `--fix` option.

错误信息提示的还是很详细的。

Strings must use singlequote ：字符串必须使用单引号

Expected indentation of 4 spaces but found 1 tab： 本应该是4个空格缩进，现在却是1个tab缩进

Extra semicolon ： 存在不必要的分号

Unexpected console statement ： 不允许使用console

针对第4条提示，我们可以禁用`no-console`规则。将配置文件`.eslintrc.js`改为这样：

```
rules": {
        "no-console": [
            "off"
        ]
}
```

在配置文件中可以设置一些规则。

这些规则的等级有三种：

* "off" 或者 0：关闭规则。
* "warn" 或者 1：打开规则，并且作为一个警告。
* "error" 或者 2：打开规则，并且作为一个错误。

## 代码格式化

在ESlint规则列表页面，我们发现有些规则的旁边会带有一个**橙色扳手图标**，表示在执行`eslint`命令时指定`--fix`参数可以**自动修复**该问题。

```
eslint [object] --fix
```

我们可以利用这个特性来自动格式化项目代码，这样就可以保证代码书写风格的统一。我们现在检查一下我们之前的`demo.js`

     1:12  error  Strings must use singlequote                  quotes
      3:1   error  Expected indentation of 4 spaces but found 2  indent
      3:6   error  Extra semicolon                               semi
      5:17  error  Extra semicolon                               semi

    ✖ 4 problems (4 errors, 0 warnings)
      4 errors, 0 warnings potentially fixable with the `--fix` option.




