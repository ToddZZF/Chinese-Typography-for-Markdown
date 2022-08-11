---
title: 代码的设计
---

## 代码的设计准则

目前代码高亮采用 Highlight.js，以后等我弄明白高亮有哪些后再换成css。

```html
<!-- hightlight.js -->
<link href="https://cdn.bootcdn.net/ajax/libs/highlight.js/11.4.0/styles/github-dark-dimmed.min.css" rel="stylesheet">
<script src="https://cdn.bootcdn.net/ajax/libs/highlight.js/11.4.0/highlight.min.js"></script>
<script>hljs.highlightAll();</script>
```

行内代码则简单的设置间距、字体、背景。
