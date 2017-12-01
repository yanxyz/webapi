# CORS

Cross-Origin Resource Sharing (CORS)

介绍文件

- [CORS - MDN](https://developer.mozilla.org/en-US/docs/Web/HTTP/CORS)


## 笔记


有 Origin header 并不意味着 CORS。Chrome 等浏览器也会为同域 POST/PUT/DELETE 添加 origin header。


### preflight request



### credentials

xhr 和 fetch 在跨域请求时默认不发送 credentials（cookie, HTTP Authentication 等）。

```js
xhr.withCredentials = true
fetch(url, {
  credentials: 'include'
})
```

response header

```
Access-Control-Allow-Credentials: true
```


## crossorigin attribute



- [Can I Use](http://caniuse.com/#feat=cors)
