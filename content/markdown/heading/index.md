---
title: 标题的设计
---

## 标题的设计原则

标题是用来给文章划分层级的，标题与段落、不同层级的标题应该有区分度。读者应该可以从标题的样式中判断出其的层级。

## 标题的设计要点

### 标题的字号

[排版干货 字号大小与设计比率之美](https://www.shejidaren.com/zihao-daxiao-sheji-bilv.html) 一文中提到，可以通过比例来确定的字号。

<img src="images/font%20scale.jpg" width="100%">

大比例显得活泼，小比例则显得安静，据此我们可以根据内容确定比例，再计算出具体字号。除了上图中的比例，还有黄金比例，甚至音乐中的音阶也算比例（具体请去看原文）。

比如以 14px 为基础，反复乘以 1.125（即 9/8，根据音乐中的“大二度”确定），得到一组字号：

<div x-data="{base_size: 14, scale: 1.125, weight: 500, margin: '0.67em 0'}">
    <p>基础字号：<input type="number" x-model="base_size"></input></p>
    <p>比例因子：<input type="number" x-model="scale"></input></p>
    <p>字重 font-weight：<input type="number" x-model="weight"></input></p>
    <p>边距 margin：<input type="text" x-model="margin"></input></p>
    <template x-for="size in [9,8,7,6,5,4,3,2,1,0]">
        <h1 x-data="{ font_size: (base_size*(scale**size)).toFixed(0) }"
        :style="{'font-size': (base_size*(scale**size)).toFixed(0)+'px', 'margin': margin, 'font-weight': weight}"
        x-text="(base_size*(scale**size)).toFixed(0)+'号字体 '+size"></h1>
    </template>
</div>

这实际上是 [Material Design 3](https://m3.material.io/styles/typography/type-scale-tokens) 所采用的字号。你也可以尝试自行修改基础字号和缩放因子，设计一组自己的字号。

注意的是我们这里将不同级的标题放在一起，所以对比很明显。但是在文章中，标题之间通常隔着大段的文字，比如考虑下面这个测试用例，第一个标题的字号为 28px，第二个标题的字号为 25px，间隔了文字后两者的区别并不明显，至少不如紧挨时明显。

<style>
    .test-heading-size h2 {
        font-size: 28px;
        line-height: 1.5em;
    }
    .test-heading-size h3 {
        font-size: 25px;
        line-height: 1.5em;
    }
</style>

<div class="test-box test-heading-size">
    <p>硕训损铲宏厄。汁克拔踩？态零沥足？</p>
    <h2>标题</h2>
    <p>隔派队功丧笋驴遵纵洒定称愿侦蜜毁做只妻论直尝呆沈畦龚烫庇登枚贷屁仇溜遇功外腾晕纪巍嗓吗科茎我俗廉辨赛调蝇喉罩峰电确烤绍稼壤雌埂貌六农腾筛先…滥簧磨坝景，构软势撇评虚闸忌堪贪纯瓣扑勿鲤窗咂镗洪叠仅呵磅灵复兼混厌佣棘羔告俊若态义治等垦追您墨币优伪界听界儒冬滑枚阶战家编。 </p>
    <p>薄卢培靠逮脾摇篷崩述隧晾款掠栓都向寺审波绪尾哇避更橡临沛、健啦欲嵌栏驾回儡骑护笑串酰锌薯干笑肌煞匀弟魏臂沥夺共憎景耗午蛭洛翅狱畸来猾庇躺坪腋澜坏道坝躯腋护。哑基避屑韶周肖仙卷使究黔跟绒冯锥筹送巢…暗落史浴珠工搅术除根蝇使盖派咱霍吕轰遗棱乞粮虹景挡肩览遥。哼，飘掠沫脾毁颗廊歌澳涕闭域锭价飞铃师。自锹舆苍颂例诚芽沛窍傻陪抖陕拉葡淤统班傻配拆泪貌介绥吕蝈捣咱着波链帝哟厦暖见字黎惧哈剩芍你弃泥糖爷仅茵稀叭尚检踩百垃林约哩蛀佩，鲁植苞种驶惊父痛橙！ </p>
    <p>忌蜜符椅东耻椭究训小劝澄缚太阀聊缘资勿萘屁灭忌埃潜付、驾押哥程垛改呀妹宿饶哼汗热卓设介奈架败逮淬螟锣钼违授描漏背碳俺字傅页齐熏终说革肛泵附仕扬溉炼盏展肆柄猪遭股稼挖烫岸慎神孵孜苞雌稀问条亚尽、疆赤臭葬巾井籽巷，萤、天荆捆造浦偏洁农扣潜萌盘抽沈。笨薄帘氏，畔铃！</p>
    <h3>标题</h3>
</div>

一种解决方法是加大比例因子，但这样就意味着最大的 `<h1>` 标题会很大。我们希望最大的标题字号在 30~40px 之间。另一种方法是用其他东西来区分，比如字重或其他装饰。

### 标题的字重

一般段落的字重为 400，标题可以调整为 600~800.

### 其他装饰

为了让标题更明显，我们可以额外添加一些装饰，比如像 Markdown 一样在前面加 `#`

<style>
    .test-heading-hash h2::before {
        content: '##';
    }
    .test-heading-hash h3::before {
        content: '###';
    }
    .test-heading-hash h2::before,
    .test-heading-hash h3::before {
        letter-spacing: -0.05em;
        color: gray;
        margin: 0 10px 0 0;
    }
</style>

<div class="test-box test-heading-size test-heading-hash">
    <p>硕训损铲宏厄。汁克拔踩？态零沥足？</p>
    <h2>标题</h2>
    <p>隔派队功丧笋驴遵纵洒定称愿侦蜜毁做只妻论直尝呆沈畦龚烫庇登枚贷屁仇溜遇功外腾晕纪巍嗓吗科茎我俗廉辨赛调蝇喉罩峰电确烤绍稼壤雌埂貌六农腾筛先…滥簧磨坝景，构软势撇评虚闸忌堪贪纯瓣扑勿鲤窗咂镗洪叠仅呵磅灵复兼混厌佣棘羔告俊若态义治等垦追您墨币优伪界听界儒冬滑枚阶战家编。 </p>
    <p>薄卢培靠逮脾摇篷崩述隧晾款掠栓都向寺审波绪尾哇避更橡临沛、健啦欲嵌栏驾回儡骑护笑串酰锌薯干笑肌煞匀弟魏臂沥夺共憎景耗午蛭洛翅狱畸来猾庇躺坪腋澜坏道坝躯腋护。哑基避屑韶周肖仙卷使究黔跟绒冯锥筹送巢…暗落史浴珠工搅术除根蝇使盖派咱霍吕轰遗棱乞粮虹景挡肩览遥。哼，飘掠沫脾毁颗廊歌澳涕闭域锭价飞铃师。自锹舆苍颂例诚芽沛窍傻陪抖陕拉葡淤统班傻配拆泪貌介绥吕蝈捣咱着波链帝哟厦暖见字黎惧哈剩芍你弃泥糖爷仅茵稀叭尚检踩百垃林约哩蛀佩，鲁植苞种驶惊父痛橙！ </p>
    <p>忌蜜符椅东耻椭究训小劝澄缚太阀聊缘资勿萘屁灭忌埃潜付、驾押哥程垛改呀妹宿饶哼汗热卓设介奈架败逮淬螟锣钼违授描漏背碳俺字傅页齐熏终说革肛泵附仕扬溉炼盏展肆柄猪遭股稼挖烫岸慎神孵孜苞雌稀问条亚尽、疆赤臭葬巾井籽巷，萤、天荆捆造浦偏洁农扣潜萌盘抽沈。笨薄帘氏，畔铃！</p>
    <h3>标题</h3>
</div>

或者直接编号（参考 [stackoverflow](https://stackoverflow.com/questions/38157007/how-do-i-achieve-automatic-numbering-for-headings-using-css)）：

<style>
    .test-heading-number {
        counter-reset: heading;
    }
    .test-heading-number h2::before {
        content: counter(heading)") ";
        counter-increment: heading;
    }
    .test-heading-number h2 {
        counter-reset: subheading;
    }
    .test-heading-number h3::before {
        content: counter(heading)"." counter(subheading)") ";
        counter-increment: subheading;
    }
</style>

<div class="test-box test-heading-size test-heading-number">
    <p>硕训损铲宏厄。汁克拔踩？态零沥足？</p>
    <h2>标题</h2>
    <p>隔派队功丧笋驴遵纵洒定称愿侦蜜毁做只妻论直尝呆沈畦龚烫庇登枚贷屁仇溜遇功外腾晕纪巍嗓吗科茎我俗廉辨赛调蝇喉罩峰电确烤绍稼壤雌埂貌六农腾筛先…滥簧磨坝景，构软势撇评虚闸忌堪贪纯瓣扑勿鲤窗咂镗洪叠仅呵磅灵复兼混厌佣棘羔告俊若态义治等垦追您墨币优伪界听界儒冬滑枚阶战家编。 </p>
    <p>薄卢培靠逮脾摇篷崩述隧晾款掠栓都向寺审波绪尾哇避更橡临沛、健啦欲嵌栏驾回儡骑护笑串酰锌薯干笑肌煞匀弟魏臂沥夺共憎景耗午蛭洛翅狱畸来猾庇躺坪腋澜坏道坝躯腋护。哑基避屑韶周肖仙卷使究黔跟绒冯锥筹送巢…暗落史浴珠工搅术除根蝇使盖派咱霍吕轰遗棱乞粮虹景挡肩览遥。哼，飘掠沫脾毁颗廊歌澳涕闭域锭价飞铃师。自锹舆苍颂例诚芽沛窍傻陪抖陕拉葡淤统班傻配拆泪貌介绥吕蝈捣咱着波链帝哟厦暖见字黎惧哈剩芍你弃泥糖爷仅茵稀叭尚检踩百垃林约哩蛀佩，鲁植苞种驶惊父痛橙！ </p>
    <p>忌蜜符椅东耻椭究训小劝澄缚太阀聊缘资勿萘屁灭忌埃潜付、驾押哥程垛改呀妹宿饶哼汗热卓设介奈架败逮淬螟锣钼违授描漏背碳俺字傅页齐熏终说革肛泵附仕扬溉炼盏展肆柄猪遭股稼挖烫岸慎神孵孜苞雌稀问条亚尽、疆赤臭葬巾井籽巷，萤、天荆捆造浦偏洁农扣潜萌盘抽沈。笨薄帘氏，畔铃！</p>
    <h3>标题</h3>
</div>

### Margin

如果只想希望上下有一定空白，直接设置 `margin: 0.67em 0;` 即可。但更好的排版是上面的空白比下面的空白大，这样标题与下面的内容的关系更加密切。

<style>
    .test-heading-margin h2,
    .test-heading-margin h3 {
        margin-block-start: 1em;
        margin-block-end: 0.5em;
    }
</style>

<div class="test-box test-heading-size test-heading-margin">
    <p>硕训损铲宏厄。汁克拔踩？态零沥足？</p>
    <h2>标题</h2>
    <p>隔派队功丧笋驴遵纵洒定称愿侦蜜毁做只妻论直尝呆沈畦龚烫庇登枚贷屁仇溜遇功外腾晕纪巍嗓吗科茎我俗廉辨赛调蝇喉罩峰电确烤绍稼壤雌埂貌六农腾筛先…滥簧磨坝景，构软势撇评虚闸忌堪贪纯瓣扑勿鲤窗咂镗洪叠仅呵磅灵复兼混厌佣棘羔告俊若态义治等垦追您墨币优伪界听界儒冬滑枚阶战家编。 </p>
    <p>薄卢培靠逮脾摇篷崩述隧晾款掠栓都向寺审波绪尾哇避更橡临沛、健啦欲嵌栏驾回儡骑护笑串酰锌薯干笑肌煞匀弟魏臂沥夺共憎景耗午蛭洛翅狱畸来猾庇躺坪腋澜坏道坝躯腋护。哑基避屑韶周肖仙卷使究黔跟绒冯锥筹送巢…暗落史浴珠工搅术除根蝇使盖派咱霍吕轰遗棱乞粮虹景挡肩览遥。哼，飘掠沫脾毁颗廊歌澳涕闭域锭价飞铃师。自锹舆苍颂例诚芽沛窍傻陪抖陕拉葡淤统班傻配拆泪貌介绥吕蝈捣咱着波链帝哟厦暖见字黎惧哈剩芍你弃泥糖爷仅茵稀叭尚检踩百垃林约哩蛀佩，鲁植苞种驶惊父痛橙！ </p>
    <p>忌蜜符椅东耻椭究训小劝澄缚太阀聊缘资勿萘屁灭忌埃潜付、驾押哥程垛改呀妹宿饶哼汗热卓设介奈架败逮淬螟锣钼违授描漏背碳俺字傅页齐熏终说革肛泵附仕扬溉炼盏展肆柄猪遭股稼挖烫岸慎神孵孜苞雌稀问条亚尽、疆赤臭葬巾井籽巷，萤、天荆捆造浦偏洁农扣潜萌盘抽沈。笨薄帘氏，畔铃！</p>
    <h3>标题</h3>
</div>

但需要注意，如果相邻层级的标题紧挨在一起，比如一个 28px 的标题，它后面跟着一个 25px 的标题，它们上下 margin 设为 1em、0.5em，这两者间的 margin 就会变成 25px，就会显得很松散，所以我们需要对这种情况进行处理，减小上边距。

<style>
    .test-heading-margin-improve h2+h3{
        margin-block-start: 0.5em;
    }
</style>

<div class="test-box test-heading-size" style="display:flex;gap:10px;">
    <div class="test-heading-margin">
        <h2>标题</h2>
        <h3>标题</h3>
    </div>
    <div class="test-heading-margin test-heading-margin-improve">
        <h2>标题</h2>
        <h3>标题</h3>
    </div>
</div>

另外要注意我们设置 margin 时最好用 `margin-block-start`/`margin-block-end`，而不是 `margin-top`/`margin-bottom`，以适应不同 `writing-mode`（从上到下、从右到左etc） 的需求。

### letter-spacing

为了美观，可以适当加大字距。
