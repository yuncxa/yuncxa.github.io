---
title: 憨憨用hexo-sakura主题与GitHub建立个人博客的经历
author: yunc
avatar: https://cdn.jsdelivr.net/gh/yuncxa/cdn@0.9.1/img/custom/avatar.jpg
authorLink: https://yuncxa.github.io
authorAbout: 一只憨憨
authorDesc: 一只又傻又可爱又……的小憨憨
categories: 技术
date: 2021-02-09 21:51:01
comments: true
tags: 
- web
keywords: blog
description: Hexo-Sakura-github=blog
photos: https://cdn.jsdelivr.net/gh/yuncxa/cdn@21.02.10/img/post202102/github.jpg
---

为什么用hexo和GitHub呢？  

答案是 矮、穷、矬  

- 刚刚入门，没有考虑去接触wordpress，视野较矮

- GitHub作为免费开源社区，对于我这种穷学生党再合适不过，一个服务器买下来，一件衣服、一顿大餐、一个npy…… 就都没了

- 经受不住HTML+CSS+JavaScript+…… 等等等的巨大工作量。相比之下，markdown嗯，nice！  

  同样的输出结果，在markdown下的代码

![alt html代码](https://znb-img.oss-cn-shanghai.aliyuncs.com/img/image-20200624102503203.png)

而在HTML下

![alt html代码](https://znb-img.oss-cn-shanghai.aliyuncs.com/img/image-20200624102852111.png)

注：图片引用自CSDN博客[什么是Markdown?为什么需要使用Markdown？](https://blog.csdn.net/xdjokhal/article/details/106954105) 

---

(⊙﹏⊙)，文章有点长

🆗，正文开始。

> 目录
>
> 1. hexo
>
>    > 环境搭建
>    >
>    > 创建第一个blog
>
> 2. GitHub  
>
>    > 建仓库
>    >
>    > 部署到远程仓库
>
> 3. Sakura主题 
>
>    > 应用主题
>    >
>    > 主题自定义
>    >
>    > cdn和leancloud

---

# hexo

#### 1. 环境搭建

**step 1** 安装node.js 和 git

两个全都是下载完成然后一直下一步傻瓜式安装  ,安装完后检查一下  

``` 
node -v	#查看node版本
npm -v	#查看npm版本
```

but，node.js最新版好像对Sakura兼容不是很好，这里推荐下载[旧版本](https://nodejs.org/dist/)

亲测v12.9.1可用  

**step 2** 安装hexo框架  

npm下载可能很慢，所以我们换成淘宝的cnpm源（b站学的）

```
npm install -g cnpm --registry=http://registry.npm.taobao.org	
cnpm -v	#查看cnpm版本
```

用cnpm安装hexo框架

```
cnpm install -g hexo-cli # 安装hexo框架   
hexo -v	#查看hexo版本
```

#### 2.创建第一篇blog文章

**step 1**

```
mkdir blog	#创建blog目录,win 10 cmd输d：进入D盘
cd blog	 #进入blog目录,或者在blog目录下右键用git bash
sudo hexo init 	#生成博客 初始化博客,win 10 去掉sudo，不需要
hexo n "我的第一篇文章" #创建新的文章，双引号内为文章标题 
```

*如果 hexo init 之后blog目录下只有一个文件，则删掉它重复这个step*

**step 2** hexo三部曲

```
hexo clean #清理
hexo g #生成
hexo s	#启动本地博客服务
```

http://localhost:4000/  为本地访问地址，在浏览器查看

---

# GitHub

#### 1. 建仓库

**step 1** 创建账号

**step 2** new repository

右上角头像旁边加号，输入repository name

```
# Github创建一个新的仓库 YourGithubName.github.io
# 即仓库名与GitHub用户名相同
```

建好后得到仓库地址 https://github.com/YourGithubName/YourGithubName.github.io.git

```
https://YourGithubName.github.io/  #访问这个地址可以查看博客
```

**step 3** 安装git插件  

```
cnpm install --save hexo-deployer-git #在blog目录下安装git部署插件
```



#### 2. 部署到GitHub远程仓库

**step 1** 配置_config.yml  

新建的blog文件夹根目录下的_config.yml这几行改成  

```
-----
	# Deployment
	## Docs: https://hexo.io/docs/deployment.html
	deploy:
		type: git
		repo: https://github.com/YourGithubName/YourGithubName.github.io.git
		branch: master
-----
```



**step 2** hexo三部曲

```
hexo clean	#清理一下
hexo g	#生成
hexo d	#部署到远程Github仓库，可能会要求输账号密码或设置git
https://YourGithubName.github.io/  #查看博客
```

*到这里，blog就可以用啦，但是好简陋。*

---

# Sakura主题使用

*这里我使用的是Sakura主题，不同主题使用方法不同，可以去hexo官网挑*

[hexo 官网](https://hexo.io/zh-cn/)  

*接下来的内容由Sakura官方教程修改*

#### 1、主题下载安装

[hexo-theme-sakura](https://github.com/honjun/hexo-theme-sakura)建议下载压缩包格式，因为除了主题内容还有些source的配置对新手来说比较太麻烦，直接下载解压就省去这些麻烦咯。

下载好后解压到博客根目录（不是主题目录哦，重复的选择替换）。接着在命令行（cmd、bash）运行`npm i`安装依赖。

#### 2、主题配置

**博客根目录下的_config配置**

 **step 1** 站点

```yml
*# Site*

title: 你的站点名

subtitle:

description: 站点简介

keywords:

author: 作者名

language: zh-cn

timezone:
```

**step 2** 部署

```yml
deploy:

 type: git

 repo: 

  github: 你的github仓库地址

  *# coding: 你的coding仓库地址*

 branch: master
```

**step 3** 备份 （使用hexo b发布备份到远程仓库）

```yml
backup:

 type: git

 message: backup my blog of https://honjun.github.io/

 repository:

  *# 你的github仓库地址,备份分支名 （建议新建backup分支）*

  github: https://github.com/honjun/honjun.github.io.git,backup

  *# coding: https://git.coding.net/hojun/hojun.git,backup*
```

**主题目录下的_config配置**

*其中标明【改】的是需要修改部门，标明【选】是可改可不改，标明【非】是不用改的部分*

**step 1** 修改说明

```yml
*# site name*

*# 站点名 【改】*

prefixName: さくら荘その

siteName: hojun



*# favicon and site master avatar*

*# 站点的favicon和头像 输入图片路径（下面的配置是都是cdn的相对路径，没有cdn请填写完整路径，建议使用jsdeliver搭建一个cdn啦，先去下载我的cdn替换下图片就行了，简单方便~）【改】*

favicon: /images/favicon.ico

avatar: /img/custom/avatar.jpg



*# 站点url 【改】*

url: https://sakura.hojun.cn



*# 站点介绍（或者说是个人签名）【改】*

description: Live your life with passion! With some drive!



*# 站点cdn，没有就为空 【改】 若是cdn为空，一些图片地址就要填完整地址了，比如之前avatar就要填https://cdn.jsdelivr.net/gh/honjun/cdn@1.6/img/custom/avatar.jpg*

cdn: https://cdn.jsdelivr.net/gh/honjun/cdn@1.6



*# 开启pjax 【选】*

pjax: 1



*# 站点首页的公告信息 【改】*

notice: hexo-Sakura主题已经开源，目前正在开发中...



*# 懒加载的加载中图片 【选】*

lazyloadImg: https://cdn.jsdelivr.net/gh/honjun/cdn@1.6/img/loader/orange.progress-bar-stripe-loader.svg



*# 站点菜单配置 【选】*

menus:

 首页: { path: /, fa: fa-fort-awesome faa-shake }

 归档: { path: /archives, fa: fa-archive faa-shake, submenus: { 

  技术: {path: /categories/技术/, fa: fa-code }, 

  生活: {path: /categories/生活/, fa: fa-file-text-o }, 

  资源: {path: /categories/资源/, fa: fa-cloud-download }, 

  随想: {path: /categories/随想/, fa: fa-commenting-o },

  转载: {path: /categories/转载/, fa: fa-book }

 } }

 清单: { path: javascript:;, fa: fa-list-ul faa-vertical, submenus: { 

  书单: {path: /tags/悦读/, fa: fa-th-list faa-bounce }, 

  番组: {path: /bangumi/, fa: fa-film faa-vertical }, 

  歌单: {path: /music/, fa: fa-headphones },

  图集: {path: /tags/图集/, fa: fa-photo }

 } }

 留言板: { path: /comment/, fa: fa-pencil-square-o faa-tada }

 友人帐: { path: /links/, fa: fa-link faa-shake }

 赞赏: { path: /donate/, fa: fa-heart faa-pulse }

 关于: { path: /, fa: fa-leaf faa-wrench , submenus: { 

  我？: {path: /about/, fa: fa-meetup}, 

  主题: {path: /theme-sakura/, fa: iconfont icon-sakura },

  Lab: {path: /lab/, fa: fa-cogs },

 } }

 客户端: { path: /client/, fa: fa-android faa-vertical }

 RSS: { path: /atom.xml, fa: fa-rss faa-pulse }



*# Home page sort type: -1: newer first，1: older first. 【非】*

homePageSortType: -1



*# Home page article shown number) 【非】*

homeArticleShown: 10



*# 背景图片 【选】*

bgn: 8



*# startdash面板 url, title, desc img 【改】*

startdash: 

 \- {url: /theme-sakura/, title: Sakura, desc: 本站 hexo 主题, img: /img/startdash/sakura.md.png}

 \- {url: http://space.bilibili.com/271849279, title: Bilibili, desc: 博主的b站视频, img: /img/startdash/bilibili.jpg}

 \- {url: /, title: hojun的万事屋, desc: 技术服务, img: /img/startdash/wangshiwu.jpg}





*# your site build time or founded date*

*# 你的站点建立日期 【改】*

siteBuildingTime: 07/17/2018





*# 社交按钮(social) url, img PC端配置 【改】*

social:

 github: {url: http://github.com/honjun, img: /img/social/github.png}

 sina: {url: http://weibo.com/mashirozx?is_all=1, img: /img/social/sina.png}

 wangyiyun: {url: http://weibo.com/mashirozx?is_all=1, img: /img/social/wangyiyun.png}

 zhihu: {url: http://weibo.com/mashirozx?is_all=1, img: /img/social/zhihu.png}

 email: {url: http://weibo.com/mashirozx?is_all=1, img: /img/social/email.svg}

 wechat: {url: /#, qrcode: /img/custom/wechat.jpg, img: /img/social/wechat.png}



*# 社交按钮(msocial) url, img 移动端配置 【改】*

msocial:

 github: {url: http://github.com/honjun, fa: fa-github, color: 333}

 weibo: {url: http://weibo.com/mashirozx?is_all=1, fa: fa-weibo, color: dd4b39}

 qq: {url: https://wpa.qq.com/msgrd?v=3&uin=954655431&site=qq&menu=yes, fa: fa-qq, color: 25c6fe}



*# 赞赏二维码（其中wechatSQ是赞赏单页面的赞赏码图片）【改】*

donate:

 alipay: /img/custom/donate/AliPayQR.jpg

 wechat: /img/custom/donate/WeChanQR.jpg

 wechatSQ: /img/custom/donate/WeChanSQ.jpg



*# 首页视频地址为https://cdn.jsdelivr.net/gh/honjun/hojun@1.2/Unbroken.mp4，配置如下 【改】*

movies:

 url: https://cdn.jsdelivr.net/gh/honjun/hojun@1.2

 *# 多个视频用逗号隔开，随机获取。支持的格式目前已知MP4,Flv。其他的可以试下，不保证有用*

 name: Unbroken.mp4



*# 左下角aplayer播放器配置 主要改id和server这两项，修改详见[aplayer文档] 【改】*

aplayer: 

 id: 2660651585

 server: netease

 type: playlist

 fixed: true

 mini: false

 autoplay: false

 loop: all

 order: random

 preload: auto

 volume: 0.7

 mutex: true



*# Valine评论配置【改】*

valine: true

v_appId: GyC3NzMvd0hT9Yyd2hYIC0MN-gzGzoHsz

v_appKey: mgOpfzbkHYqU92CV4IDlAUHQ
```

**step 2** [创建cdn教程点击查看](https://blog.csdn.net/weixin_45631738/article/details/104731332)

下载[作者cdn压缩包](https://github.com/honjun/cdn)，再新建并git clone自己的cdn仓库地址

```
git clone https://https://github.com/YourGithubName/cdn.github.io.git
```

将作者除.git外的文件复制进自己cdn文件夹，然后

```
git add * //注意 *代表当前目录下所用的文件
git commit -m "add files" //然后推送到本地仓库
git push //推送到远程仓库
```

cdn上传后记得更新release

**step 3** leancloud创建应用获取appid和appkey

**分类页和标签页配置**

**step 1** 标签页

![](https://wx2.sinaimg.cn/large/006bYVyvly1g07azb2399j31040jgazs.jpg)



配置项在\themes\Sakura\languages\zh-cn.yml里。新增一个分类或标签最好加下哦，当然嫌麻烦可以直接使用一张默认图片（可以改主题或者直接把404图片替换下，征求下意见要不要给这个在配置文件中加个开关，可以issue或群里提出来），现在是没设置的话会使用那种倒立小狗404哦。

```yml
*#category*

*# 按分类名创建*

技术:

  *#中文标题*

  zh: 野生技术协会 

  *# 英文标题*

  en: Geek – Only for Love

  *# 封面图片*

  img: https://cdn.jsdelivr.net/gh/honjun/cdn@1.6/img/banner/coding.jpg

生活:

  zh: 生活

  en: live

  img: https://cdn.jsdelivr.net/gh/honjun/cdn@1.6/img/banner/writing.jpg



*#tag*

*# 标签名即是标题*

悦读:

  *# 封面图片*

  img: https://cdn.jsdelivr.net/gh/honjun/cdn@1.6/img/banner/reading.jpg
```

**step 2** 单页面封面配置

如留言板页面页面，位于source下的comment下，打开index.md如下：

```markdown
\---

title: comment

date: 2018-12-20 23:13:48

keywords: 留言板

description: 

comments: true

\# 在这里配置单页面头部图片，自定义替换哦~

photos: https://cdn.jsdelivr.net/gh/honjun/cdn@1.4/img/banner/comment.jpg

\---
```

**step 3** 单页面配置

 番组计划页 （请直接在下载后的文件中改，下面的添加了注释可能会有些影响）

![](https://wx2.sinaimg.cn/large/006bYVyvly1g07b2gyx60j31090jjahj.jpg)

```yml
\```yml

\---

layout: bangumi

title: bangumi

comments: false

date: 2019-02-10 21:32:48

keywords:

description:

bangumis:

 *# 番组图片*

 \- img: https://lain.bgm.tv/pic/cover/l/0e/1e/218971_2y351.jpg

 *# 番组名*

  title: 朝花夕誓——于离别之朝束起约定之花

 *# 追番状态 （追番ing/已追完）*

  status: 已追完

 *# 追番进度*

  progress: 100

 *# 番剧日文名称*

  jp: さよならの朝に約束の花をかざろう

 *# 放送时间*

  time: 放送时间: 2018-02-24 SUN.

 *# 番剧介绍*

  desc: 住在远离尘嚣的土地，一边将每天的事情编织成名为希比欧的布，一边静静生活的伊欧夫人民。在15岁左右外表就停止成长，拥有数百年寿命的他们，被称为“离别的一族”，并被视为活着的传说。没有双亲的伊欧夫少女玛奇亚，过着被伙伴包围的平稳日子，却总感觉“孤身一人”。他们的这种日常，一瞬间就崩溃消失。追求伊欧夫的长寿之血，梅萨蒂军乘坐着名为雷纳特的古代兽发动了进攻。在绝望与混乱之中，伊欧夫的第一美女蕾莉亚被梅萨蒂带走，而玛奇亚暗恋的少年克里姆也失踪了。玛奇亚虽然总算逃脱了，却失去了伙伴和归去之地……。

 \- img: https://lain.bgm.tv/pic/cover/l/0e/1e/218971_2y351.jpg

  title: 朝花夕誓——于离别之朝束起约定之花

  status: 已追完

  progress: 50

  jp: さよならの朝に約束の花をかざろう

  time: 放送时间: 2018-02-24 SUN.

  desc: 住在远离尘嚣的土地，一边将每天的事情编织成名为希比欧的布，一边静静生活的伊欧夫人民。在15岁左右外表就停止成长，拥有数百年寿命的他们，被称为“离别的一族”，并被视为活着的传说。没有双亲的伊欧夫少女玛奇亚，过着被伙伴包围的平稳日子，却总感觉“孤身一人”。他们的这种日常，一瞬间就崩溃消失。追求伊欧夫的长寿之血，梅萨蒂军乘坐着名为雷纳特的古代兽发动了进攻。在绝望与混乱之中，伊欧夫的第一美女蕾莉亚被梅萨蒂带走，而玛奇亚暗恋的少年克里姆也失踪了。玛奇亚虽然总算逃脱了，却失去了伙伴和归去之地……。

\---
```

友链页 （请直接在下载后的文件中改，下面的添加了注释可能会有些影响）

```yml
\---

layout: links

title: links

*# 创建日期，可以改下*

date: 2018-12-19 23:11:06 

*# 图片上的标题，自定义修改*

keywords: 友人帐 

description: 

*# true/false 开启/关闭评论*

comments: true 

*# 页面头部图片，自定义修改*

photos: https://cdn.jsdelivr.net/gh/honjun/cdn@1.4/img/banner/links.jpg 

*# 友链配置*

links: 

 *# 类型分组*

 \- group: 个人项目

  *# 类型简介*

  desc: 充分说明这家伙是条咸鱼 < (￣︶￣)>

  items:

  *# 友链链接*

  \- url: https://shino.cc/fgvf

  *# 友链头像*

   img: https://cloud.moezx.cc/Picture/svg/landscape/fields.svg

  *# 友链站点名*

   name: Google

  *# 友链介绍 下面雷同*

   desc: Google 镜像

  \- url: https://shino.cc/fgvf

   img: https://cloud.moezx.cc/Picture/svg/landscape/fields.svg

   name: Google

   desc: Google 镜像

 *# 类型分组...*

 \- group: 小伙伴们

  desc: 欢迎交换友链 ꉂ(ˊᗜˋ)

  items:

  \- url: https://shino.cc/fgvf

   img: https://cloud.moezx.cc/Picture/svg/landscape/fields.svg

   name: Google

   desc: Google 镜像

  \- url: https://shino.cc/fgvf

   img: https://cloud.moezx.cc/Picture/svg/landscape/fields.svg

   name: Google

   desc: Google 镜像

\---
```

写文章配置(文章开头)

```markdown
title: {{ title }}
date: {{ date }}
author: hojun
avatar: https://wx1.sinaimg.cn/large/006bYVyvgy1ftand2qurdj303c03cdfv.jpg
authorLink: hojun.cn
authorAbout: 一个好奇的人
authorDesc: 一个好奇的人
categories: 技术
comments: true
tags: 
keywords: 
description: 
photos: 
```

主题集成了个人插件hexo-tag-bili和hexo-tag-fancybox_img。其中hexo-tag-bili用来在文章或单页面中插入B站外链视频，使用语法如下：

```markdown
{% bili video_id [page] %}
```

详细使用教程详见[hexo-tag-bili](https://github.com/honjun/hexo-tag-bili/blob/master/README-zh_cn.md)。

hexo-tag-fancybox_img用来在文章或单页面中图片，使用语法如下：

```markdown
{% fb_img src [caption] %}
```

详细使用教程详见[hexo-tag-fancybox_img](https://github.com/honjun/hexo-tag-fancybox_img/blob/master/README-zh_cn.md)

其他页面自定义按照同样的方法改source目录下文件



最后更新 2021.02.10

