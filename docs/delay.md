## 延迟函数delay

如下代码
```JavaScript
const delay = ms => new Promise((resolve, reject) => setTimeout(resolve, ms))

const getData = status => new Promise((resolve, reject) => {
    status ? resolve('done') : reject('fail')
})
const getRes = async (data) => {
    try {
        const res = await getData(data)
        const timestamp = new Date().getTime()
        await delay(1000)
        console.log(res, new Date().getTime() - timestamp)
    } catch (error) {
        console.log(error)
    }
}
getRes(true) // 隔了1秒