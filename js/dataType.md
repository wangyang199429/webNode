 ### 001

``` js
let a;
typeof a //undefiend

const str = 'abc';
typeof str // string

const nub = 100;
typeof num //number

const a = ttue;
typeof a // Boole

symble a = 3214;
typeof a // symble

const obj = {};
typeof obj // object

const arr = [];
typeof arr // object
```

### 002

``` js
// nstanceof 运算符用来测试一个对象在其原型链中是否存在一个构造函数的 prototype 属性

const arr = [];
arr intanceof Array // true
```

### 003

``` js
function deepClone(obj) {
    if (typeof obj !== 'object' || obj == null) {
        return obj
    }

    let res
    if (obj instanceof Array) {
        res = []
    } else {
        res = {}
    }

    for (let key in obj) {
        if (obj.hasOwnProperty(key)) {
            res[key] = deepClone(obj[key])
        } else {
            res[key] = obj[key]
        }
    }
    return res
}
```

### 004

``` js
const a = 100 + 10; //100
const b = 100 + '10'; // '10010'
const c = true + '10' // 'true10'
const cd = true + 10 //11
```

### 005

``` js
if (a) {
    //truly 类型的值
} else {
    // falsely 类型的值
}

falsely类型的值有如下：
    !!0 // flase
    !!NaN //false
    !!'' // false
    !![] //false
    !!{} //false
    !!undefiend //false
    !!null // false
```

### 006

``` js
'100' == 100 // true
true == 1 // true
false == 0 // true

// == 会做隐式转换  ===不会哦
```
