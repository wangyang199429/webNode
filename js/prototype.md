### 001 class和继承

``` js
// 创建类
class people {
    constructor(name, age) {
        this.name = name;
        this.age = age
    }
    sayHi() {
        console.log( `Hi 我叫${this.name} 我今年${this.age}了` )
    }
}

// 创建子类去继承父类
class student extends people {
    constructor(name, age, sid) {
        super(name, age)
        this.sid = sid
    }
    say() {
        console.log( `我叫${this.name},今年${this.age}了,学号为${this.sid}` )
    }

}
let wangyang = new student('王洋', 26, 22)
console.log(wangyang.say())

wangyang instanceof people // true
wangyang instanceof student // true
wangyang instanceof Object // true
```

### 002 原型和原型链

``` js
> // 创建类
class people {
    constructor(name, age) {
        this.name = name;
        this.age = age
    }
    sayHi() {
        console.log( `Hi 我叫${this.name} 我今年${this.age}了` )
    }
}
// 创建子类去继承父类
class student extends people {
    constructor(name, age, sid) {
        super(name, age)
        this.sid = sid
    }
    say() {
        console.log( `我叫${this.name},今年${this.age}了,学号为${this.sid}` )
    }
}
let wangyang = new student('王洋', 26, 22)
console.log(wangyang.say())
```

> 三句话：

    1. 每个class 都有一个显示原型 prototype
    2. 每个实例都有一个隐式原型_proto_
    3. _proto_指向prototype

### 003 手写jQuery

>

``` js
class jQuery {
    constructor(selector) {
        const res = document.querySelectorAll(selector)
        const length = res.length
        for (let i = 0; i < length; i++) {
            this[i] = res[i]
        }
        this.length = res.length
    }
    get(index) {
        return this[index]
    }
    ench(fn) {
        for (let i = 0; i < this.length; i++) {
            const elem = this[i]
            console.log(this)
            fn(elem)
        }
    }
    on(type, fn) {
        return this.ench(elem => {
            elem.addEventListener(type, fn, false)
        })
    }
}
// 插件
jQuery.prototype.dialog = function(into) {
    alert(into)
}

// 复写  造轮子
class myjQuery extends jQuery {
    constructor(selector) {
        super(selector)
    }
    addClass(className) {}
    style(data) {

    }
}
```

### 004 普通函数取window

``` JS
const wang = {
    a: 100,
    say() {
        console.log(this)
    },
    fun() {
        setTimeout(function() {
            // windows
            console.log(this)
        }, 1)
    }
}
console.log(wang.fun())
```

### 005 箭头函数this取上级作用域

``` js
const wang = {
    a: 100,
    say() {
        console.log(this)
    },
    fun() {
        setTimeout(() => {

            console.log(this)
        }, 1)
    }
}
console.log(wang.fun())
```

### 006 用call 和apply手写一个bind函数

``` js
Function.prototype.bind1 = function() {
    // 将参数拆解为数组
    const args = Array.prototype.slice.call(arguments)
    // 获取this(数组第一项)
    const t = args.shift()
    // fn1.bind(...) 中的fn1
    const self = this
    return function() {
        return self.apply(t, args)
    }
}

function fn1(a, b, c) {
    console.log('this', this)
    console.log(a, b, c)
    return 'this is fn1'
}
const fn2 = fn1.bind1({
    x: 100
}, 10, 20, 30)
const res = fn2()
console.log(res)
```

### 007 实现闭包数据被隐藏的一个函数

``` js
function createCache() {
    const data = {} // 闭包中的数据， 被隐藏
    return {
        set: function(key, value) {
            data[key] = value
        },
        get: function(key) {
            return data[key]
        }
    }
}
let res = createCache()
res.set('name', 'wangyyang')
console.log(res.get('name'))
```

### 008 实现10个a标签，点击出现各自编号

``` js
let a
for (let i = 0; i < 10; i++) {
    a = document.createElement('a')
    a.innerHTML = i + '<br>'
    a.addEventListener('click', function(e) {
        e.preventDefault();
        alert(i)
    })
    document.body.appendChild(a)
}
```
