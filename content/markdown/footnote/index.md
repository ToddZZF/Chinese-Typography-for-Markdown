---
title: 脚注的设计
typography: style
---

## 脚注的设计准则

脚注采用与论文参考文献类似的格式，用 `[1]` 来表示一个脚注。

<style>
    a.footnote-ref::before {
        content: "[" !important;
    }
    a.footnote-ref::after {
        content: "]" !important;
    }
    .footnotes a::after {
        content: "" !important;
    }
    .footnotes li p {
        margin: 0;
    }
    .footnotes ol>li::before {
        content: "[" counter(list-item) "] ";
    }
</style>

脚注 [^1] [^2] [^2] [^3]

[^1]: 脚注 1
[^2]: 脚注 2
[^3]: 脚注 3
