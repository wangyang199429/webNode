### 000 dom&bom

``` html 

    <div id="div1" style="border:1px solid #000;">
        <p id="p1">p 1巴拉巴拉</p>
        <p>p 2</p>
        <p>p 3</p>
    </div>
    <div id="div2" style="border:1px solid #000; margin-top:23px;" >
        <p>p4</p>
        <p>p5</p>
    </div>
    <ul id="list">

    </ul>

``` 

### 001 dom节点操作

``` js
const div1 = document.getElementById('div1')
const div2 = document.getElementById('div2')
//新建节点
const newP = document.createElement('p')
newP.innerHTML = 'p标签的一段文字'
newP.classList.add('p1')
div1.appendChild(newP)
// 移动节点
const p1 = document.getElementById('p1')
div2.appendChild(p1)
console.log(p1.parentNode)
// 获取子元素列表
const div1ChildNode = div1.childNodes
console.log(div1ChildNode)
// Array.prototype.slice.call(div1.childNodes) 可将node节点转换为数组
const div1ChildNodesP = Array.prototype.slice.call(div1.childNodes).filter(child => {
    if (child.nodeType === 1) {
        return true
    } else {
        return false
    }
})
console.log(div1ChildNodesP)
```

### 003 dom接口操作

``` js
// property: 修改对象属性，不会提现到html结构中
// attribute:修改html属性，会改变html结构
// 二者均有可能导致html结构发生变化
```
