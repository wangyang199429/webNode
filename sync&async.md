### 001 promise的基本形式

``` js
function getData(url) {
    return new Promise((resolve, reject) => {
        $.ajax({
            url,
            success(data) {
                resolve(data)
            },
            error(err) {
                reject(data)
            }
        })
    })
}
```

### 002  手写promise加载图片的实例

``` js
function loadImg (url) {
    let p = new Promise((resolve, reject) => {
        let img = document.createElement('img')
        img.onload = () => {
            resolve(img)
        }
        img.onerror = () => {
            reject(img)
        }
        img.src = url
    })
    return p
}

const url1 = 'https://img.mukewang.com/5a9fc8070001a82402060220-140-140.jpg'
const url2 = 'https://img3.mukewang.com/5a9fc8070001a82402060220-100-100.jpg'

loadImg(url1).then(img => {
    console.log(img.width)
    return loadImg(url2)
}).then(img => {
    console.log(img.width)
}).catch(ex => {
    console.log(ex)
})
```