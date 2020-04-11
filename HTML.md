## 1、自定义标签属性使用方法（data-*）

```
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <title>Title</title>
</head>
<body>
<script>
    onload = function (ev) {
        var img = document.getElementsByTagName('img')[0];
        img.setAttribute('src',img.getAttribute('data-src'))
    }
</script>
<img src="img/IMG_8808.JPG" data-src="img/IMG_8806.JPG" alt="">
<img src="img/IMG_8808.JPG" data-src="img/IMG_8681.JPG" alt="">
</body>
<script src="https://cdn.bootcss.com/jquery/3.3.1/jquery.js"></script>
<script>
    $('img').each(
        function(){
            $(this).attr('src',$(this).attr('data-src'));

        })
</script>
</html>

```

## 2、HTML meta标签总结与属性使用介绍

### 2.1 简介

中文w3school说的是元信息，Google和百度都没有相关的词条。但元数据在Google就有详细解释。所以这儿采用英文版W3school的解释。

> The <meta> tag provides metadata about the HTML document. Metadata will not be displayed on the page, but will be machine parsable.

不难看出，其中的关键是metadata，中文名叫元数据，是用于描述数据的数据。它不会显示在页面上，但是机器却可以识别。这么一来meta标签的作用方式就很好理解了。

### 2.2 用处

> Meta elements are typically used to specify page description, keywords, author of the document, last modified, and other metadata.

The metadata can be used by browsers (how to display content or reload page), search engines (keywords), or other web services

这句话对meta标签用处的介绍，简洁明了。
翻译过来就是：meta常用于定义页面的说明，关键字，最后修改日期，和其它的元数据。这些元数据将服务于浏览器（如何布局或重载页面），搜索引擎和其它网络服务。

### 2.3 组成

meta标签共有两个属性，分别是http-equiv属性和name属性。

### 2.3.1 name属性

name属性主要用于描述网页，比如网页的关键词，叙述等。与之对应的属性值为content，content中的内容是对name填入类型的具体描述，便于搜索引擎抓取。
meta标签中name属性语法格式是：

```
<meta name="参数" content="具体的描述">。
```

其中name属性共有以下几种参数。**(A-C为常用属性)**

#### A. keywords(关键字)

说明：用于告诉搜索引擎，你网页的关键字。
举例：

```
<meta name="keywords" content="Lxxyx,博客，文科生，前端">
```

#### B. description(网站内容的描述)

说明：用于告诉搜索引擎，你网站的主要内容。
举例：

```
<meta name="description" content="文科生，热爱前端与编程。目前大二，这是我的前端博客">
```

#### C. viewport(移动端的窗口)

说明：这个概念较为复杂，具体的会在下篇博文中讲述。
这个属性常用于设计移动端网页。在用bootstrap,AmazeUI等框架时候都有用过viewport。

举例（常用范例）：

```
<meta name="viewport" content="width=device-width, initial-scale=1">
```

#### D. robots(定义搜索引擎爬虫的索引方式)

说明：robots用来告诉爬虫哪些页面需要索引，哪些页面不需要索引。
content的参数有all,none,index,noindex,follow,nofollow。默认是all。

举例：

```
<meta name="robots" content="none">
```

具体参数如下：

1.none : 搜索引擎将忽略此网页，等价于noindex，nofollow。
2.noindex : 搜索引擎不索引此网页。
3.nofollow: 搜索引擎不继续通过此网页的链接索引搜索其它的网页。
4.all : 搜索引擎将索引此网页与继续通过此网页的链接索引，等价于index，follow。
5.index : 搜索引擎索引此网页。
6.follow : 搜索引擎继续通过此网页的链接索引搜索其它的网页。

#### E. author(作者)

说明：用于标注网页作者
举例：

```
<meta name="author" content="Lxxyx,841380530@qq.com">
```

#### F. generator(网页制作软件)

说明：用于标明网页是什么软件做的
举例: (不知道能不能这样写)：

```
<meta name="generator" content="Sublime Text3">
```

#### G. copyright(版权)

说明：用于标注版权信息
举例：

```
<meta name="copyright" content="Lxxyx"> //代表该网站为Lxxyx个人版权所有。
```

#### H. revisit-after(搜索引擎爬虫重访时间)

说明：如果页面不是经常更新，为了减轻搜索引擎爬虫对服务器带来的压力，可以设置一个爬虫的重访时间。如果重访时间过短，爬虫将按它们定义的默认时间来访问。
举例：

```
<meta name="revisit-after" content="7 days" >
```

#### I. renderer(双核浏览器渲染方式)

说明：renderer是为双核浏览器准备的，用于指定双核浏览器默认以何种方式渲染页面。比如说360浏览器。
举例：

```
<meta name="renderer" content="webkit"> //默认webkit内核
<meta name="renderer" content="ie-comp"> //默认IE兼容模式
<meta name="renderer" content="ie-stand"> //默认IE标准模式
```

### 2.3.2 http-equiv属性

　　介绍之前，先说个小插曲。看文档和博客关于http-equiv的介绍时，有这么一句。

> http-equiv顾名思义，相当于http的文件头作用。

　　一开始看到这句话的时候，我是迷糊的。因为我看各类技术名词，都会习惯性的去记住它的英文全称。equiv的全称是"equivalent"，意思是相等，相当于。然后我脑子里出现了大大的迷惑：“HTTP相等？”

　　后来还准备去Segmentfault提问来着。结果在写问题的时候，突然反应出equivalent还有相当于的意思。意思就是相当于http的作用。至于文件头是哪儿出来的，估计是从其作用来分析的。我认为顾名思义并不能得出"相当于http的文件头作用"这个论断。

　　这个我所认为的http-equiv意思的简介。
　　`相当于HTTP的作用，比如说定义些HTTP参数啥的。`

　　meta标签中http-equiv属性语法格式是：

```
<meta http-equiv="参数" content="具体的描述">
```

　　其中http-equiv属性主要有以下几种参数：

#### A. content-Type(设定网页字符集)(推荐使用HTML5的方式)

　　说明：用于设定网页字符集，便于浏览器解析与渲染页面
　　举例：

```
<meta http-equiv="content-Type" content="text/html;charset=utf-8">  //旧的HTML，不推荐

<meta charset="utf-8"> //HTML5设定网页字符集的方式，推荐使用UTF-8
```

#### B. X-UA-Compatible(浏览器采取何种版本渲染当前页面)

　　说明：用于告知浏览器以何种版本来渲染页面。（一般都设置为最新模式，在各大框架中这个设置也很常见。）
　　举例：

```
<meta http-equiv="X-UA-Compatible" content="IE=edge,chrome=1"/> //指定IE和Chrome使用最新版本渲染当前页面
```

#### C. cache-control(指定请求和响应遵循的缓存机制)

###### 用法1.

　　说明：指导浏览器如何缓存某个响应以及缓存多长时间。这一段内容我在网上找了很久，但都没有找到满意的。
　　最后终于在Google Developers中发现了我想要的答案。

> ![cache简介](http://7xoxxe.com1.z0.glb.clouddn.com/cache.png)

举例:

```
<meta http-equiv="cache-control" content="no-cache">
```

　　共有以下几种用法：

1. no-cache: 先发送请求，与服务器确认该资源是否被更改，如果未被更改，则使用缓存。
2. no-store: 不允许缓存，每次都要去服务器上，下载完整的响应。（安全措施）
3. public : 缓存所有响应，但并非必须。因为max-age也可以做到相同效果
4. private : 只为单个用户缓存，因此不允许任何中继进行缓存。（比如说CDN就不允许缓存private的响应）
5. maxage : 表示当前请求开始，该响应在多久内能被缓存和重用，而不去服务器重新请求。例如：max-age=60表示响应可以再缓存和重用 60 秒。

> [参考链接：HTTP缓存](https://developers.google.com/web/fundamentals/performance/optimizing-content-efficiency/http-caching?hl=zh-cn#cache-control)

###### 用法2.(禁止百度自动转码)

　　说明：用于禁止当前页面在移动端浏览时，被百度自动转码。虽然百度的本意是好的，但是转码效果很多时候却不尽人意。所以可以在head中加入例子中的那句话，就可以避免百度自动转码了。
　　举例：

```
<meta http-equiv="Cache-Control" content="no-siteapp" />
```

#### D. expires(网页到期时间)

　　说明:用于设定网页的到期时间，过期后网页必须到服务器上重新传输。
　　举例：

```
<meta http-equiv="expires" content="Sunday 26 October 2016 01:00 GMT" />
```

#### E. refresh(自动刷新并指向某页面)

　　说明：网页将在设定的时间内，自动刷新并调向设定的网址。
　　举例:

```
<meta http-equiv="refresh" content="2；URL=http://www.lxxyx.win/"> //意思是2秒后跳转向我的博客
```

#### F. Set-Cookie(cookie设定)

　　说明：如果网页过期。那么这个网页存在本地的cookies也会被自动删除。

```
<meta http-equiv="Set-Cookie" content="name, date"> //格式

<meta http-equiv="Set-Cookie" content="User=Lxxyx; path=/; expires=Sunday, 10-Jan-16 10:00:00 GMT"> //具体范例
```

**代码一**：`<meta name="renderer" content="webkit|ie-comp|ie-stand">`

　　如果说小标题的meta 标签你不懂，那么下面几个你该有点印象吧：

```
<meta http-equiv="X-UA-Compatible" content="IE=Edge,chrome=1" >
<meta http-equiv="X-UA-Compatible" content="edge" />12
```

　　对，就是说强制使用chrome 内核浏览或者IE最高版本浏览的代码，但这不是本文要讨论的内容，提及只是为了过渡下，请再看小标题：

```
<meta name="renderer" content="webkit|ie-comp|ie-stand">1
```

　　其实这个是360 提出来的“浏览器内核控制Meta标签”（对，是360，不要看到这个数字就反感，但Jeff 觉得在这一点上，360 厚道多了）。参考360 官方文档的说明，你就知道这个meta 标签的作用是为了照顾国内众多“双核浏览器”的用户，你在网页使用这段代码，如设置为`<meta name="renderer" content="webkit">` ，则会强制使用webkit 内核进行渲染。

　　总得来说，我认为这是好事，毕竟添加这个meta标签不是很费事效果却不错，“狠狠”地照顾了国内的小白用户。Jeff 在最新开发的Mindia主题上已经添加了这个代码了，写到这里，我又突然想起国内某狗浏览器对我以前某个按HTML5 标准写的网站居然默认是采用IE 内核渲染的所谓“智能”。

**代码二**：`<meta http-equiv="Cache-Control" content="no-siteapp" />`

也是一段meta 标签，N久以前，这段meta是这样的，

```
<meta http-equiv="Cache-Control" content="no-transform " />1
```

　　这个meta 标签是禁止百度转码的，在大概一两年前，移动互联网飞起，当时很多网站都没有多移动端进行适配，国内的“百毒”公司就率先考虑到“用户体验”，本着“为人民币服务”的原则，在移动端通过百度搜索过来的网页会默认进行转码。

　　从搜索引擎用户角度，这看起来“哟，还不错欧”，毕竟上网流量要钱嘛；从站长角度看，也还可以嘛，毕竟不是所有站长都有能力做移动端适配的，李彦宏帮大家想到了不错，还不用站长动一手一脚，你看多好！　　

　　一个公司之所以让人恶心，常常不是因为本身干的事情足够恶心，而是表面上干着好事背地里龌蹉行为让人恶心。

　　墙裂建议每位搞前端开发的都添加上这个代码，不要再给李首富捐钱了。

**代码三**：`<a href="http://www.miitbeian.gov.cn" rel="nofollow" rel="nofollow" target="_blank">X ICP备xxxxx号.</a>`

　　这个就不多说了，毕竟咱网站下边就挂着这个，虽然是被某部门要求挂上的。对于这些事情，我们要用平常心对待，毕竟挂上这个对于我们这些小网站也不是太碍眼，你看人家某浪的网页下面：

　　不过要注意一点，你一定要在a 链接这里添加这个 rel=”nofollow”，为什么捏，看这篇文章你就知道了《中国唯一一个PR10的网站》。

妥协，也是最小的妥协。

**代码四**：`<meta name="applicable-device" content="pc,mobile">` 
　　自适应就是使用相同的网址不考虑用户浏览器UA，向不同设备的用户提供同一套html代码。

　　自适应也叫响应式，可以自动识别屏幕宽度并作出相应调整设计。

　　在`<head>`中标识`<meta name="applicable-device"content="pc,mobile">`，并使用`<picture>`元素处理自适应图片，即可成功自适应。

`<meta name="viewport" content="width=device-width, initial-scale=1.0">`作用是设置显示宽度和手机屏幕宽度一样，也就是满屏显示。

**代码五**:`<meta name="MobileOptimized" content="width"/>`

```
<meta name="viewport" content="width=device-width, initial-scale=1, user-scalable=no, minimal-ui" /> 
12
```

width: viewport 的宽度 （范围从 200 到 10,000 ，默认为 980 像素 ）

height: viewport 的高度 （范围从 223 到 10,000 ）

initial-scale: 初始的缩放比例 （范围从>0到 10 ）

minimum-scale: 允许用户缩放到的最小比例

maximum-scale: 允许用户缩放到的最大比例

user-scalable: 用户是否可以手动缩放

下面是我们经常用到的一些标签，由于浏览器的差异，并不能百分百兼容。

```
<!-- 是否删除默认的苹果工具栏和菜单栏 -->
<meta name="apple-mobile-web-app-capable" content="yes" />

<!-- 其他的meta设置 -->
<!-- 启用360浏览器的极速模式(webkit) -->
<meta name="renderer" content="webkit">

<!-- 避免IE使用兼容模式 -->
<meta http-equiv="X-UA-Compatible" content="IE=edge">

<!-- 针对手持设备优化，主要是针对一些老的不识别viewport的浏览器，比如黑莓 -->
<meta name="HandheldFriendly" content="true">

<!-- 微软的老式浏览器 -->
<meta name="MobileOptimized" content="320">

<!-- uc强制竖屏 -->
<meta name="screen-orientation" content="portrait">

<!-- QQ强制竖屏 -->
<meta name="x5-orientation" content="portrait">

<!-- UC强制全屏 -->
<meta name="full-screen" content="yes">

<!-- QQ强制全屏 -->
<meta name="x5-fullscreen" content="true">

<!-- UC应用模式 -->
<meta name="browsermode" content="application">

<!-- QQ应用模式 -->
<meta name="x5-page-mode" content="app">

<!-- windows phone 点击无高光 -->
<meta name="msapplication-tap-highlight" content="no">123456789101112131415161718192021222324252627282930313233343536
```

　　此外，apple还有两个有趣的标签： 
　　**1.apple-touch-icon** 
`< link rel= "apple-touch-icon" sizes= "76x76" href= "touch-icon-ipad.png">`

　　如果 apple-mobile-web-app-capable 设置为 yes 了，那么在苹果机的safari上可以通过添加到主屏按钮将网站添加到主屏幕上。而设置相应 apple-touch-icon 标签，则添加到主屏上的图标就会使用我们指定的图片。

　　**2.apple-touch-startup-image** 
`< link rel= "apple-touch-startup-image" href= "/startup.png">` 
　　基于 apple-mobile-web-app-capable 设置为 yes ，可以为WebApp设置一个类似NativeApp的启动画面。和 apple-touch-icon 不同， apple-mobile-web-app-capable 不支持sizes属性，要使用media来加载不同的启动画面。详细查询 大漠的文章 。

```
// iPhone
<link href="apple-touch-startup-image-320x460.png" media="(device-width: 320px)" rel="apple-touch-startup-image" />

// iPhone Retina
<link href="apple-touch-startup-image-640x920.png" media="(device-width: 320px) and (-webkit-device-pixel-ratio: 2)" rel="apple-touch-startup-image" />
123456
```

### 3、html中a标签href='#'与href='###'的区别分享

　　首先，<a> 标签 + onclick='{jscode}' 是很常用的一种 js 运用方式，而不使用 href='javascript:{jscode}' 是为了兼容多种浏览器对 <a> 标签的解释和处理不同。其次，使用 <a> 标签 + onclick='{jscode}' 时经常会加一个 href='###'，而有时这个 href='###' 会被误写为 <a href='#'> 是因为使用者没有理解 '#' 和 '###' 的区别。

　　简单地说，就是说如果想定义一个空的链接，又不跳转到页面头部，可以写href="###"。详细解释就是'#' 是有特定意义的，如果 '#' 后有内容会被认为是一个标签而从页面找到相应标签跳转到该处，找不到时会跳到页首， '###' 其实就是一个无意义的标签指定，也就是一个 '#' 和不存在的标签 '##' 的组合，页面中找不到命名为 '##' 的 <a> 时该链接就不会发生跳转，也就不会导致执行 onclick 中的内容时突然发生页面跳到页首的问题。'###' 只是一种使用者习惯，如果你愿意，可以随便找一个跳转不到的标签作为命名。说白了"###" 就是一个不是锚点的字符串，浏览器找不到也不会跳到页首，原理就是依赖了网页的报错机制，找不到就不做处理。

　　有些人说，不喜欢“###”因为他会改变链接。都是使用一直用javascript:void(0)或者javascript:。href="javascript:void(0);"但也有人说用href="javascript:void(0);"可能会有浏览器兼容问题。在做页面时，如果想做一个链接点击后不做任何事情，或者响应点击而完成其他事情，可以设置其属性 href = "#"，但是，这样会有一个问题，就是当页面有滚动条时，点击后会返回到页面顶端，用户体验不好。

　　javascript:void(0)这种伪协议，少写的好，如果你看过一些web标准的书就知道为什么了。 链接（href）直接使用javascript:void(0)在IE中可能会引起一些问题，比如：造成gif动画停止播放等，所以，最安全的办法还是使用“####”。为防止点击链接后跳转到页首，onclick事件return false即可。

### 4、腾讯alloyteam团队前端代码规范

```
http://alloyteam.github.io/CodeGuide
```

### 5、网站性能优化

#### 一、网站结构的优化

1、代码结构：精简

对于搜索引擎来说，爬取的都是网站的代码，所以代码结构越精简，蜘蛛爬取就越高效，怎样精简代码?CSS与JS进行封装调用，不要写进源代码中。另外网站尽量少使用JS，采用DIV+CSS结构。不过现在广州网站优化的企业建站在代码精简上已经做得很好了。

2、网址结构：url静态化

url静态化到底对seo有多重要呢?其实根据之前的一些研究表明，静态化与动态url并没有明显的优势，一般来说，其实两者差不多，但如果动态网址是http：//www.这样子的话，用户体验就很不好了，所以url静态化是最好的选择。

3、目录逻辑结构：三级目录

一般来说，建议网站的目录层次不超过3级，之前众多经验是采用树状结构，也就是首页——目录——文章这样子的结构。网站优化需要注意的地方：

1）网站优化核心关键词很重要，优化网站的时候不要只优化一个关键词，可以先优化好一到二个关键词，优化好之后再进行多一个关键词的优化，做到优化的目的。

2）优化的网站不要出现死链，死链是网站的大敌，所以在优化网站的时候一定要防止死链接。

3）网速的重要性，网站首页不需要加大量的动态展示，如效果音乐、动画等等，这些都会影响网速，用户体验也不好，所以在建设网站同时，也要考虑到网站的速度与质量。

#### 二、网站性能优化

https://www.cnblogs.com/puyongsong/p/5968935.html

##### 1、尽量减少HTTP请求次数

终端用户响应的时间中，有80%用于下载各项内容，这部分时间包括下载页面中的图像、样式表、脚本、Flash等。通过减少页面中的元素可以减少HTTP请求的次数，这是提高网页速度的关键步骤。

减少页面组件的方法其实就是简化页面设计。那么有没有一种方法既能保持页面内容的丰富性又能达到加快响应时间的目的呢？这里有几条减少HTTP请求次数同时又可能保持页面内容丰富的技术。

1、合并文件：合并文件是通过把所有的脚本放到一个文件中来减少HTTP请求的方法，例如可以简单地把所有的CSS文件都放入一个样式表中。当脚本 或者样式表在不同页面中使用时需要做不同的修改，这可能会相对比较麻烦，但即便如此也要把这个方法作为改善页面性能的重要一步；

2、CSS Sprites：CSS Sprites是减少图像请求的有效方法。把所有的背景图像都放到一个图片文件中，然后通过CSS的background-image和background-position属性来显示图片的不同部分;

3、图片地图：图片地图是把多张图片整合到一张图片中。虽然文件的总体大小不会改变，但是可以减少HTTP请求次数。图片地图只有在图片的所有组成 部分在页面中是紧挨在 一起的时候才能使用，如导航栏。确定图片的坐标和可能会比较繁琐且容易出错，同时使用图片地图导航也不具有可读性，因此不推荐这种方法；

4、内联图像：内联图像是使用data:URL scheme的方法把图像数据加载页面中，这可能会增加页面的大小。把内联图像放到样式表（可缓存）中可以减少HTTP请求同时又避免增加页面文件的大小，但是内联图像现在还没有得到主流浏览器的支持。

减少页面的HTTP请求次数是你优化网站性能首先要做的一步，这是改进首次访问用户等待时间的最重要的方法。如同Tenni Theurer的博文《Browser Cahe Usage – Exposed》中所说，HTTP请求在无缓存情况下占去了40%到60%的响应时间。改善HTTP请求，让那些初次访问你网站的人获得更加快速的体验 吧！

##### 2、减少DNS查找次数

域名系统（DNS）提供了域名和IP的对应关系，就像电话本中人名和他们的电话号码的关系一样。当你在浏览器地址栏中输入 www.52maomao.info时，DNS解析服务器就会返回这个域名对应的IP地址。DNS解析的过程同样也是需要时间的，一般情况下返回给定域名 对应的IP地址会花费20到120毫秒的时间，而且在这个过程中浏览器什么都不会做直到DNS查找完毕。

缓存DNS查找可以改善页面性能。这种缓存需要一个特定的缓存服务器，这种服务器一般属于用户的ISP提供商或者本地局域网控制，但是它同样会在用 户使用的计算机上产生缓存。DNS信息会保留在操作系统的DNS缓存中（微软Windows系统中DNS Client Service），大多数浏览器有独立于操作系统以外的自己的缓存。由于浏览器有自己的缓存记录，因此在一次请求中它不会受到操作系统的影响。

Internet Explorer默认情况下对DNS查找记录的缓存时间为30分钟，它在注册表中的键值为DnsCacheTimeout。Firefox对DNS的查找 记录缓存时间为1分钟，它在配置文件中的选项为network.dnsCacheExpiration（Fasterfox把这个选项改为了1小时）。

当客户端中的DNS缓存都为空时（浏览器和操作系统都为空），DNS查找的次数和页面中主机名的数量相同，这其中包括页面中URL、图片、脚本文 件、样式表、Flash对象等包含的主机名。减少主机名的数量可以减少DNS查找次数。减少主机名的数量还可以减少页面中并行下载的数量。减少DNS查找 次数可以节省响应时间，但是减少并行下载却会增加响应时间。我的指导原则是把这些页面中的内容分割成至少两部分但不超过四部分，这种结果就是在减少DNS 查找次数和保持较高程度并行下载两者之间的权衡了。

##### 3、避免跳转

跳转是使用301和302代码实现的。下面是一个响应代码为301的HTTP头：

　　　　HTTP/1.1 301 Moved Permanently

　　　　Location: http://52maomao.info/demo

　　　　Content-Type: text/html

浏览器会把用户指向到Location中指定的URL。头文件中的所有信息在一次跳转中都是必需的，内容部分可以为空。不管他们的名称，301和302 响应都不会被缓存，除非增加一个额外的头选项，如Expires或者Cache-Control来指定它缓存。

<meat />元素的刷新标签和JavaScript也可以实现URL的跳转，但是如果你必须要跳转的时候，最好的方法就是使用标准的3XXHTTP状态代 码，这主要是为了确保“后退”按钮可以正确地使用。

但是要记住跳转会降低用户体验。在用户和HTML文档中间增加一个跳转，会拖延页面中所有元素的显示，因为在HTML文件被加载前任何文件（图像、 Flash等）都不会被下载。

有一种经常被网页开发者忽略却往往十分浪费响应时间的跳转现象。这种现象发生在当URL本该有斜杠（/）却被忽略掉时。例如，当我们要访问 http: //astrology.yahoo.com/astrology 时，实际上返回的是一个包含301代码的跳转，它指向的是http://astrology.yahoo.com/astrology/ （注意末尾的斜杠）。在Apache服务器中可以使用Alias 或者 mod_rewrite或者the DirectorySlash来避免。

连接新网站和旧网站是跳转功能经常被用到的另一种情况。这种情况下往往要连接网站的不同内容然后根据用户的不同类型（如浏览器类型、用户账号所属类 型）来进行跳转。使用跳转来实现两个网站的切换十分简单，需要的代码量也不多。尽管使用这种方法对于开发者来说可以降低复杂程度，但是它同样降低用户体 验。

一个可替代方法就是如果两者在同一台服务器上时使用Alias和mod_rewrite和实现。如果是因为域名的不同而采用跳转，那么可以通过使用 Alias或者mod_rewirte建立CNAME（保存一个域名和另外一个域名之间关系的DNS记录）来替代。

##### 4、可缓存的AJAX

Ajax经常被提及的一个好处就是由于其从后台服务器传输信息的异步性而为用户带来的反馈的即时性。但是，使用Ajax并不能保证用户不会在等待异步的JavaScript和XML响应上花费时间。

在很多应用中，用户是否需要等待响应取决于Ajax如何来使用。例如，在一个基于Web的Email客户端中，用户必须等待Ajax返回符合他们条件的邮件查询结果。记住一点，“异步”并不异味着“即时”，这很重要。

为了提高性能，优化Ajax响应是很重要的。提高Ajxa性能的措施中最重要的方法就是使响应具有可缓存性，具体的讨论可以查看《Add an Expires or a Cache-Control Header》。其它的几条规则也同样适用于Ajax：

1、Gizp压缩文件；

2、减少DNS查找次数；

3、精简JavaScript；

4、避免跳转；

5、配置ETags。

让我们来看一个例子：一个Web2.0的Email客户端会使用Ajax来自动完成对用户地址薄的下载。如果用户在上次使用过Email web应用程序后没有对地址薄作任何的修改，而且Ajax响应通过Expire或者Cacke-Control头来实现缓存，那么就可以直接从上一次的缓 存中读取地址薄了。必须告知浏览器是使用缓存中的地址薄还是发送一个新的请求。这可以通过为读取地址薄的Ajax URL增加一个含有上次编辑时间的时间戳来实现，例如，&t=11900241612等。如果地址薄在上次下载后没有被编辑过，时间戳就不变，则 从浏览器的缓存中加载从而减少了一次HTTP请求过程。如果用户修改过地址薄，时间戳就会用来确定新的URL和缓存响应并不匹配，浏览器就会重要请求更新 地址薄。

即使你的Ajxa响应是动态生成的，哪怕它只适用于一个用户，那么它也应该被缓存起来，这样做可以使你的Web2.0应用程序更加快捷。

##### 5、推迟加载内容

你可以仔细看一下你的网页，问问自己“哪些内容是页面呈现时所必需首先加载的？哪些内容和结构可以稍后再加载？

把整个过程按照onload事件分隔成两部分，JavaScript是一个理想的选择。例如，如果你有用于实现拖放和动画的JavaScript， 那么它 就以等待稍后加载，因为页面上的拖放元素是在初始化呈现之后才发生的。其它的例如隐藏部分的内容（用户操作之后才显现的内容）和处于折叠部分的图像也可以 推迟加载

工具可以节省你的工作量：YUI Image Loader可以帮你推迟加载折叠部分的图片，YUI Get utility是包含JS和CSS的便捷方法，比如你可以打开Firebug的Net选项卡看一下Yahoo的首页。

当性能目标和其它网站开发实践一致时就会相得益彰。这种情况下，通过程序提高网站性能的方法告诉我们，在支持JavaScript的情况下，可以先 去除用户体验，不过这要保证你的网站在没有JavaScript也可以正常运行。在确定页面运行正常后，再加载脚本来实现如拖放和动画等更加花哨的效果。

##### 6、预加载

预加载和后加载看起来似乎恰恰相反，但实际上预加载是为了实现另外一种目标。预加载是在浏览器空闲时请求将来可能会用到的页面内容（如图像、样式表和脚本）。使用这种方法，当用户要访问下一个页面时，页面中的内容大部分已经加载到缓存中了，因此可以大大改善访问速度。

下面提供了几种预加载方法：

无条件加载：触发onload事件时，直接加载额外的页面内容。以Google.com为例，你可以看一下它的spirit image图像是怎样在onload中加载的。这个spirit image图像在google.com主页中是不需要的，但是却可以在搜索结果页面中用到它。

有条件加载：根据用户的操作来有根据地判断用户下面可能去往的页面并相应的预加载页面内容。在search.yahoo.com中你可以看到如何在你输入内容时加载额外的页面内容。

有预期的加载：载入重新设计过的页面时使用预加载。这种情况经常出现在页面经过重新设计后用户抱怨“新的页面看起来很酷，但是却比以前慢”。问题可 能出在用户对于你的旧站点建立了完整的缓存，而对于新站点却没有任何缓存内容。因此你可以在访问新站之前就加载一部内容来避免这种结果的出现。在你的旧站 中利用浏览器的空余时间加载新站中用到的图像的和脚本来提高访问速度。

##### 7、减少DOM元素数量

一个复杂的页面意味着需要下载更多数据，同时也意味着JavaScript遍历DOM的效率越慢。比如当你增加一个事件句柄时在500和5000个DOM元素中循环效果肯定是不一样的。

大量的DOM元素的存在意味着页面中有可以不用移除内容只需要替换元素标签就可以精简的部分。你在页面布局中使用表格了吗？你有没有仅仅为了布局而引入更多的<div>元素呢？也许会存在一个适合或者在语意是更贴切的标签可以供你使用。

YUI CSS utilities可以给你的布局带来巨大帮助：grids.css可以帮你实现整体布局，font.css和reset.css可以帮助你移除浏览器默 认格式。它提供了一个重新审视你页面中标签的机会，比如只有在语意上有意义时才使用<div>，而不是因为它具有换行效果才使用它。

DOM元素数量很容易计算出来，只需要在Firebug的控制台内输入：

document.getElementsByTagName(‘*’).length

那么多少个DOM元素算是多呢？这可以对照有很好标记使用的类似页面。比如Yahoo!主页是一个内容非常多的页面，但是它只使用了700个元素（HTML标签）。

##### 8、根据域名划分页面内容

把页面内容划分成若干部分可以使你最大限度地实现平行下载。由于DNS查找带来的影响你首先要确保你使用的域名数量在2个到4个之间。例如，你可以 把用到的HTML内容和动态内容放在www.52maomao.info上，而把页面各种组件（图片、脚本、CSS)分别存放在 statics1.52maomao.info和statics.52maomao.info上。

你可在Tenni Theurer和Patty Chi合写的文章《Maximizing Parallel Downloads in the Carpool Lane》找到更多相关信息。

##### 9、使iframe的数量最小

ifrmae元素可以在父文档中插入一个新的HTML文档。了解iframe的工作理然后才能更加有效地使用它，这一点很重要。

iframe优点：

1、解决加载缓慢的第三方内容如图标和广告等的加载问题；

2、Security sandbox；

3、并行加载脚本。

iframe的缺点：

1、即时内容为空，加载也需要时间；

2、会阻止页面加载；

3、没有语意。

##### 10、不要出现404错误

　　HTTP请求时间消耗是很大的，因此使用HTTP请求来获得一个没有用处的响应（例如404没有找到页面）是完全没有必要的，它只会降低用户体验而不会有一点好处。有些站点把404错误响应页面改为“你是不是要找***”，这虽然改进了用户体验但是同样也会浪费服务器资源（如数据库等）。最糟糕的情况是指向外部 JavaScript的链接出现问题并返回404代码。首先，这种加载会破坏并行加载；其次浏览器会把试图在返回的404响应内容中找到可能有用的部分当 作JavaScript代码来执行。

##### 11、使用内容分发网络

用户与你网站服务器的接近程度会影响响应时间的长短。把你的网站内容分散到多个、处于不同地域位置的服务器上可以加快下载速度。但是首先我们应该做些什么呢？

按地域布置网站内容的第一步并不是要尝试重新架构你的网站让他们在分发服务器上正常运行。根据应用的需求来改变网站结构，这可能会包括一些比较复杂 的任务，如在服务器间同步Session状态和合并数据库更新等。要想缩短用户和内容服务器的距离，这些架构步骤可能是不可避免的。

要记住，在终端用户的响应时间中有80%到90%的响应时间用于下载图像、样式表、脚本、Flash等页面内容。这就是网站性能黄金守则。和重新设 计你的应用程序架构这样比较困难的任务相比，首先来分布静态内容会更好一点。这不仅会缩短响应时间，而且对于内容分发网络来说它更容易实现。

内容分发网络（Content Delivery Network，CDN）是由一系列分散到各个不同地理位置上的Web服务器组成的，它提高了网站内容的传输速度。用于向用户传输内容的服务器主要是根据 和用户在网络上的靠近程度来指定的。例如，拥有最少网络跳数（network hops）和响应速度最快的服务器会被选定。

一些大型的网络公司拥有自己的CDN，但是使用像Akamai Technologies，Mirror Image Internet， 或者Limelight Networks这样的CDN服务成本却非常高。对于刚刚起步的企业和个人网站来说，可能没有使用CDN的成本预算，但是随着目标用户群的不断扩大和更加 全球化，CDN就是实现快速响应所必需的了。以Yahoo来说，他们转移到CDN上的网站程序静态内容节省了终端用户20%以上的响应时间。使用CDN是 一个只需要相对简单地修改代码实现显著改善网站访问速度的方法。

##### 12、为文件头指定Expires或Cache-Control

这条守则包括两方面的内容：

对于静态内容：设置文件头过期时间Expires的值为“Never expire”（永不过期）；

对于动态内容：使用恰当的Cache-Control文件头来帮助浏览器进行有条件的请求。

网页内容设计现在越来越丰富，这就意味着页面中要包含更多的脚本、样式表、图片和Flash。第一次访问你页面的用户就意味着进行多次的HTTP请 求，但是通过使用Expires文件头就可以使这样内容具有缓存性。它避免了接下来的页面访问中不必要的HTTP请求。Expires文件头经常用于图像 文件， 但是应该在所有的内容都使用他，包括脚本、样式表和Flash等。

浏览器（和代理）使用缓存来减少HTTP请求的大小和次数以加快页面访问速度。Web服务器在HTTP响应中使用Expires文件头来告诉客户端 内容需 要缓存多长时间。下面这个例子是一个较长时间的Expires文件头，它告诉浏览器这个响应直到2010年4月15日才过期。

Expires: Thu, 15 Apr 2010 20:00:00 GMT

如果你使用的是Apache服务器，可以使用ExpiresDefault来设定相对当前日期的过期时间。

下面这个例子是使用 ExpiresDefault来设定请求时间后10年过期的文件头：

ExpiresDefault “access plus 10 years”

要切记，如果使用了Expires文件头，当页面内容改变时就必须改变内容的文件名。依Yahoo!来说我们经常使用这样的步骤：在内容的文件名中加上版本号，yahoo_2.0.6.js。

使用Expires文件头只有会在用户已经访问过你的网站后才会起作用。当用户首次访问你的网站时这对减少HTTP请求次数来说是无效的，因为浏览 器的缓存是空的。因此这种方法对于你网站性能的改进情况要依据他们“预缓存”存在时对你页面的点击频率（“预缓存”中已经包含了页面中的所有内容）。 Yahoo!建立了一套测量方法，我们发现所有的页面浏览量中有75~85%都有“预缓存”。通过使用Expires文件头，增加了缓存在浏览器中内容的 数量，并且可以在用户接下来的请求中再次使用这些内容，这甚至都不需要通过用户发送一个字节的请求。

##### 13、Gzip压缩文件内容

网络传输中的HTTP请求和应答时间可以通过前端机制得到显著改善。的确，终端用户的带宽、互联网提供者、与对等交换点的靠近程度等都不是网站开发者所能决定的。但是还有其他因素影响着响应时间。通过减小HTTP响应的大小可以节省HTTP响应时间。

从HTTP/1.1开始，web客户端都默认支持HTTP请求中有Accept-Encoding文件头的压缩格式：

Accept-Encoding: gzip, deflate

如果web服务器在请求的文件头中检测到上面的代码，就会以客户端列出的方式压缩响应内容。Web服务器把压缩方式通过响应文件头中的Content- Encoding来返回给浏览器。

Content-Encoding: gzip

Gzip是目前最流行也是最有效的压缩方式。这是由GNU项目开发并通过RFC 1952来标准化的。另外仅有的一个压缩格式是deflate，但是它的使用范围有限效果也稍稍逊色。

Gzip大概可以减少70%的响应规模。目前大约有90%通过浏览器传输的互联网交换支持gzip格式。如果你使用的是Apache，gzip模块配置和你的版本有关：Apache 1.3使用mod_zip，而Apache 2.x使用moflate。

浏览器和代理都会存在这样的问题：浏览器期望收到的和实际接收到的内容会存在不匹配的现象。幸好，这种特殊情况随着旧式浏览器使用量的减少在减少。 Apache模块会通过自动添加适当的Vary响应文件头来避免这种状况的出现。

服务器根据文件类型来选择需要进行gzip压缩的文件，但是这过于限制了可压缩的文件。大多数web服务器会压缩HTML文档。对脚本和样式表进行 压缩同 样也是值得做的事情，但是很多web服务器都没有这个功能。实际上，压缩任何一个文本类型的响应，包括XML和JSON，都值得的。图像和PDF文件由于 已经压缩过了所以不能再进行gzip压缩。如果试图gizp压缩这些文件的话不但会浪费CPU资源还会增加文件的大小。

Gzip压缩所有可能的文件类型是减少文件体积增加用户体验的简单方法。

##### 14、配置ETag

Entity tags（ETags）（实体标签）是web服务器和浏览器用于判断浏览器缓存中的内容和服务器中的原始内容是否匹配的一种机制（“实体”就是所说的“内 容”，包括图片、脚本、样式表等）。增加ETag为实体的验证提供了一个比使用“last-modified date（上次编辑时间）”更加灵活的机制。Etag是一个识别内容版本号的唯一字符串。唯一的格式限制就是它必须包含在双引号内。原始服务器通过含有 ETag文件头的响应指定页面内容的ETag。

HTTP/1.1 200 OK

Last-Modified: Tue, 12 Dec 2006 03:03:59 GMT

ETag: “10c24bc-4ab-457e1c1f”

Content-Length: 12195

稍后，如果浏览器要验证一个文件，它会使用If-None-Match文件头来把ETag传回给原始服务器。在这个例子中，如果ETag匹配，就会返回一 个304状态码，这就节省了12195字节的响应。

GET /i/yahoo.gif HTTP/1.1

Host: love.52maomao.info

If-Modified-Since: Tue, 12 Dec 2006 03:03:59 GMT

If-None-Match: “10c24bc-4ab-457e1c1f”

HTTP/1.1 304 Not Modified

ETag的问题在于，它是根据可以辨别网站所在的服务器的具有唯一性的属性来生成的。当浏览器从一台服务器上获得页面内容后到另外一台服务器上进行 验证时ETag就会不匹配，这种情况对于使用服务器组和处理请求的网站来说是非常常见的。默认情况下，Apache和IIS都会把数据嵌入ETag中，这 会显著减少多服务器间的文件验证冲突。

Apache 1.3和2.x中的ETag格式为inode-size-timestamp，即使某个文件在不同的服务器上会处于相同的目录下，文件大小、权限、时间戳等都完全相同，但是在不同服务器上他们的内码也是不同的。

IIS 5.0和IIS 6.0处理ETag的机制相似。IIS中的ETag格式为Filetimestamp:ChangeNumber。用ChangeNumber来跟踪 IIS配置的改变。网站所用的不同IIS服务器间ChangeNumber也不相同。 不同的服务器上的Apache和IIS即使对于完全相同的内容产生的ETag在也不相同，用户并不会接收到一个小而快的304响应；相反他们会接收一个正 常的200响应并下载全部内容。

如果你的网站只放在一台服务器上，就不会存在这个问题。但是如果你的网站是架设在多个服务器上，并且使用Apache和IIS产生默认的ETag配 置，你的用户获得页面就会相对慢一点，服务器会传输更多的内容，占用更多的带宽，代理也不会有效地缓存你的网站内容。即使你的内容拥有Expires文件 头，无论用户什么时候点击“刷新”或者“重载”按钮都会发送相应的GET请求。

如果你没有使用ETag提供的灵活的验证模式，那么干脆把所有的ETag都去掉会更好。Last-Modified文件头验证是基于内容的时间戳 的。去掉 ETag文件头会减少响应和下次请求中文件的大小。微软的这篇支持文稿讲述了如何去掉ETag。在Apache中，只需要在配置文件中简单添加下面一行代 码就可以了：FileETag none。

##### 15、尽早刷新输出缓冲

当用户请求一个页面时，无论如何都会花费200到500毫秒用于后台组织HTML文件。在这期间，浏览器会一直空闲等待数据返回。在PHP中，你可 以使用flush()方法，它允许你把已经编译的好的部分HTML响应文件先发送给浏览器，这时浏览器就会可以下载文件中的内容（脚本等）而后台同时处理 剩余的 HTML页面。这样做的效果会在后台烦恼或者前台较空闲时更加明显。

输出缓冲应用最好的一个地方就是紧跟在<head />之后，因为HTML的头部分容易生成而且头部往往包含CSS和JavaScript文件，这样浏览器就可以在后台编译剩余HTML的同时并行下载它们。 例子：

… <!– css, js –>

</head> 

<body>

… <!– content –>

##### 16、使用GET来完成AJAX请求

Yahoo! Mail团队发现，当使用XMLHttpRequest时，浏览器中的POST方法是一个“两步走”的过程：首先发送文件头，然后才发送数据。因此使用 GET最为恰当，因为它只需发送一个TCP包（除非你有很多cookie）。IE中URL的最大长度为2K，因此如果你要发送一个超过2K的数据时就不能 使用GET了。

一个有趣的不同就是POST并不像GET那样实际发送数据。根据HTTP规范，GET意味着“获取”数据，因此当你仅仅获取数据时使用GET更加有意义（从语意上讲也是如此），相反，发送并在服务端保存数据时使用POST。

##### 17、把样式表置于顶部

　　在研究Yahoo!的性能表现时，我们发现把样式表放到文档的<head />内部似乎会加快页面的下载速度。这是因为把样式表放到<head />内会使页面有步骤的加载显示。

　　注重性能的前端服务器往往希望页面有秩序地加载。同时，我们也希望浏览器把已经接收到内容尽可能显示出来。这对于拥有较多内容的页面和网速较慢的用户来说 特别重要。向用户返回可视化的反馈，比如进程指针，已经有了较好的研究并形成了正式文档。在我　　们的研究中HTML页面就是进程指针。当浏览器有序地加载文 件头、导航栏、顶部的logo等对于等待页面加载的用户来说都可以作为可视化的反馈。这从整体上改善了用户体验。

把样式表放在文档底部的问题是在包括Internet Explorer在内的很多浏览器中这会中止内容的有序呈现。浏览器中止呈现是为了避免样式改变引起的页面元素重绘，用户不得不面对一个空白页面。

HTML规范清楚指出样式表要放包含在页面的<head />区域内：“和<a />不同，<link />只能出现在文档的<head />区域内，尽管它可以多次使用它”。无论是引起白屏还是出现没有样式化的内容都不值得去尝试。最好的方案就是按照HTML规范在文 档<head />内加载你的样式表。

##### 18、避免使用CSS表达式（Expression）

CSS表达式是动态设置CSS属性的强大（但危险）方法。Internet Explorer从第5个版本开始支持CSS表达式。下面的例子中，使用CSS表达式可以实现隔一个小时切换一次背景颜色：

background-color: expression( (new Date()).getHours()%2 ? “#B8D4FF” : “#F08A00″ );

如上所示，expression中使用了JavaScript表达式。CSS属性根据JavaScript表达式的计算结果来设置。 expression方法在其它浏览器中不起作用，因此在跨浏览器的设计中单独针对Internet Explorer设置时会比较有用。

表达式的问题就在于它的计算频率要比我们想象的多。不仅仅是在页面显示和缩放时，就是在页面滚动、乃至移动鼠标时都会要重新计算一次。给CSS表达式增加一个计数器可以跟踪表达式的计算频率。在页面中随便移动鼠标都可以轻松达到10000次以上的计算量。

一个减少CSS表达式计算次数的方法就是使用一次性的表达式，它在第一次运行时将结果赋给指定的样式属性，并用这个属性来代替CSS表达式。如果样 式属性必须在页面周期内动态地改变，使用事件句柄来代替CSS表达式是一个可行办法。如果必须使用CSS表达式，一定要记住它们要计算成千上万次并且可能 会对你页面的性能产生影响。

##### 19、使用外部JavaScript和CSS

很多性能规则都是关于如何处理外部文件的。但是，在你采取这些措施前你可能会问到一个更基本的问题：JavaScript和CSS是应该放在外部文件中呢还是把它们放在页面本身之内呢？

在实际应用中使用外部文件可以提高页面速度，因为JavaScript和CSS文件都能在浏览器中产生缓存。内置在HTML文档中的 JavaScript和CSS则会在每次请求中随HTML文档重新下载。这虽然减少了HTTP请求的次数，却增加了HTML文档的大小。从另一方面来说， 如果外部文件中的JavaScript和CSS被浏览器缓存，在没有增加HTTP请求次数的同时可以减少HTML文档的大小。

关键问题是，外部JavaScript和CSS文件缓存的频率和请求HTML文档的次数有关。虽然有一定的难度，但是仍然有一些指标可以一测量它。 如果一个会话中用户会浏览你网站中的多个页面，并且这些页面中会重复使用相同的脚本和样式表，缓存外部文件就会带来更大的益处。

许多网站没有功能建立这些指标。对于这些网站来说，最好的坚决方法就是把JavaScript和CSS作为外部文件引用。比较适合使用内置代码的例 外就是网站的主页，如Yahoo!主页和My Yahoo!。主页在一次会话中拥有较少（可能只有一次）的浏览量，你可以发现内置JavaScript和CSS对于终端用户来说会加快响应时间。

对于拥有较大浏览量的首页来说，有一种技术可以平衡内置代码带来的HTTP请求减少与通过使用外部文件进行缓存带来的好处。其中一个就是在首页中内 置 JavaScript和CSS，但是在页面下载完成后动态下载外部文件，在子页面中使用到这些文件时，它们已经缓存到浏览器了。

##### 20、削减JavaScript和CSS

精简是指从去除代码不必要的字符减少文件大小从而节省下载时间。消减代码时，所有的注释、不需要的空白字符（空格、换行、tab缩进）等都要去掉。 在 JavaScript中，由于需要下载的文件体积变小了从而节省了响应时间。精简JavaScript中目前用到的最广泛的两个工具是JSMin和YUI Compressor。YUI Compressor还可用于精简CSS。

混淆是另外一种可用于源代码优化的方法。这种方法要比精简复杂一些并且在混淆的过程更易产生问题。在对美国前10大网站的调查中发现，精简也可以缩 小原来代码体积的21%，而混淆可以达到25%。尽管混淆法可以更好地缩减代码，但是对于JavaScript来说精简的风险更小。

除消减外部的脚本和样式表文件外，<script>和<style>代码块也可以并且应该进行消减。即使你用Gzip压缩 过脚本和样式表，精简这些文件仍然可以节省5%以上的空间。由于JavaScript和CSS的功能和体积的增加，消减代码将会获得益处。

##### 21、用link代替@import

　　前面的最佳实现中提到CSS应该放置在顶端以利于有序加载呈现。

　　在IE中，页面底部@import和使用link作用是一样的，因此最好不要使用它。

​       　　LESS、SASS例外！

##### 22、避免使用滤镜

IE独有属性AlphaImageLoader用于修正7.0以下版本中显示PNG图片的半透明效果。这个滤镜的问题在于浏览器加载图片时它会终止内容的呈现并且冻结浏览器。在每一个元素（不仅仅是图片）它都会运算一次，增加了内存开支，因此它的问题是多方面的。

完全避免使用AlphaImageLoader的最好方法就是使用PNG8格式来代替，这种格式能在IE中很好地工作。如果你确实需要使用 AlphaImageLoader，请使用下划线_filter又使之对IE7以上版本的用户无效。

##### 23、把脚本置于页面底部

脚本带来的问题就是它阻止了页面的平行下载。HTTP/1.1 规范建议，浏览器每个主机名的并行下载内容不超过两个。如果你的图片放在多个主机名上，你可以在每个并行下载中同时下载2个以上的文件。但是当下载脚本 时，浏览器就不会同时下载其它文件了，即便是主机名不相同。

在某些情况下把脚本移到页面底部可能不太容易。比如说，如果脚本中使用了document.write来插入页面内容，它就不能被往下移动了。这里可能还会有作用域的问题。很多情况下，都会遇到这方面的问题。

一个经常用到的替代方法就是使用延迟脚本。DEFER属性表明脚本中没有包含document.write，它告诉浏览器继续显示。不幸的 是，Firefox并不支持DEFER属性。在Internet Explorer中，脚本可能会被延迟但效果也不会像我们所期望的那样。如果脚本可以被延迟，那么它就可以移到页面的底部，这会让你的页面加载的快一点。

##### 24、剔除重复脚本

在同一个页面中重复引用JavaScript文件会影响页面的性能。你可能会认为这种情况并不多见。对于美国前10大网站的调查显示其中有两家存在 重复引用脚本的情况。有两种主要因素导致一个脚本被重复引用的奇怪现象发生：团队规模和脚本数量。如果真的存在这种情况，重复脚本会引起不必要的HTTP 请求和无用的JavaScript运算，这降低了网站性能。

在Internet Explorer中会产生不必要的HTTP请求，而在Firefox却不会。在Internet Explorer中，如果一个脚本被引用两次而且它又不可缓存，它就会在页面加载过程中产生两次HTTP请求。即时脚本可以缓存，当用户重载页面时也会产 生额外的HTTP请求。

除增加额外的HTTP请求外，多次运算脚本也会浪费时间。在Internet Explorer和Firefox中不管脚本是否可缓存，它们都存在重复运算JavaScript的问题。

一个避免偶尔发生的两次引用同一脚本的方法是在模板中使用脚本管理模块引用脚本。在HTML页面中使用script 标签引用脚本的最常见方法就是：

```
<script type=”text/javascript” src=”menu_1.0.17.js”></script>
```

在PHP中可以通过创建名为insertScript的方法来替代：

为了防止多次重复引用脚本，这个方法中还应该使用其它机制来处理脚本，如检查所属目录和为脚本文件名中增加版本号以用于Expire文件头等。

##### 25、减少DOM访问

使用JavaScript访问DOM元素比较慢，因此为了获得更多的应该页面，应该做到：

1、缓存已经访问过的有关元素；

2、线下更新完节点之后再将它们添加到文档树中；

3、避免使用JavaScript来修改页面布局。

有关此方面的更多信息请查看Julien Lecomte在YUI专题中的文章《高性能Ajax程序》。

##### 26、开发智能事件处理程序

有时候我们会感觉到页面反应迟钝，这是因为DOM树元素中附加了过多的事件句柄并且些事件句病被频繁地触发。这就是为什么说使用event delegation（事件代理）是一种好方法了。如果你在一个div中有10个按钮，你只需要在div上附加一次事件句柄就可以了，而不用去为每一个按 钮增加一个句柄。事件冒泡时你可以捕捉到事件并判断出是哪个事件发出的。

你同样也不用为了操作DOM树而等待onload事件的发生。你需要做的就是等待树结构中你要访问的元素出现。你也不用等待所有图像都加载完毕。

你可能会希望用DOMContentLoaded事件来代替事件应用程序中的onAvailable方法。

##### 27、减小Cookie体积,最好使用*localStorage*

HTTP coockie可以用于权限验证和个性化身份等多种用途。coockie内的有关信息是通过HTTP文件头来在web服务器和浏览器之间进行交流的。因此保持coockie尽可能的小以减少用户的响应时间十分重要。

有关更多信息可以查看Tenni Theurer和Patty Chi的文章《When the Cookie Crumbles》。这们研究中主要包括：

1、去除不必要的coockie；

2、使coockie体积尽量小以减少对用户响应的影响；

3、注意在适应级别的域名上设置coockie以便使子域名不受影响。

设置合理的过期时间，较早地Expire时间和不要过早去清除coockie，都会改善用户的响应时间。

##### 28、对于页面内容使用无coockie域名

当浏览器在请求中同时请求一张静态的图片和发送coockie时，服务器对于这些coockie不会做任何地使用。因此他们只是因为某些负面因素而创建的 网络传输。所有你应该确定对于静态内容的请求是无coockie的请求。创建一个子域名并用他来存放所有静态内容。

如果你的域名是www.52maomao.info，你可以在static.52maomao.info上存在静态内容。但是，如果你不是在 www.52maomao.info 上而是在顶级域名52maomao.info设置了coockie，那么所有对于static.52maomao.info的请求都包含coockie。 在这种情 况下，你可以再重新购买一个新的域名来存在静态内容，并且要保持这个域名是无coockie的。Yahoo!使用的是ymig.com，YouTube使 用的是ytimg.com，Amazon使用的是images-anazon.com等等。

使用无coockie域名存在静态内容的另外一个好处就是一些代理（服务器）可能会拒绝对coockie的内容请求进行缓存。一个相关的建议就是， 如果你想确定应该使用52maomao.info还是www.52maomao.info 作为你的一主页，你要考虑到coockie带来的影响。忽略掉www会使你除了把coockie设置到*.example.org（*是泛域名解析，代表 了所有子域名）外没有其它选择，因此出于性能方面的考虑最好是使用带有www的子域名并且在它上面设置coockie。

##### 29、优化图像

设计人员完成对页面的设计之后，不要急于将它们上传到web服务器，这里还需要做几件事：

你可以检查一下你的GIF图片中图像颜色的数量是否和调色板规格一致。 使用imagemagick中下面的命令行很容易检查：identify-verbose image.gif。

如果你发现图片中只用到了4种颜色，而在调色板的中显示的256色的颜色槽，那么这张图片就还有压缩的空间。

尝试把GIF格式转换成PNG格式，看看是否节省空间。大多数情况下是可以压缩的。由于浏览器支持有限，设计者们往往不太乐意使用PNG格式的图 片，不过这 都是过去的事情了。现在只有一个问题就是在真彩PNG格式中的alpha通道半透明问题，不过同样的，GIF也不是真彩格式也不支持半透明。因此GIF能 做到的，PNG（PNG8）同样也能做到（除了动画）。下面这条简单的命令可以安全地把GIF格式转换为PNG格式：

convert image.gif image.png

“我们要说的是：给PNG一个施展身手的机会吧！”

在所有的PNG图片上运行pngcrush（或者其它PNG优化工具）。例如：

pngcrush image.png -rem alla -reduce -brute result.png

在所有的 JPEG图片上运行jpegtran。这个工具可以对图片中的出现的锯齿等做无损操作，同时它还可以用于优化和清除图片中的注释以及其它无用信息（如 EXIF信息）：

jpegtran -copy none -optimize -perfect src.jpg dest.jpg

##### 30、优化CSS Spirite

在Spirite中水平排列你的图片，垂直排列会稍稍增加文件大小；

Spirite 中把颜色较近的组合在一起可以降低颜色数，理想状况是低于256色以便适用PNG8格式；

便于移动，不要在Spirite的图像中间留有较大空隙。这虽然不大会增加文件大小但对于用户代理来说它需要更少的内存来把图片解压为像素地图。100×100的图片为1万像素，而 1000×1000就是100万像素。

##### 31、不要在HTML中缩放图像

　　不要为了在HTML中设置长宽而使用比实际需要大的图片。如果你需要：

　　<img width=”100″ height=”100″ src=”mycat.jpg” alt=”My Cat” />

　　那么你的图片（mycat.jpg）就应该是100×100像素而不是把一个500×500像素的图片缩小使用。

##### 32、favicon.ico要小而且可缓存

favicon.ico是位于服务器根目录下的一个图片文件。它是必定存在的，因为即使你不关心它是否有用，浏览器也会对它发出请求，因此最好不要 返回一 个404 Not Found的响应。由于是在同一台服务器上，它每被请求一次coockie就会被发送一次。这个图片文件还会影响下载顺序，例如在IE中当你在 onload中请求额外的文件时，favicon会在这些额外内容被加载前下载。

因此，为了减少favicon.ico带来的弊端，要做到：文件尽量地小，最好小于1K。

在适当的时候（也就是你不要打算再换 favicon.ico的时候，因为更换新文件时不能对它进行重命名）为它设置Expires文件头。你可以很安全地把Expires文件头设置为未来的几个月。你可以通过核对当前favicon.ico的上次编辑时间来作出判断。

Imagemagick可以帮你创建小巧的favicon。

##### 33、保持单个内容小于25K

这条限制主要是因为iPhone不能缓存大于25K的文件。注意这里指的是解压缩后的大小。由于单纯gizp压缩可能达不要求，因此精简文件就显得十分重要。

查看更多信息，请参阅Wayne Shea和Tenni Theurer的文件《Performance Research, Part 5: iPhone Cacheability – Making it Stick》。

##### 34、打包组件成复合文本

把页面内容打包成复合文本就如同带有多附件的Email，它能够使你在一个HTTP请求中取得多个组件（切记：HTTP请求是很奢侈的）。当你使用这条规则时，首先要确定用户代理是否支持（iPhone就不支持）。