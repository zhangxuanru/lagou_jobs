# 了解一下Golang的市场行情

项目地址：https://github.com/go-crawler/lagou_jobs

如果对你有所帮助，欢迎 Star :)

## 目标

在工作中 Golang 已是一份子，想让大家了解一下 Golang 的市场行情，也想让更多的人熟悉它。因此主要是展示数据分析的结果

目标站点是 [某招聘网站](https://www.lagou.com/) 的职位数据抓取和分析，爬取城市分别为 北京、上海、广州、深圳、杭州、成都，再得出一个结论

### 分析

首先需要进行页面分析，找到我们的抓取方向

![image](https://i.loli.net/2018/04/26/5ae1e28a3412a.jpeg)

搜索 golang 关键字，打开页面 F12 就能看到它发送了四个请求，留意 positionAjax.json 这个请求

![image](https://i.loli.net/2018/04/26/5ae1efe538791.jpeg)

我们仔细研判这个接口的入参和出参

### 入参

1、Query String Param

- city：请求的城市

- needAddtionalResult：是否需要补充额外的参数，这里默认 false

2、Form Data
- first：是否首页
- pn：页码
- kd：关键字

### 出参

![image](https://i.loli.net/2018/04/26/5ae1f4c9920a9.jpeg)

就是它了，从返回结果可得出许多有用的信息

- companyFullName：公司全称
- companyLabelList：公司标签
- companyShortName：公司简称
- companySize：公司规模
- education：学历要求
- financeStage：融资阶段

等等~


### 分页

在上面两张图中，可以发现在 content 节点中包含 pageNo、pageSize 字段，content.positionResult 节点有 totalCount 字段，可以得知当前是第几页，每页显示多少条，当前的职位总条数

需要注意一下，分页的计算是要向上取整的

## 数据

### 一、分布图

不同工作、工种，自然也会遍布在不同的工作区域，我们先了解一下各个城市的 Golang 工程师都主要在哪个区上班，心里留个底

#### 北京

![image](https://i.loli.net/2018/04/27/5ae291859667c.jpeg)

#### 上海

![image](https://i.loli.net/2018/04/27/5ae290856b774.jpeg)

#### 广州

![image](https://i.loli.net/2018/04/27/5ae28f1ab3e0c.jpeg)

#### 深圳

![image](https://i.loli.net/2018/04/27/5ae1fbebb1784.jpeg)

#### 杭州

![image](https://i.loli.net/2018/04/27/5ae29218c91dc.jpeg)

#### 成都

![image](https://i.loli.net/2018/04/27/5ae295b1059ed.jpeg)

### 二、招聘与职位数量对比

![image](https://i.loli.net/2018/04/27/5ae296b750dd8.png)

通过分析图中的数据，我们可以得知各城市的招聘职位数量
- 北京：348
- 上海：145
- 广州：37
- 成都：49
- 杭州：45
- 深圳：108

总共招聘的职位数量为 732 个，数量顺序分别为 北京 > 上海 > 深圳 > 成都 > 杭州 > 广州

还有另外一个关注点，就是招聘公司数量与职位的数量对比，可以看到 北京 招聘的职位数量为 348 个，而招聘的公司数量为 191 个，约为 1.82 的比例，也就是一家公司能提供两个 Golang 职位，它可能类别不同、（中级、中高级、高级）级别不同，具有一定可能性。而在广州，为 31 对比 37，虽然差额不大，但仍然存在这种现象

可以得出结果，Golang 在市场上具有一定的伸缩空间，也就是具有上升空间，一家公司会将 Golang 应用在多个不同的应用场景，也就是方向不同，需要的级别人才也就不同了

但是需要注意的是，Golang 的市场招聘人数目前份额还是较低，六个城市总数仅为 732 个，与其他大热语言相差有一定距离，需要谨慎

同时，面试 Golang 的人与其他大热语言相比会少些，职位的争夺是否小点呢？

### 三、招聘公司规模

![image](https://i.loli.net/2018/04/27/5ae2ab2babbd9.png)

通过查看招聘 Golang 工程师的公司规模，可以很直观的发现，微型公司使用 Golang 较少，其他类别的规模都有一定程度的应用，且差距不大。在 2000 人以上、50 - 150 人的公司规模中最受青睐

为什么呢，我认为有以下可能
- 大型公司结合场景，想通过 Golang 的特性来解决一些痛点问题
- 在小型公司 Golang 这颗新星实施起来更便捷，有一定的应用场景

你觉得呢，是不是应该有更多的选择它的原因？

### 四、学历要求

![image](https://i.imgur.com/dYOz2xB.png)

在招聘市场上，Golang 的招聘者更希望你是本科学历，大专和不限也有一定的份额，但市场份额相差较大

硕士学历要求的为两个，可以得出，在市场上 Golang 招聘者们对高学历的需求并不高，或者并不强制高学历

### 五、行业领域

![image](https://i.imgur.com/VdpmS5a.png)

在这里，重点关注 Golang 工程师的招聘公司都分别在什么行业领域，大头移动互联网是不容置疑的了，还可以惊喜的发现

- 数据服务
- 电子商务
- 金融
- 企业服务
- 游戏

Golang 在这几个方面都有所应用，说明了在市场上，Golang 的路子是比较广阔的，前景不错

同时，如果可以涉及多个领域的内容，想必身为工程师的你，肯定很激动

### 六、职位诱惑

![image](https://i.imgur.com/KlkGFI4.png)

职位诱惑是投简历时必看的一点了，可以看到高频词条基本都是 IT 从业者关心的话题了，这里你懂的...

重点，我看到了一个 “免费三餐” 的词条命中 7 次，分别来自北京的海淀区、东城区、朝阳区，上海的黄浦区的七家不同的公司，辛苦了

### 七、行业、职位标签

![image](https://i.imgur.com/8GGslq8.png)

在招聘JD中，描述和标签常用于给求职者了解这一职业的具体工作内容和其关联性

在图中你可以看到 Golang 常常和什么内容搭上边，这点很有意义哦

1、语言
- Java
- Python
- C/C++
- PHP

在图中可以看出，Golang 与以上四种语言有一定关联性，而 Java 和 Python 分别第一、第二名，可以说明市场上对复合型人才的渴望度更高，也许你不懂也行，但你懂了就最好（加分项）。需要你自身有多语言的经验，也便于和其他人对接

同时 Golang 目前存在许多内部转语言写的情况，所以这一点可以参考

2、职称
- 高级
- 资深
- 中级

特意将职称放在第二位，可以发现在市场上 Golang 标签的需求是 高级 > 资深 > 中级，关联第一项 “语言关联” 不难得出这个结论，因为语言只是解决问题的工具，到了中级及以上的工程师都是懂多门语言的居多，再采取不同的方案去解决应用场景上的问题

可得出结论，市场目前对 Golang 更期望是中高、高级、资深的人才，而中级的反而少一点点

大家可以努力再往上冲击冲击

3、组件
- Linux
- Redis
- Mysql

4、行业
- 云计算
- 信息安全
- 大数据
- 金融
- 软件开发

#### 八、薪资与工作年限

![image](https://i.imgur.com/CEYqOau.jpg)


1、1-3年

一个（成长）特殊的阶段，有个位数也有双位数的，大头可以到15-30k，20-40k，而初级的也有8-16k

2、3-5年

厚积待发的阶段，薪酬范畴的跨度是较大，10-60k的薪酬都有，这充分说明能力决定你的上下

3、5-10年

核心，招聘网站上的招聘数量反而少，都会走内推或猎头，不需要特别介绍了

##### 小结

这一部分，相信是很多人关注的地方

在有的文章中会看到，他们的薪资部分是以平均值来展示的。我就很纳闷，因为对平均值并不是很关心，**重点是无法体现薪资幅度**。因此这里我会尽可能的把数据展现给你们看

（正文）从图表来看，Golang 当前的薪酬水平还是很不错的，市场能根据不同阶段（水平）的人给出一个好的价位

（题外话）看完之后希望你能知道以下内容
- 你当前工作年限的最高、最低薪资范畴
- 你的下一阶段的薪资范畴
- 为什么有的人高，有的人低
- 在大头部队还是小头，为什么
- 不要满足于平均值

### 九、融资阶段

 ![image](https://i.imgur.com/H3R9TvZ.png)

选用 Golang 的公司大多数都较为稳定，有一部分比较刺激 :)

#### 融资阶段与薪资范畴对比

##### 不需要融资

![image](https://i.imgur.com/FoiRau8.png)

##### 上市公司

![image](https://i.imgur.com/ok22AsZ.png)

##### A轮

![image](https://i.imgur.com/wA4YFmR.png)

##### B轮

![image](https://i.imgur.com/kng4LTf.png)

##### C轮

![image](https://i.imgur.com/pYvpJuH.png)

##### D轮以上

![image](https://i.imgur.com/oKEDxif.png)

### 十、附近的地铁

Golang 工程师都驻扎在什么地铁站附近呢

经常在地铁上看到同行在看代码，来了解一下都分布在哪 :)

#### 北京

![image](https://i.imgur.com/Bjzx8Nf.png)

#### 上海

![image](https://i.imgur.com/CYHtWSi.png)

#### 广州

![image](https://i.imgur.com/pFuFMNy.png)

#### 深圳

![image](https://i.imgur.com/nPAoVil.png)

#### 杭州

![image](https://i.imgur.com/7dGFfns.png)

#### 成都

![image](https://i.imgur.com/DvsKJuu.png)


## 结论

如同官方所说 "Go has been on an amazing journey over the last 8+ years"，作为一门新生语言，一直在不断地发展，**缺点肯定是有的，你要去识别它**

### 从数量来看

单从这个招聘网站上来看，数量方面，与大热语言的招聘职位数量仍然有一定的差距，但 Golang 存在许多内部转语言开发的情况，当前展现出来的数据，**招聘数量不多，但质量不错**

### 从分布图来看

一线城市基本都有 Golang 的职位，虽然其他城市较少，但对于新语言来说是需要持续关注的过程，不能一刀切

### 从职称级别来看

Golang 中高、高级、资深仍然是占大头，给的薪资也基本符合市场行情

### 从方向来看

Golang 涉及的行业领域广泛，移动互联网、数据服务、电子商务、金融、企业服务、云计算等都是它的战场之一

### 从开源项目来看

docker、k8s、etcd、consul 都挺稳

---

总的来说，Golang 处于一个发展的阶段，市场行情也还行，你又怎么看呢？

最后放上今天新发布的 Logo :)

![image](https://i.imgur.com/nWO32Bl.jpg)