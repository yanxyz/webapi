# CSSOM-View

## viewport

视口尺寸 window.innerWidth/innerHeight，包括 scrollbar。

页面滚动距离 window.scrollX/scrollY。

滚动页面 window.scrollTo(), window.scrollBy()。


---

下面属性，如果 element 没有 box(display: none)，返回 null 或 0。

## scroll

scrolling area，
对于 viewport 是容纳所有 elements(margin) 的 box；
对于 element 是容纳所有后代的 margin-box 的 box；

element 的 padding-box 左上角在 scroll area 中的位置。

scrollTop/scrollLeft 既是 getter 也是 setter。
用作 setter 时在背后调用 scrollTo()。

scrollTop

- html, 在 standard mode 下返回 window.scrollY； 在 quirks mode 下返回 0。
- body, 在 standard mode 下同普通 element; 在 quirks mode 下返回 window.scrollY。

Chrome < 61 始终用 body，[chromestatus](https://www.chromestatus.com/features/6386758136627200)

```js
// clientHeight 不包含 scrollbar
var viewportHeight = (document.compatMode === 'CSS1Compat'
  ? document.documentElement : document.body).clientHeight

var pageHeight = Math.max(document.documentElement.scrollHeight,
  document.body.scrollHeight)

var pageY = document.documentElement.scrollTop || document.body.scrollTop
```

## client

4 个只读属性

- clientTop, clientLeft
- clientHeight, clientWidth

element 的 padding-box 左上角在 border-box 中的位置。

如果有滚动条，滚动条出现在 padding 和 border 之间，占用 content 的尺寸（即 content 的尺寸减小）。

- clientTop/clientLeft, 要加上滚动条，不过实际中没有上滚动条和左滚动条。
- clientWidth/clientHeight，要减去滚动条。

clientHeight

- inline 返回 0
- html 在 standard mode 下返回 viewpaort height - scrollbar height
- body 在 quirks mode 下返回 viewpaort height - scrollbar height

## offset

element 的 border-box 左上角在它的 offsetParent padding-box 中的位置。

offsetParent

- html, body, fixed, none 为 null
- 从 element 的 parent 开始向上查找
  - position: absolute 的 container block
  - body

IE < 11, element display: none offsetParent 不为 null。

## 资料

- [CSS Object Model (CSSOM)](https://drafts.csswg.org/cssom/)
