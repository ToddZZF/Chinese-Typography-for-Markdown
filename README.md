# Chinese-Typography-for-Markdown

用于 Markdown 的中文排版样式

对比和实验常见的中文排版样式，并设计一份用于自己博客的样式。因为要用于博客，所以直接用 [Hugo](https://gohugo.io/) 框架（对应的 Markdown parser 为 [goldmark](https://github.com/yuin/goldmark/)），符合 [CommonMark 0.30](https://spec.commonmark.org/0.30/)。

此处详细记录了设计过程和测试样例。

## 进度

- [x] heading
- [x] paragraph
- [x] strong
- [x] em
- [x] del
- [x] link
- [x] list(ol ul task)
- [x] table
- [x] image
- [x] footnote
- [x] code
- [x] blockquote

## resets

有多种重置、统一浏览器默认样式的方法，比如：

- [normalize.css](https://github.com/necolas/normalize.css)
- [reseter.css](https://github.com/resetercss/reseter.css)
- [(new) reset.css](https://github.com/elad2412/the-new-css-reset)

## 借鉴的样式

- [yue.css](https://github.com/typlog/yue.css)
- [entry.css](https://github.com/zmmbreeze/Entry.css)
- [typo.css](https://github.com/sofish/Typo.css)
- [heti.css](https://github.com/sivan/heti)

## 相关资源

- [fonts.css](https://github.com/zenozeng/fonts.css)：跨平台中文字体解决方案
- [中文排版需求](https://www.w3.org/International/clreq/)（需要翻墙）
- [中文文案排版细则](https://dawner.top/posts/chinese-copywriting-rules/#emoji)