---
layout:     post
title:      "使用jekyll搭建个人博客"
subtitle:   "简单的记录下如何使用Jekyll搭建博客"
date:       2017-03-09
author:     "Cheng"
header-img: "img/post-bg-unix-linux.jpg"
tags:
    - 博客搭建
---

> 文章不够完善，随时可能会更新。

## [Hux blog](http://huxpro.github.io)

这个博客的模板是我在[Huxpro.github](https://github.com/Huxpro/huxpro.github.io)中看到的。原作者的README已经写得很好了，所以你会发现文章里出现Hux（黄玄），这是原作者的名字，文章大部分内容都是原作者README中的文档，我会增加一些个人的意见作为补充，其他的不会作改变。

同时我也参考了[一步一步创建Jekyll主题](http://www.jokinkuang.info/2016/09/03/how-to-create-the-jekyll-theme.html)这篇博文的一些内容，作者写得很详细，有兴趣可以看一看。

## 说明文档

* 开始
	* [环境要求](#environment)
	* [开始](#get-started)
	* [博客结构](#structure)
	* [写一篇博文](#write-posts)
* 组件
	* [侧边栏](#sidebar)
	* [迷你关于我](#mini-about-me)
	* [推荐标签](#featured-tags)
	* [好友链接](#friends)
	* [HTML5 演示文档布局](#keynote-layout)
* 评论与 Google/Baidu Analytics
	* [评论](#comment)
	* [网站分析](#analytics) 
* 高级部分
	* [自定义](#customization)
	* [标题底图](#header-image)
	* [搜索展示标题-头文件](#seo-title)

---

### Environment

- **安装[Ruby](http://rubyinstaller.org/downloads/)**

	国内链接 [rubyinstaller-2.3.3.exe-32](http://omkrno85z.bkt.clouddn.com/rubyinstaller-2.3.3.exe) & [rubyinstaller-2.3.3.exe-64](http://omkrno85z.bkt.clouddn.com/rubyinstaller-2.3.3-64.exe)。
	注意安装到这一步时请将 Add Ruby executables to your PATH 勾选。
	![Path](/img/post/2017-03-09-jekyll-note-path.png)

- **安装[DEVELOPMENT KIT](http://rubyinstaller.org/downloads/)**

	国内链接 [DevKit-tdm-32](http://omkrno85z.bkt.clouddn.com/DevKit-mingw64-32-4.7.2-20130224-1151-sfx.exe) & [DevKit-tdm-64](http://omkrno85z.bkt.clouddn.com/DevKit-mingw64-64-4.7.2-20130224-1432-sfx.exe)。

- **在命令行中运行以下命令**

	`ruby dk.rb init`  生成_config.yml文件

	`ruby dk.rb install` 

	`gem install jekyll`  安装jekyll


- **后续操作**

	`jekyll --version` 查看当前jekyll版本

	`gem update jekyll`  更新jekyll

	`gem update github-pages` 更新依赖包

### Get Started

-  **通过以下命令新建一个可以运行在浏览器上的本地博客**

	`jekyll new myblog`  新建名为myblog的本地博客文件夹

	`cd myblog` 将操作区切换到新建的myblog文件夹

	`gem install bundler` 安装bundler。注：通过bundler运行本地博客时，页面效果和GitHub Pages上一样（这里我还不太明白）。如果你不需要或搞不懂，跳过所有和bundler有关的命令，直接运行`jekyll server`即可

	`bundle install` 安装github pages的依赖

	`bundle exec jekyll server` 运行myblog博客

	`jekyll server` 运行myblog博客，在浏览器输入http://127.0.0.1:4000/进行访问。注：通过`jekyll new myblog`完成博客新建后，下一次想运行时只需在myblog文件夹使用Git Bash或使用命令行`cd myblog`后，输入`jekyll server`即可

-  **通过简单修改 `_config.yml`文件来轻松的开始搭建自己的博客:**

	```
	# Site settings
	title: Cheng Blog             # 你的博客网站标题
	SEOTitle: Cheng Blog			# 在后面会详细谈到
	description: "This is  MyBlog"    # 随便说点，描述一下

	# SNS settings      
	github_username: Cheng-Ya     # 你的github账号
	你的微博账号，底部链接会自动更新的。

	# Build settings
	# paginate: 10              # 一页你准备放几篇文章

	```

	Jekyll官方网站还有很多的参数可以调，比如设置文章的链接形式...网址在这里：[Jekyll - Official Site](http://jekyllrb.com/) 中文版的在这里：[Jekyll中文](http://jekyllcn.com/).

### Structure
运行`jekyll new myblog`命令后，生成的文件夹结构类似如下：
![structure](/img/post/2017-03-09-jekyll-note-structure.png)

```
_config.yml:  核心配置文件
_drafts:  存放草稿也就是暂时不准备发布的文章
_includes:  存放一些页面以便于重用,例如head.html
_layouts:  在YAML头信息里根据不同需求引用不同的_layouts文件
_posts:  用来存放要发布的文章
_site: jekyll转化后的静态页面
index.html:  通常为主页，也可以是.markdown,.md后缀的文件
```
[关于目录结构介绍的官方文档](http://jekyll.com.cn/docs/structure/)

下面是简化版的结构:
![structureeasy](/img/post/2017-03-09-jekyll-note-structureeasy.png)
如果你搞不清各个文件是什么意思，按简化版的结构增加或删除文件/文件夹即可。

也可以参考[开始制作自己的jekyll主题](http://www.jokinkuang.info/2016/09/03/how-to-create-the-jekyll-theme.html#开始制作自己的jekyll主题)这里的内容了解模板的结构。
#### write-posts

要发表的文章一般以markdown的格式放在这里`_posts`文件夹中，你只要看看这篇模板里的文章你就立刻明白该如何设置。

yaml 头文件长这样:

```
---
layout:     post
title:      "Hello 2015"
subtitle:   "Hello World, Hello Blog"
date:       2015-01-29 12:00:00
author:     "Hux"
header-img: "img/post-bg-2015.jpg"
tags:
    - Life
---

```

#### SideBar

看右边:
![](http://huangxuan.me/img/blog-sidebar.jpg)

设置是在 `_config.yml`文件里面的`Sidebar settings`那块。
```
# Sidebar settings
sidebar: true  #添加侧边栏
sidebar-about-description: "简单的描述一下你自己"
sidebar-avatar: /img/avatar-hux.jpg     #你的大头贴，请使用绝对地址.
```

侧边栏是响应式布局的，当屏幕尺寸小于992px的时候，侧边栏就会移动到底部。具体请见bootstrap栅格系统 <http://v3.bootcss.com/css/>


#### Mini About Me

Mini-About-Me 这个模块将在你的头像下面，展示你所有的社交账号。这个也是响应式布局，当屏幕变小时候，会将其移动到页面底部，只不过会稍微有点小变化，具体请看代码。

#### Featured Tags

看到这个网站 [Medium](http://medium.com) 的推荐标签非常的炫酷，所以我将他加了进来。
这个模块现在是独立的，可以呈现在所有页面，包括主页和发表的每一篇文章标题的头上。

```
# Featured Tags
featured-tags: true  
featured-condition-size: 1     # A tag will be featured if the size of it is more than this condition value
```

唯一需要注意的是`featured-condition-size`: 如果一个标签的 SIZE，也就是使用该标签的文章数大于上面设定的条件值，这个标签就会在首页上被推荐。
 



#### Friends

好友链接部分。这会在全部页面显示。

设置是在 `_config.yml`文件里面的`Friends`那块，自己加吧。

```
# Friends
friends: [
    {
        title: "Foo Blog",
        href: "http://foo.github.io/"
    },
    {
        title: "Bar Blog",
        href: "http://bar.github.io"
    }
]
```


#### Keynote Layout

HTML5幻灯片的排版：

![](http://huangxuan.me/img/blog-keynote.jpg)

这部分是用于占用html格式的幻灯片的，一般用到的是 Reveal.js, Impress.js, Slides, Prezi 等等.我认为一个现代化的博客怎么能少了放html幻灯的功能呢~

其主要原理是添加一个 `iframe`，在里面加入外部链接。你可以直接写到头文件里面去，详情请见下面的yaml头文件的写法。

```
---
layout:     keynote
iframe:     "http://huangxuan.me/js-module-7day/"
---
```

iframe在不同的设备中，将会自动的调整大小。保留内边距是为了让手机用户可以向下滑动，以及添加更多的内容。


#### Comment

博客不仅支持多说[Duoshuo](http://duoshuo.com)评论系统，也支持[Disqus](http://disqus.com)评论系统。

`Disqus`优点是：国际比较流行，界面也很大气、简介，如果有人评论，还能实时通知，直接回复通知的邮件就行了；缺点是：评论必须要去注册一个disqus账号，分享一般只有Facebook和Twitter，另外在墙内加载速度略慢了一点。想要知道长啥样，可以看以前的版本点[这里](http://brucezhaor.github.io/about.html) 最下面就可以看到。

`多说` 优点是：支持国内各主流社交软件(微博，微信，豆瓣，QQ空间 ...)一键分享按钮功能，另外登陆比较方便，管理界面也是纯中文的，相对于disqus全英文的要容易操作一些；缺点是：就是界面丑了一点。
当然你是可以自定义界面的css的，详情请看多说开发者文档 http://dev.duoshuo.com/docs/5003ecd94cab3e7250000008 。

**首先**，你需要去注册一个账号，不管是disqus还是多说的。**不要直接使用我的啊！**

**其次**，你只需要在下面的yaml头文件中设置一下就可以了。

```
duoshuo_username: _你的用户名_
# 或者
disqus_username: _你的用户名_
```

**最后**多说是支持分享的，如果你不想分享，请这样设置：`duoshuo_share: false`。你可以同时使用两个评论系统，不过个人感觉怪怪的。

#### Analytics

网站分析，现在支持百度统计和Google Analytics。需要去官方网站注册一下，然后将返回的code贴在下面：

```
# Baidu Analytics
ba_track_id: 4cc1f2d8f3067386cc5cdb626a202900

# Google Analytics
ga_track_id: 'UA-49627206-1'            # 你用Google账号去注册一个就会给你一个这样的id
ga_domain: huangxuan.me			# 默认的是 auto, 这里我是自定义了的域名，你如果没有自己的域名，需要改成auto。
```

#### Customization

如果你喜欢折腾，你可以去自定义我的这个模板的 code，[Grunt](gruntjs.com)已经为你准备好了。（感谢 Clean Blog）

JavaScript 的压缩混淆、Less 的编译、Apache 2.0 许可通告的添加与 watch 代码改动，这些任务都揽括其中。简单的在命令行中输入 `grunt` 就可以执行默认任务来帮你构建文件了。如果你想搞一搞 JavaScript 或 Less 的话，`grunt watch` 会帮助到你的。

**如果你可以理解 `_include/` 和 `_layouts/`文件夹下的代码（这里是整个界面布局的地方），你就可以使用 Jekyll 使用的模版引擎 [Liquid](https://github.com/Shopify/liquid/wiki)的语法直接修改/添加代码，来进行更有创意的自定义界面啦！**

#### Header Image

标题底图是可以自己选的，看看几篇示例post你就知道如何设置了。在
  [issue #6 ](https://github.com/Huxpro/huxpro.github.io/issues/6) 中我被问到：怎么样才能让标题底图好看呢？
  
标题底图的选取完全是看个人的审美了，我也帮不了你。每一篇文章可以有不同的底图，你想放什么就放什么，最后宽度要够，大小不要太大，否则加载慢啊。

但是需要注意的是本模板的标题是**白色**的，所以背景色要设置为**灰色**或者**黑色**，总之深色系就对了。当然你还可以自定义修改字体颜色，总之，用github pages就是可以完全的个性定制自己的博客。

#### SEO Title

我的博客标题是 **“Hux Blog”** 但是我想要在搜索的时候显示 **“黄玄的博客 | Hux Blog”** ，这个就需要SEO Title来定义了。

其实这个SEO Title就是定义了<head><title>标题</title></head>这个里面的东西和多说分享的标题，你可以自行修改的。

## 致谢

1. 这个模板是从这里[IronSummitMedia/startbootstrap-clean-blog-jekyll](https://github.com/IronSummitMedia/startbootstrap-clean-blog-jekyll)  fork 的。 感谢这个作者
2. 感谢[@BrucZhaoR](https://github.com/BruceZhaoR)的中文翻译 

3. 感谢 Jekyll、Github Pages 和 Bootstrap!



