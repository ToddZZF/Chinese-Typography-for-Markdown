---
title: 表格的设计
---

## 表格的设计准则

前后的 margin 与自然段一致，格子内部也要有 padding。表格默认居中。

对于边框，设为 collapse 连在一起比较好看。最上面、th与td之间、最下面的边框比其他格子要粗。另外最左和最右两边无边框。

为了便于区分每一行，hover 时会改变当行的背景颜色。

<style>
    .table table {
        display: block;
        max-width: fit-content;
        table-layout: auto;
        caption-side: top;

        margin-top: 0.5em;
        margin-bottom: 1.5em;
        margin-left: auto;
        margin-right: auto;

        border-collapse: collapse;
        word-break: break-word;
        border-top: 2px solid black;
        border-bottom: 2px solid black;

    }

    .table td,
    .table th {
        padding: 0.25em 0.5em;
        border: 2px solid black;
        min-width: 3em;
    }

    .table th {
        border-top: 2px solid black;
        border-bottom: 2px solid black;
    }

    .table tr th:first-child,
    .table tr td:first-child {
        border-left: none;
    }

    .table tr th:last-child,
    .table tr td:last-child {
        border-right: none;
    }

    .table tr:hover {
        background: rgba(233 240 245);
        transition: background 150ms ease;
    }
</style>

<div class="table">
    <table>
<thead>
<tr>
<th style="text-align:left">表头</th>
<th style="text-align:center">表头</th>
<th style="text-align:right">表头</th>
</tr>
</thead>
<tbody>
<tr>
<td style="text-align:left">左对齐</td>
<td style="text-align:center">居中</td>
<td style="text-align:right">右对齐</td>
</tr>
<tr>
<td style="text-align:left">左对齐</td>
<td style="text-align:center">居中</td>
<td style="text-align:right">右对齐</td>
</tr>
<tr>
<td style="text-align:left">左对齐</td>
<td style="text-align:center">居中</td>
<td style="text-align:right">右对齐</td>
</tr>
</tbody>
</table>
</div>