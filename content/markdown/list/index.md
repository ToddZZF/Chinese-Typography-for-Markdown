---
title: 列表的设计
---

## 旧方案

> 为了解决对齐问题，后面重新设计了 list

列表作为块元素，其上下边距与一般的段落一样。列表的缩进可以采用 2em

<style>
    .list ul, .list ol {
        list-style-position: outside;
        display: block;
        margin-block-start: 0.5em;
        margin-block-end: 1.5em;
        padding-inline-start: 2em;
    }

    .list ul {
        list-style-type: disc;
    }

    .list ol {
        list-style-type: decimal;
    }

    .list ul ul,
    .list ul ol,
    .list ol ul,
    .list ol ol
     {
        margin-block-start: 0;
        margin-block-end: 0;
    }
    .list li {
        display: list-item;
        list-style-type: unset;
    }
</style>

<div x-data="{padding: '2em'}" class="test-box list">
    <p>padding-inline-start:</p>
    <input type="text" x-model="padding">
    <ul>
        <li>列表一
            <ul :style="{'padding-inline-start': padding}">
                <li>子列表</li>
                <li>子列表</li>
            </ul>
        </li>
        <li>列表二</li>
        <li>列表三</li>
    </ul>
</div>

为了更好地区分不同层级的列表，可以采用不同的 list-style-type，比如：

<style>
    .marker ul ul {
        list-style-type: circle;
    }
    .marker ul ul ul {
        list-style-type: square;
    }
</style>

<div class="test-box list marker">
    <ul>
        <li>列表一
            <ul>
                <li>子列表</li>
                <li>子列表
                    <ul>
                        <li>子列表</li>
                        <li>子列表</li>
                    </ul>
                </li>
            </ul>
        </li>
        <li>列表二</li>
        <li>列表三</li>
    </ul>
</div>

对于 order list，除了 list-style-type 不同其余一致。

<div class="test-box list marker">
    <ol>
        <li>列表一
            <ol>
                <li>子列表</li>
                <li>子列表
                    <ol>
                        <li>子列表</li>
                        <li>子列表</li>
                    </ol>
                </li>
            </ol>
        </li>
        <li>列表二</li>
        <li>列表三</li>
    </ol>
</div>

还有一种 task list 比较特殊，如果不加处理，它默认会以 unorder list+checkbox 的形式出现：

<div class="test-box list task-list">
    <ul>
        <li><input type="checkbox"> 任务一</li>
        <li><input checked="" type="checkbox"> 任务二</li>
    </ul>
</div>

但有个问题是 Goldmark 它生成的 HTML `<ul>` 是不带 `check-list` class 的，单纯多一个 checkbox。目前的 CSS 选择器无法实现父类选择，只能用是用实验性的 `:has` 选择器去选择 `<li>`，或者用 js 去检查每个 `<li>` 是否包含 checkbox。这两种方法都不太好。

我使用了一种比较曲折的方法，用 checkbox 覆盖 `::marker`。由于原有的 checkbox 是透明的，所以我又重新定义了其样式（参考 [Pure CSS Custom Checkbox Style](https://moderncss.dev/pure-css-custom-checkbox-style/)）。但这种方式对齐有问题，缩放后就对不齐了。

<style>
    .hide-marker li input[type="checkbox"] {
        margin-left: -1.35em;
        appearance: none;
        font: inherit;
        color: currentColor;
        width: 0.85em;
        height: 0.85em;
        border: 0.15em solid currentColor;
        border-radius: 0.15em;
    }

    .hide-marker li input[type="checkbox"]::before {
        content: "";
        width: 0.65em;
        height: 0.65em;
        transform: scale(0.8);
        box-shadow: inset 1em 1em white;
    }

    .hide-marker li input[type="checkbox"] {
  /* ...existing styles */
  display: inline-grid;
  place-content: center;
}


.hide-marker li input[type="checkbox"]:checked::before {
  box-shadow: inset 1em 1em black;
}
</style>

<div class="test-box list task-list hide-marker">
    <ul><li><input type="checkbox"> Uncheck<ul><li>无序列表</li><li>无序列表</li></ul></li><li><input checked="" type="checkbox"> Check<ul><li><input type="checkbox"> Uncheck</li><li><input checked="" type="checkbox"> Check</li></ul></li><li><input checked="" type="checkbox"> Check<ol><li>有序列表</li><li>有序列表</li></ol></li></ul>
</div>

在我尝试解决对齐问题时，我搜到这么一个问题：[Set width of ::marker](https://stackoverflow.com/questions/73062487/set-width-of-marker)，这个问题提到 ::marker 有可能显示不全。

## 新方案

新方案直接采用 table 来显示 list. ::marker 变为了一个 ::before 元素，占据单独一个 cell，其余内容另占一个 table-row.


