# ESLint

ESLint是一个插件化的javascript代码检测工具，它可以用于检查常见的JavaScript代码错误，也可以进行代码风格检查，这样我们就可以根据自己的喜好指定一套ESLint配置，然后应用到所编写的项目上，从而实现**辅助编码规范的执行，有效控制项目代码的质量。**

## 安装

你可以使用 npm 来安装 ESLint:

```
npm install eslint -g
```

## 用法

如果你首次使用 ESLint，那么你需要先设置一个配置文件，你可以在项目根目录下使用 `--init` 选项来生成:

```
eslint --init
```

如果项目根目录下没有 `package.json` 文件，它会提示你先使用 `npm init` 来初始化一个 `package.json` 文件。

