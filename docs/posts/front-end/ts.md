---
date: 2024-04-17
category:
  - CategoryC
tag:
  - tag E
sticky: 10
archive: false
---

# ts

ts:超级js,强类型支持,编写代码时精准提示

```bash
npm install typescript -g
tsc -v
npm i @types/node -D
tsc index.ts -w
```

## 类型自动检查或推断

```ts
function sum(params:number) {
  return params * 2
}
```