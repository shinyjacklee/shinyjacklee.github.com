---
layout: post
title:  "My Software Kit for Android Developing"
date:   2015-12-16 
categories: [工具,Android]
tags: [开发环境]
---

  整理出开发环境搭建 _2015/12/16_

  Update:整理记录详尽点的工作环境 _2016/5/3_

____

#### 一个Android开发的工具箱
  
- 基本开发环境

  1. `JDK`
  
  2. `AndroidStudio`

  _附件： AS里面效率工具插件：_

  - ButterKnife 不喜欢写很多的findViewById就用这个注解吧
  - GsonFormat 配合GSON很好很强大的工具，节省一杯咖啡的时间
  - Fabric twitter出品的免费强大的crash日志收集系统
  - _loading..._


- 必需的工具

  1. `chrome`，如果你喜欢`FireFox`也不错。
  chrome下面强大的插件生态，收藏夹等特性，无疑开发者最友好的浏览器，没有之一。
  _附件：我的chrome插件_
  - JSON格式化工具`JSON-handle`。
  - 打开很多网页，觉得都挺好的，又不想关闭，可是内存爆了，那么试试`OneTab`，可以一键把当前所有page收藏折叠保存起来,支持一键恢复等。
  - 老牌的网页调试发送请求的工具`PostMan`，说到这个得提一下抓包工具了，我在win下用的是`Fiddler`,OS X 下推荐`Charles`，均属神器。
  - Android手机直接在PC端调试？不想每次低头按手机？ 试试`Vysor`插件吧。
  - Proxy Switchy# always online...
  - Octotree,每次浏览Github的时候路径比较深，想回退到上上一层页面要返回两次，用了这个神器，可以一次跳转了。
  - Adblock Plus,恼人的广告再见。
  
  2. SQL数据库查看工具：
我在win下用的是`SQLExpert`，在OS X下用的是`SQLite Free Datum`。至于导出手机里面自己的数据库，AS里面已经换到`Android Device Monitor`了，不要试图找什么`DDMS`了,然后就是`File Explorer`旁边就是你喜欢的小按钮，导入导出。

  3. 版本控制系统VCS(Version Control System)：
    - `GIT`，我在win里面是有两个的，一个是`gitHub`,还有一个是gitHub `shell`,就是命令行工具，在OS X下安装的时候，可以自己勾选一下，同时安装shell工具。安装好了之后as里面可以直接上terminal，挺方便的。
    - 如果你喜欢`SVN`，我在win下用的是`tortoiseSVN`，然后在eclipse里面用了一个`subClipse`这个插件，就可以在`eclipse`里面直接push pull了。
  4. 文档阅读:
嗯，我一直以为搞开发的看文档都会用`Dash`的，appStore搜索一下，真神器，各种语言的API文档还有编辑器等快捷键，还有比如SQL语句的小抄。
然后高级点的，`sourceInsight`，还有我的朋友推荐的`atom`。
  4. 文本编辑器：
   - ` SublimeText` 因为学习成本相对于`vim`或者`emacs`不是很高，然后各种语言支持，时不时的改点C代码又不想安装很重的IDE，有了sublimeText直接CMD＋B编译，然后再加个shift就运行了，`UltraEdit`要key的，估计也不错吧。
   - `Notepad++`代表的简单编辑器。
   - 笔记本－印象笔记`Evernote`等。
  5. <s>` Eclipse Mars` ,学习`JAVA8`需要。</s>
    `IntelliJ IDEA` 由于快捷键切换的成本，不再推荐eclipse了，因为AS基于IDEA开发的，所以默认的快捷键是基本一样的，so写java的话用更智能的idea吧。
  
  6. 虚拟机：
    - `Genymotion` ，Eclipse年代受过AVD折磨的人都知道的神器。
    - `VirtualBox`不解释，你喜欢的话，`VMware Workstation`也行。
    
  8. 团队协作IM工具，`EIM`，`Slack`,还有你的`Wechat`  之类的 。
  
  9. 保护眼睛，`F.lux`,这个工具在随着时间推移改变屏幕亮度颜色，晚上的时候光比较昏黄柔和，iOS9.3里面新增的那个`Night shift`就是类似这个功能的。
  
  10. 修改Mac的F1 F2这样的功能键。写代码的时候热键F系列总是背占用，很恼人，那么改回来吧。［System preferences］-[keyboard]- 勾选上讲F1，F2等作为标准功能键，热键F5等就解放出来了。
  
  11. 效率管理工具，推荐`OmniPlan`（感谢我的朋友OKernel慷慨的赠予），这个是收费的，你也可以在chrome里面安装一个番茄钟插件。
  
  12. 录屏小工具，推荐`LiceCap`,
  这个软件可以把视屏录制成GIF格式，然后拖拽到chrome就可以打开了。如果有录制手机的需求，无疑AndroidStudio里面提供的屏幕录制功能挺好的，路径在AS-Android Monitor-然后找到小相机下面的就是了，and这个是直接录制成Mp4格式的。
  但是因为Github里面还有QQ里面支持GIF直接播放，所以我一般录制好了都会用chrome播放一下，同时用liceCap再录制一下转成GIF的。
  
  14.  如果有需要和产品设计沟通，或者自己取色之类的，可能需要`sketch(OS X only)`,`Axure`,`photoshop`等 。
  
  
#### 总结
 JDK AS Chrome SQL GitHub SublimeText IntelliJ IDEA Genymotion VirtualBox Slack Evernote Flux OmniPlan LiceCap Sketch

__The end__
   

