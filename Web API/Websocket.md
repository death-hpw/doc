[参考资料](https://www.runoob.com/html/html5-websocket.html)

## 定义

基于TCP协议的双工通信协议。
WebSocket是HTML5开始提供的一种在单个TCP连接上进行全双工通讯的协议。

WebSocket使得客户端和服务端之间的数据交换变得更加简单，允许服务端主动向客户端推送。且客户端和服务端只需一次握手，两者之间就可以直接创建永久性的连接，并进行双向数据传输。

使用场景便是替换Ajax轮询。传统轮询的模式需要不断向服务端发出请求，浪费很多资源。WebSocket协议更好的节省服务器资源和带宽，更好的实时通讯。


## 特点

- 只需完成一次握手，便可在Server、client端实现持久性连接
- 双工通信，数据双向传输，实时通讯，服务端可主动push
- 更好的节省宽带和资源

## 常用API

```js

// 创建
let ws = new WebStocket();

// readyState属性
0: 连接尚未建立
1: 已连接，可以通信
2: 连接正在关闭
3: 连接已关闭或不能打开

// 事件
onopen: 连接时触发
onclose: 连接关闭触发
onmessage: 客户端接收服务端数据触发
onerror: 连接发生错误触发

ws.send() // 使用连接发送数据
ws.close() // 关闭连接
```

