---
date: 2024-04-02
category:
  - Electron
  - React
tag:
  - Markdown
  - 七牛云
---

# Electron+React+Nodejs+七牛云打造Markdown云同步编辑器

## 查看运行环境并创建工程

```bash
node -v
npm -v
mkdir my-electron-app && cd my-electron-app
npm init
```

### package.json

```json title="package.json"
{
  "name": "react-markdown",
  "version": "1.0.0",
  "description": "",
  "main": "main.js",
  "scripts": {
    "test": "echo \"Error: no test specified\" && exit 1",
    "start": "electron ."
  },
  "author": "",
  "license": "ISC"
}

```

### 安装electron
```bash
npm install --save-dev electron
```

### 运行
```bash
npm run start
```
