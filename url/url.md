# URL class

- [URL class](https://url.spec.whatwg.org/#url-class)

```js
new URL(url, [base])
```

- 至少有一个参数。
- 只有一个参数时，参数必须是 absolute url
- 有两个参数时，第二个参数必须是 absolute url（href string 或 URL object）；若第一个参数是 absolute url 则忽略第二个参数。

哪些地址是 absolute url

```
// http, https, ftp
http://hostname[:port][pathname]
file://
```

#### protocol

protocol 不区分大小写，getter 返回小写。

#### origin

<https://url.spec.whatwg.org/#origin>

origin 只有 getter，没有 setter。

```

```

#### port

<https://url.spec.whatwg.org/#url-miscellaneous>

默认端口

#### pathname


#### search

#### hash

hash, getter 返回值以 `#` 开始，


## 资料

IE10-11 有 window.URL，但是
