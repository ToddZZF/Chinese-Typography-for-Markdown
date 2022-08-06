---
title: 段落的设计
typography: yue
---

## 段落的设计要点

我们不仅要考虑段落本身的样式，还要考虑段落在其他元素中的表现，以及段落中出现其他样式的表现。比如，`<sub>`/`<sup>` 对行高会有影响。

### 行高与字体

行高与字体与其他元素保持一致。

### margin

有三种方法：

1. 上下一致
2. 上窄下宽
3. 上为0，下不为0

如果只是考虑不同段落之间的 margin，则这三种的效果是一样的。但如果考虑上其他元素的话，我认为上窄下宽比较好，上面的 margin 作为保险，避免其他元素（比如一些自定义元素）靠太近。

下 margin 建议取 1-1.5 之间，上 margin 建议取 0.5-1 之间。

<div x-data="{margin_top: '0.5em', margin_bottom: '1.5em'}" class="test-box">
    <p>上边距：<input type="text" x-model="margin_top"></input></p>
    <p>下边距：<input type="text" x-model="margin_bottom"></input></p>
    <p :style="{'margin-top': margin_top, 'margin-bottom': margin_bottom}">硕训损铲宏厄。汁克拔踩？态零沥足？</p>
    <p x-bind:style="{'margin-top': margin_top, 'margin-bottom': margin_bottom}">隔派队功丧笋驴遵纵洒定称愿侦蜜毁做只妻论直尝呆沈畦龚烫庇登枚贷屁仇溜遇功外腾晕纪巍嗓吗科茎我俗廉辨赛调蝇喉罩峰电确烤绍稼壤雌埂貌六农腾筛先…滥簧磨坝景，构软势撇评虚闸忌堪贪纯瓣扑勿鲤窗咂镗洪叠仅呵磅灵复兼混厌佣棘羔告俊若态义治等垦追您墨币优伪界听界儒冬滑枚阶战家编。 </p>
    <p :style="{'margin-top': margin_top, 'margin-bottom': margin_bottom}">薄卢培靠逮脾摇篷崩述隧晾款掠栓都向寺审波绪尾哇避更橡临沛、健啦欲嵌栏驾回儡骑护笑串酰锌薯干笑肌煞匀弟魏臂沥夺共憎景耗午蛭洛翅狱畸来猾庇躺坪腋澜坏道坝躯腋护。哑基避屑韶周肖仙卷使究黔跟绒冯锥筹送巢…暗落史浴珠工搅术除根蝇使盖派咱霍吕轰遗棱乞粮虹景挡肩览遥。哼，飘掠沫脾毁颗廊歌澳涕闭域锭价飞铃师。自锹舆苍颂例诚芽沛窍傻陪抖陕拉葡淤统班傻配拆泪貌介绥吕蝈捣咱着波链帝哟厦暖见字黎惧哈剩芍你弃泥糖爷仅茵稀叭尚检踩百垃林约哩蛀佩，鲁植苞种驶惊父痛橙！ </p>
    <p :style="{'margin-top': margin_top, 'margin-bottom': margin_bottom}">忌蜜符椅东耻椭究训小劝澄缚太阀聊缘资勿萘屁灭忌埃潜付、驾押哥程垛改呀妹宿饶哼汗热卓设介奈架败逮淬螟锣钼违授描漏背碳俺字傅页齐熏终说革肛泵附仕扬溉炼盏展肆柄猪遭股稼挖烫岸慎神孵孜苞雌稀问条亚尽、疆赤臭葬巾井籽巷，萤、天荆捆造浦偏洁农扣潜萌盘抽沈。笨薄帘氏，畔铃！</p>
</div>

另外要注意我们设置 margin 时最好用 `margin-block-start`/`margin-block-end`，而不是 `margin-top`/`margin-bottom`，以适应不同 `writing-mode`（从上到下、从右到左etc） 的需求。

