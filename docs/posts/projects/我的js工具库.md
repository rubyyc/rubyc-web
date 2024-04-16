---
date: 2022-01-03
category:
  - CategoryA
  - CategoryB
tag:
  - tag A
  - tag B
---

# 我的js工具库 r.js

## 截流函数

Here is the content.

### Heading 3

Here is the content.


# 快速上手

::: warning
VuePress v2 目前仍处于 RC (Release Candidate) 阶段。你已经可以用它来构建你的站点，但是它的配置和 API 还不够稳定，有可能会发生一些微小的 Breaking Changes 。因此，在每次更新 RC 版本之后，请一定要仔细阅读 [更新日志](https://github.com/vuepress/core/blob/main/CHANGELOG.md)。
:::

## 在线试一试

你可以通过 [StackBlitz](https://stackblitz.com/fork/vuepress) 在你的浏览器里直接使用 VuePress 。

## 安装

### 依赖环境

- [Node.js v18.16.0+](https://nodejs.org/)
- 包管理器，如 [pnpm](https://pnpm.io/zh/)、[yarn](https://classic.yarnpkg.com/en/)、[npm](https://www.npmjs.com/) 等。

::: tip

- 使用 [pnpm](https://pnpm.io/zh/) 时，你需要安装 `vue` 作为 peer-dependencies 。
- 使用 [yarn 2+](https://yarnpkg.com/) 时，你需要在 [`.yarnrc.yml`](https://yarnpkg.com/configuration/yarnrc#nodeLinker) 文件中设置 `nodeLinker: 'node-modules'` 。

:::

### 创建项目

#### 通过命令行创建

你可以通过 [create-vuepress](https://www.npmjs.com/package/create-vuepress) 直接创建项目模板。

<CodeGroup>
  <CodeGroupItem title="pnpm" active>

```bash
pnpm create vuepress vuepress-starter
```

  </CodeGroupItem>

  <CodeGroupItem title="yarn">

```bash
yarn create vuepress vuepress-starter
```

  </CodeGroupItem>

  <CodeGroupItem title="npm">

```bash
npm init vuepress vuepress-starter
```

  </CodeGroupItem>
</CodeGroup>

#### 手动创建

这一章节会帮助你从头搭建一个简单的 VuePress 文档网站。

- 创建并进入一个新目录

```bash
mkdir vuepress-starter
cd vuepress-starter
```

- 初始化项目

<CodeGroup>
  <CodeGroupItem title="pnpm" active>

```bash
git init
pnpm init
```

  </CodeGroupItem>

  <CodeGroupItem title="yarn">

```bash
git init
yarn init
```

  </CodeGroupItem>

  <CodeGroupItem title="npm">

```bash
git init
npm init
```

  </CodeGroupItem>
</CodeGroup>

- 安装 VuePress

<CodeGroup>
  <CodeGroupItem title="pnpm" active>

```bash
# 安装 vuepress 和 vue
pnpm add -D vuepress@next vue
# 安装打包工具和主题
pnpm add -D @vuepress/bundler-vite@next @vuepress/theme-default@next
```

  </CodeGroupItem>

  <CodeGroupItem title="yarn">

```bash
# 安装 vuepress
yarn add -D vuepress@next
# 安装打包工具和主题
yarn add -D @vuepress/bundler-vite@next @vuepress/theme-default@next
```

  </CodeGroupItem>

  <CodeGroupItem title="npm">

```bash
# 安装 vuepress
npm install -D vuepress@next
# 安装打包工具和主题
npm install -D @vuepress/bundler-vite@next @vuepress/theme-default@next
```

  </CodeGroupItem>
</CodeGroup>

- 创建 `docs` 目录和 `docs/.vuepress` 目录

```bash
mkdir docs
mkdir docs/.vuepress
```

- 创建 VuePress 配置文件 `docs/.vuepress/config.js`

```ts
import { viteBundler } from '@vuepress/bundler-vite'
import { defaultTheme } from '@vuepress/theme-default'
import { defineUserConfig } from 'vuepress'

export default defineUserConfig({
  bundler: viteBundler(),
  theme: defaultTheme(),
})
```

- 创建你的第一篇文档

```bash
echo '# Hello VuePress' > docs/README.md
```

## 目录结构

创建完成后，你项目的目录结构应该是这样的：

```
├─ docs
│  ├─ .vuepress
│  │  └─ config.js
│  └─ README.md
└─ package.json
```

`docs` 目录是你放置 Markdown 文件的地方，它同时也会作为 VuePress 的源文件目录。

`docs/.vuepress` 目录，即源文件目录下的 `.vuepress` 目录，是放置所有和 VuePress 相关的文件的地方。当前这里只有一个配置文件。默认还会在该目录下生成临时文件、缓存文件和构建输出文件。建议你把它们添加到 `.gitignore` 文件中。

::: details 示例 `.gitignore` 文件

```
# VuePress 默认临时文件目录
.vuepress/.temp
# VuePress 默认缓存目录
.vuepress/.cache
# VuePress 默认构建生成的静态文件目录
.vuepress/dist
```

:::

## 开始使用 VuePress

### 启动开发服务器

你可以在 `package.json` 中添加一些 [scripts](https://classic.yarnpkg.com/zh-Hans/docs/package-json#toc-scripts) ：

```json
{
  "scripts": {
    "docs:dev": "vuepress dev docs",
    "docs:build": "vuepress build docs"
  }
}
```

运行 `docs:dev` 脚本可以启动开发服务器:

<CodeGroup>
  <CodeGroupItem title="pnpm" active>

```bash
pnpm docs:dev
```

  </CodeGroupItem>

  <CodeGroupItem title="yarn">

```bash
yarn docs:dev
```

  </CodeGroupItem>

  <CodeGroupItem title="npm">

```bash
npm run docs:dev
```

  </CodeGroupItem>
</CodeGroup>

VuePress 会在 [http://localhost:8080](http://localhost:8080) 启动一个热重载的开发服务器。当你修改你的 Markdown 文件时，浏览器中的内容也会自动更新。

### 构建你的网站

运行 `docs:build` 脚本可以构建你的网站：

<CodeGroup>
  <CodeGroupItem title="pnpm" active>

```bash
pnpm docs:build
```

  </CodeGroupItem>

  <CodeGroupItem title="yarn">

```bash
yarn docs:build
```

  </CodeGroupItem>

  <CodeGroupItem title="npm">

```bash
npm run docs:build
```

  </CodeGroupItem>
</CodeGroup>

## json序列化与字符串化
```js
// 解析
JSON.parse(xxx)
// 字符串序列化
JSON.stringify(xxxx)
```
## 数组浅克隆

## 数组深克隆

## 封装一个函数,可以返回所有子元素节点（兼容IE6）,类似children的功能
主要判断nodeType === 1

## 封装一个函数,可以返回前一个元素的兄弟节点
主要判断nodeType === 1

## 封装一个函数,可以返回元素的所有兄弟节点

## 对象的深克隆

## 对象的浅克隆

## 范围内的随机数
```js
parseInt(Math.random()*8)-4
```

## 得到[a,b]区间的整数
```js
parseInt(Math.random()*(b-a+1))+a
```

## 删除数组中的第i项

```js
arr.splice(i,1)
```

## 求数组的最大值

```js
var arr = [3,4,5,6,9]
var max = Math.max.apply(null,arr)
// es6
var max = Math.max(...application_record)
console.log(max);
```

## exec()方法的逐条遍历

```js
var str8 = 'abc123def456ghi789'
var regex8 = /\d+/g

while(result = regex8.exec(str8)){
  console.log(result);
}
```