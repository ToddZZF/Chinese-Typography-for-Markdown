---
title: 图片的设计
typography: style
---

## 图片的设计准则

首先图片不能超出左右的范围（max-width: 100%），如果不能铺满，则应该居中。另外图片不能超过屏幕的显示范围（max-heigth: 100vh），同时保持长宽比不变（object-fit: scale-down）

另外为了避免图片在打印时跨页，设置了 `page-break-inside: avoid;`。

<style>
    .image img {
        display: block;
        max-width: 100%;
        max-height: 100vh;
        object-fit: scale-down;
        margin-inline-start: auto;
        margin-inline-end: auto;
        margin-block-start: 0.5em;
        margin-block-end: 1.5em;

        page-break-before: auto;
        page-break-after: auto;
        page-break-inside: avoid;
    }
</style>

<div class="image">
<p><img src="images/wallhaven-6oxwpx.jpg" alt="alternate text" title="title"></p>
</div>

<div class="image">
<p><img src="images/wallhaven-q2xvkl.png" width="500" alt="alternate text" title="title"></p>
</div>
