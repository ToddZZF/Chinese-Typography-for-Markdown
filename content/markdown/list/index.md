---
title: 列表的设计
---

列表作为块元素，其上下边距与一般的段落一样。列表的缩进可以采用 2em

<style>
    .list ul, .list ol {
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

<style>
    .task-list ul li input {
        list-style-type: none;
    }
</style>

<div class="test-box list task-list">
    <ul>
        <li><input disabled="" type="checkbox"> 任务一</li>
        <li><input checked="" disabled="" type="checkbox"> 任务二</li>
    </ul>
</div>


