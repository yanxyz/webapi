# DOM API

<https://dom.spec.whatwg.org/>

[IE 兼容性](https://github.com/yanxyz/ie/tree/master/webapi/dom/api/)

## NonElementParentNode

这个 interface 的名字，意思是 parentNode 不是 element

```
Element? getElementById(DOMString elementId)
```

## ParentNode

```
HTMLCollection children
Element? firstElementChild
Element? lastElementChild
unsigned long childElementCount

void prepend(...nodes)
void append(...nodes)

Element? querySelector(DOMString selectors)
NodeList querySelectorAll(DOMString selectors)
```

### childElementCount

IE9+ 支持，不过只有 Element 支持，Document 和 DocumentFragment 不支持

### querySelector

querySelectorAll 返回的是静态的 collection，getElementsByTagName 等返回的是实时的 collection。

### prepend

参数是一个或多个 nodes。 type 是 Node 或 DOMString，DOMString 将创建为 TextNode 节点

```js

```

prepend, append 以及下文提到的 before, after, replaceWith，这些方法类似。

IE 不支持这些方法。

## ChildNode

```
void before(...nodes)
void after(...nodes)
void replaceWith(...nodes)
void remove()
```

## NonDocumentTypeChildNode

```
Element? previousElementSibling
Element? nextElementSibling
```

## Node

```
Document? ownerDocument
Node getRootNode(options)

Node? parentNode
Element? parentElement
boolean hasChildNodes()
NodeList childNodes
Node? firstChild
Node? lastChild
Node? previousSibling
Node? nextSibling

DOMString? textContent
DOMString? innerText

Node cloneNode(optional boolean deep = false)

Node insertBefore(Node node, Node? child)
Node appendChild(Node node)
Node replaceChild(Node node, Node child)
Node removeChild(Node child)
```

### contains

```
boolean contains(Node otherNode)
```

没有参数时报错。
otherNode 为 node 自身或 node 后代时返回 true。
其它情况（包含 otherNode 为 null）返回 false。

```js
document.body.contains(document.body)  // true
document.body.contains(null)  // false
```

### normalize

```
void normalize()
```

node 在 normalize 之后不包含 empty text node 或毗邻的 text node。


## Document

```
HTMLCollection getElementsByTagName(DOMString qualifiedName)
HTMLCollection getElementsByTagNameNS(DOMString? namespace, DOMString localName)
HTMLCollection getElementsByClassName(DOMString classNames)
```

[Document](document.md)


## Element

```
Element? closest(DOMString selectors)
boolean matches(DOMString selectors)

Element? insertAdjacentElement(DOMString where, Element element)
void insertAdjacentText(DOMString where, DOMString data)
```

Node tree         | Element tree
---------------   | -------------
parentNode        | parentElement
childNodes        | children
-                 | childElementCount
hasChildNodes()   | -
firstChild        | firstElementChild
lastChild         | lastElementChild
previousSibling   | previousElementSibling
nextSibling       | nextElementSibling


[Element](element.md)

## DocumentFragement


## Text


## Range

[Range](range.md)
