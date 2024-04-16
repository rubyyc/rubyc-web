---
date: 2020-01-01
category:
  - CategoryC
tag:
  - tag E
sticky: 10
archive: false
---

# css组件库

## 弹出层(modal)

```css
.modal{
  width: 400px;
  height: 140px;
  background-color: #333;
  position: absolute;
  top: 50%;
  left: 50%;
  margin-top: -70px;
  margin-left: -200px;
}
```

```js
btn.onclick = function(e){
  e.stopPropagation()
  modal.style.display = 'block';
}

document.onclick = function(){
  modal.style.display = 'block';
}

modal.onclick = function(e){
  e.stopPropagation()
}
```