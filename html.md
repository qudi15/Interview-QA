## Front-end HTML Interview Q/A

* What does a `doctype` do?
  * 告诉解析器使用哪种标准解析当前文档
* What's the difference between full standards mode, almost standards mode and quirks mode?
  * 目的: 兼容
  * 使用: `doctype` 和 `<meta http-equiv="X-UA-Compatible" content="IE=5" >`
  * 区别:
    * Box model 
      * quirks: border + padding + content
      * standard: content
    * Image vertical-align
      * quirks: bottom
      * standard: base-line
    * Table Font inherit
      * quirks: In(family), Out(font-size，font-style，font-weight)
      * standard: All
    * Replaced and non-replaced inline element
      * quirks: self width & height like replaced
      * standard: depends on content
    * Element size percentage
      * quirks: a 90% height div in table cell height does work
      * standard: fine
    * Default overflow
      * quirks: resized with children
      * standard: visible
* What's the difference between HTML and XHTML?
  * HTML
    * `<html>` 必须是root元素
    * `<head>`和`<body>`是`<html>`中一定有且只有的元素
  * XHTML
    * html元素需要有xml相关属性
    * 元素名必须是小写字母
    * 元素属性用"包围,不能为空值
    * 在内容里不能有&, 需要转义，包括其他特殊字符<>
    * 空元素以 />结尾
* Are there any problems with serving pages as `application/xhtml+xml`?
  * Same as difference between HTML and XHTML
* How do you serve a page with content in multiple languages?
  * 多语言静态页
  * 动态页
* What kind of things must you be wary of when design or developing for multilingual sites?
  * 默认页 - 在没有相匹配到语言
  * Unicode encoding
  * `lang` 属性
  * 字体(方向，大小等)
* What are `data-` attributes good for?
  * JS
    * getAttribute()
    * dataset
  * CSS
    * attr()
* Consider HTML5 as an open web platform. What are the building blocks of HTML5?
  * 语义化标签
  * vedio & audio
  * JavaScript Api
    * web socket
  * canvas & SVG
  * Workers
  * Storage
    * localStorage
    * sessionStorage
    * webSQL/indexDB
* Describe the difference between a `cookie`, `sessionStorage` and `localStorage`.
  * size
    * cookie: 4k
    * storage: 5m
  * life cycle
    * cookie:
      * expire date
      * session
    * sessionStorage: tab关闭时销毁
    * localStorage: 长期保留
  * cookie可被请求传递
* Describe the difference between `<script>`, `<script async>` and `<script defer>`.
  * 同步加载及运行
  * async: 加载及运行并发(异步)
  * defer: 记载并发(异步)，运行在DOMContentLoaded之前
* Why is it generally a good idea to position CSS `<link>`s between `<head></head>` and JS `<script>`s just before `</body>`? Do you know any exceptions?
  * link 
    * IE 只要看到HTML 标签就会进行绘制
    * chrome 不管css放在前面还是后面，都要等到CSSOM构建形成后才会绘制到页面上
    * firefox 放在head则会阻塞绘制，放在body末尾会先绘制前面的标签
  * script 同 async/defer

* What is progressive rendering?
  * Lazy load
  * 缩减首屏内容的大小
* Have you used different HTML templating languages before?
  * jade