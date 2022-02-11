#### Url规则
hosts和dns拦截，是拦截整个域名，url 可以针对 url 的关键字拦截，但只支持部分应用。
制作规则前，再简单说明一下hosts跟url拦截的相同点和不同点。
就以优酷为例：
1. 假设地址是http://tv.youku.com/aaa/bbb/ccc/xxxxxx.html,那么tv.youku.com就是主域名，把它填到hosts或url关键字里，起的作用是完全相同的，都是屏蔽了优酷视频，都打不开。
但视频广告却在ccc下，很明显Hosts屏蔽广告方式就失败了，而在Url关键字填入http://tv.youku.com/aaa/bbb/ccc/就可以正确拦截广告而不伤及其它有用的视频链接。
2. 通过上面的描述，估计大家就会明白为何hosts拦截会容易造成误伤了。
3. 优酷视频，为防止被hosts拦截，广告视频链接是藏在主域名下的，因此没有一个hosts能去其广告，甭找了！由于给主域带来沉重负担，所以打开优酷比其他视频客户端都显得卡卡卡。

#### Hosts，url拦截 规则制作
这两个方式的规则制作，就必须用到第三方的抓包软件了，这里向大家推荐一个在国内应用市场挺热门的APP（Packet Capture 无ROOT抓包）。抓包软件使用就不赘述了。
这里以“江苏移动营业厅”这个APP为例：
<img src="https://raw.githubusercontent.com/wiki/jdlingyu/ad-wars/images/url_capture.jpg" width="250">

<img src="https://raw.githubusercontent.com/wiki/jdlingyu/ad-wars/images/url_capture_app.jpg" width="250">

通过上图，就会知道，假如用hosts方式填wap.js.10086.cn到域名拦截的话，那么营业厅也就会没网了。
1. 抓到的目标页，分析地址，填到Url关键字里面，保存规则。
2. 还必须手动删除营业厅缓存的广告图片，路径在内置存储的jsmcc/.images下面。

注意：通过hosts及url拦截的，需要在应用还未缓存广告文件到手机之前就要生效，所以新添加规则的APP为确保拦截有效，须先清空一次数据。