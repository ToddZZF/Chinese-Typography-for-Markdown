---
title: 行内元素
---

## 加粗与斜体

按照一般地采用加粗和斜体：

<style>
    .strong strong {
        font-weight: 600;
    }
</style>

<div class="test-box strong">
    <p>忌蜜符椅东耻椭究训小劝澄缚太阀聊缘资勿萘屁灭忌埃潜付、驾押哥程垛改呀妹宿饶哼汗热卓设介奈架败逮淬螟锣<strong>钼违授描漏背碳俺字傅页齐熏终说革肛泵附仕扬溉炼盏展肆柄猪遭股稼挖烫岸慎神孵孜苞雌稀问</strong>条亚尽、疆赤臭葬巾井籽巷，萤、天荆捆造浦偏洁农扣潜萌盘抽沈。笨薄帘氏，畔铃！</p>
</div>

<style>
    .em em {
        font-style: italic;
    }
</style>

<div class="test-box em">
    <p>忌蜜符椅东耻椭究训小劝澄缚太阀聊缘资勿萘屁灭忌埃潜付、驾押哥程垛改呀妹宿饶哼汗热卓设介奈架败逮淬<em>螟锣钼违授描漏背碳俺字傅页齐熏终说革肛泵附仕扬溉炼盏展肆柄猪遭股稼挖烫岸慎神孵孜苞雌稀问条亚</em>尽、疆赤臭葬巾井籽巷，萤、天荆捆造浦偏洁农扣潜萌盘抽沈。笨薄帘氏，畔铃！</p>
</div>

不过这样有个问题就是不明显。粗体还好，但斜体的话就难以分辨。可以考虑在下面加点：

<style>
    .em-dot em {
        text-emphasis: filled circle;
        text-emphasis-position: under;
    }
</style>

<div class="test-box em-dot">
    <p>忌蜜符椅东耻椭究训小劝澄缚太阀聊缘资勿萘屁灭忌埃潜付、驾押哥程垛改呀妹宿饶哼汗热卓设介奈架败逮淬<em>螟锣钼违授描漏背碳俺字傅页齐熏终说革肛泵附仕扬溉炼盏展肆柄猪遭股稼挖烫岸慎神孵孜苞雌稀问条亚</em>尽、疆赤臭葬巾井籽巷，萤、天荆捆造浦偏洁农扣潜萌盘抽沈。笨薄帘氏，畔铃！</p>
</div>

但这样的话英语又会显得很乱。那么能不能加下划线呢？比如粗体用双下划线，斜体用波浪线（单下划线留给链接）

<style>
    .underline strong {
        text-decoration: underline double currentColor;
        text-decoration-thickness: 0.05em;
        text-underline-offset: 0.1em;
    }
</style>

<div class="test-box underline">
    <p>忌蜜符椅东耻椭究训小劝澄缚太阀聊缘资勿萘屁灭忌埃潜付、驾押哥程垛改呀妹宿饶哼汗热卓设介奈架败逮淬<strong>螟锣钼违授描漏背碳俺字傅页齐熏终说革肛泵附仕扬溉炼盏展肆柄猪遭股稼挖烫岸慎神孵孜苞雌稀问条亚</strong>尽、疆赤臭葬巾井籽巷，萤、天荆捆造浦偏洁农扣潜萌盘抽沈。笨薄帘氏，畔铃！</p>
</div>

<style>
    .underline em {
        text-decoration: underline wavy currentColor;
        text-decoration-thickness: 0.05em;
        text-underline-offset: 0.1em;
    }
</style>

<div class="test-box underline">
    <p>忌蜜符椅东耻椭究训小劝澄缚太阀聊缘资勿萘屁灭忌埃潜付、驾押哥程垛改呀妹宿饶哼汗热卓设介奈架败逮淬<em>螟锣钼违授描漏背碳俺字傅页齐熏终说革肛泵附仕扬溉炼盏展肆柄猪遭股稼挖烫岸慎神孵孜苞雌稀问条亚</em>尽、疆赤臭葬巾井籽巷，萤、天荆捆造浦偏洁农扣潜萌盘抽沈。笨薄帘氏，畔铃！</p>
</div>

我觉得这种方式不错。而且可以和记笔记时的习惯保持一致。但这样有个很严重的问题就是当加粗和斜体同时出现时，下划线会重合在一起，并且如果中间有链接的话，下划线也会重叠。所以这种方案最终还是被排除了。

## 链接

<style>
    a.link {
        color: blue;
        text-decoration: underline solid blue;
        text-decoration-thickness: 0.05em;
        text-underline-offset: 0.1em;
    }

    a.after::after {
        content: "↩"
    }
</style>

默认的链接是直接用下划线的，颜色与一般文字不同，比如：<a href="#">链接</a>。可以微调一下下划线的样式，改成这样：
<a class="link">链接</a>。要加其他装饰也可以，比如 <a class="link after">链接</a>

<style>
    a.animate {
        display: inline;
        color: blue;
        position: relative;
        text-decoration: none;
        transition: all 250ms ease-in;
        box-shadow: 0 -2px rgba(189, 195, 199, 0.5)inset;
        background-color: transparent;
    }
    a.animate:hover {
        box-shadow: 0 calc(-1 * 1.2rem) rgba(189,195,199, 0.5) inset;
    }

    a.animate:visited:not(:hover) {
        color: #551AB8;
    }
</style>

另外，链接 hover 和 active 时最好有动画效果，visited 的链接也应该有所不同。我比较喜欢的动画效果是这样的：<a class="animate after" href="https://baidu.com">链接</a>（跟 hugo-theme-stack 学的）

## 删除线

<style>
    .del del {
        text-decoration: line-through solid currentColor;
    }
</style>

<div class="test-box del">
    <p>忌蜜符椅东耻椭究训小劝澄缚太阀聊缘资勿萘屁灭忌埃潜付、驾押哥程垛改呀妹宿饶哼汗热卓设介奈架败逮淬<del>螟锣钼违授描漏背碳俺字傅页齐熏终说革肛泵附仕扬溉炼盏展肆柄猪遭股稼挖烫岸慎神孵孜苞雌稀问条亚</del>尽、疆赤臭葬巾井籽巷，萤、天荆捆造浦偏洁农扣潜萌盘抽沈。笨薄帘氏，畔铃！</p>
</div>

## code

见code的那个文件。
