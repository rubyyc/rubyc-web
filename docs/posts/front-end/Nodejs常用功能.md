---
date: 2024-03-20
category:
  - CategoryA
  - CategoryB
tag:
  - tag A
  - tag B
---

# Nodejs

## fs操作

### 读取文件
```js
const { electronAPI } = window
const fs = electronAPI.require('fs')

const importFiles = async ()=>{
console.log('click');
// 通过某种方式获取filepath
const filePath = await window.electronAPI.openFile()
// 读文件
const data = await fs.promises.readFile(filePath,'utf8')
// 处理成json
const allItems = JSON.parse(data);
// 把json处理成jsArray 并写入文件
await fs.promises.writeFile('all.js',JSON.stringify(allItems.items))
}
```


### 写文件

Here is the content.

### Heading 3

Here is the content.
