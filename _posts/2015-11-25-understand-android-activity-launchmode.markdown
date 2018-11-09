---
layout: post
title:  "理解Android启动模式"
date:   2015-11-25 
categories: [Android]
tags: [LaunchMode,Activity]
---
Activity是Android系统最杰出的组件之一,从Activity众所周知的在允许多任务在绝大多数手机运行良好的内存管理方面的良好架构可以看出来了。

不管怎么说，Activity不只是简单的在屏幕上显示，它如何启动也是一个值得考虑的问题。这个话题有很多细节，其中一个相当重要的点就是Activity的启动模式，这就是我们今天在这篇博客要讨论的。

每个Activity做不太一样的任务。有些Activity被设计成使用Intent来独立完成任务的，比如一个邮箱客户端里面编辑邮件的Activity；然而还有些是要单例运行的，比如这个客户端的收件箱Activity。

所以指定一个Activity是否要重新创建还是使用已经存在的实例这个问题就比较重要了，否则就会出现比较差的用户体验或者功能问题。感谢Android的核心 的开发工程师，在特别设计的启动模式的帮助下我们就可以容易的完成这个需求了。

___指定一个启动模式___
我们可以在AndroidManifest.xml文件里的<activity>标签内直接指定一个下面的属性：

    
    <activity
            android:name=".SingleTaskActivity"
            android:label="singleTask launchMode"
            android:launchMode="singleTask">



一共有四种可用的启动模式，我们依次来看吧。

1.__standard__

这是默认的。

设置这个standard模式的Activity将会每次新建个发送单独Intent工作的Activity。想象一下，如果发送了十个写邮件的Intent那么就会启动十个Activity来单独处理每个Intent。结果就是设备上会启动无限个那种Activity。

- 在Android pre-Lollopop版本中
这种Activity会被创建并放置到发送Intent的Activity的栈的栈顶。

当我们分享一个图片到一个standard的Activity。新的Activity会被放到启动这个Activity的栈里面，即使是它们是属于不同的应用。你在TaskManager里面会看到这个，或许有点奇怪。

如果我们把这个应用切换到另外一个，然后在返回Gallery，我们依然可以看到那个standard模式启动的Activity处于Gallery的task中。那么如果我们要对Gallery做一些处理就需要先结束那个增加的Activity。

- 在Android Lollipop版本中

如果是同一个应用的Activities，会和在pre-Lollipop版本一样，新的Activity放在task栈顶。
但是如果启动的Intent是另一个不同的应用发送的话，新的Activity会新开一个task栈。
这个是因为任务管理器系统在lollipop版本的时候修改得更好更有意义。在lollipop版本你可以直接返回Gallery因为他们在不同的task。你也可以发送另外一个Intent，一个新的Task会像之前的一样被创建来服务这个Intent。

这种Activity的例子就是邮件编辑Activity或者是社交应用里面发布新状态的Activity。如果你需要一个Activity单独为每个Intent服务，就可以想想这个standard模式。

2.__singleTop__

接下的模式就是singleTop模式。它几乎和standard模式一样，这意味着singleTop模式的Activity实例可以创建我们想要的次数。唯一的区别就是，如果已经有一个该Activity实例并且已经在启动它的Activity的Task的栈顶，那么就不会创建出这个Activity实例,那么会通过onNewIntent(）方法发送Intent到这个已经存在的Activity实例。

所以在singleTop模式下，你需要处理来自onCreate()和onNewIntent(）方法的Intent，这样应用才会在各种情况下都运行良好。

其中一个使用singleTop模式的示例就是搜索功能。让我们想象一下，创建一个可以引导到SearchActivity看搜索结果的搜索框，为了更好的用户体验，一般来说我们也会一直将这个搜索框放在搜索结果页，这样用户要再搜索其他的就不需要按下返回键了。

如果我们一直为每个新的搜索结果启动一个新的SearchActivity，十次搜索就会有十个新的Activities，如果要返回你就得返回十次才能到你的根Activity，这将会是非常奇怪的事情。

如果在栈顶有了一个SearchActivity，我们最好可以发送一个Intent到这个已经存在的Activity实例然后让他更新一下搜索结果。那么现在就会只有一个SearchActivity在栈顶，你可以只要返回一次就能回到之前的Activity了，这样才讲的通。

不管怎么说，singleTop模式只在调用者同一个task内有效。如果你希望一个发送一个Intent启动一个在其他task中处于栈顶的已经存在的Activity实例，恐怕你要失望了，singleTop无法那样使用。为了防止其他的应用发送一个singleTop模式的Activity过来，一个新的Activity会以standard模式启动（在pre-Lollipop版本放置到了调用者的Task栈，在Lollipop会新建一个新的Task，如上所述）。

3.__singleTask__

这个模式和standard以及singleTop模式有很大的不同，singleTask模式的Activity在系统中只允许有一个实例（也可以说，单例模式）。如果在系统中已经有个singleTask模式的Activity实例存在，该实例所在的Task栈会被移动到顶部，Intent会通过onNewIntent()发送过来。否则一个新的Activity会在合适的Task中被创建。

- 在同一个应用里
如果在系统里尚没有那个singleTask模式的Activity实例存在，就会在同一个Task中创建一个新的Activity并置顶。
但是如果已经存在那个实例的话，那么所有置于那个singleTask模式的Activity都会自动以合适的方式（生命周期里面触发）被销毁掉，这样那个我们想要的Activity就会出现在栈顶了。同时，一个Intent将会通过可爱的onNewIntent()方法被发送到这个singleTask模式的Activity。

或许在用户使用过程中好像讲不通，但是它就是那样设计的。。。

在文档中你或许会发现一件事说：
>The system creates a new task and instantiates the activity at the root of the new task.
但事实看来，并不是文档描述的那样。我们可以从dumpsys activity命令看出来 ，一个singleTask模式的Activity依然会置顶于Task的Activity栈。
如果你希望让一个singleTask的Activity像文档描述的那样，那么就新建一个Task，然后把放一个Activity到里面作为root的Activity。你需要像这样指定taskAffinity属性到这个singleTask的Activity中：

    
    <activity
            android:name=".SingleTaskActivity"
            android:label="singleTask launchMode"
            android:launchMode="singleTask"
            android:taskAffinity="">

是否需要Activity使用taskAffinity就是你的工作了。

- 和其他的应用一起使用

一旦有来自其他应用的Intent发送过来，并且系统里面尚没有任何Activity实例，新的Task会被创建，并且会有新创建的Activity放在里面作为rootActivity。
除非这个应用的一个Task里面已经存在这个调用singleTask模式的Activity,那么就会新建一个新的Activity在这个Task的栈顶。
如果在任何Task里面已经有一个这样的Activity实例，整个Task会被置顶，每个在栈里面处于这个singleTask模式的Activity上面的Activity会在生命周期里面被回收。如果返回按钮被按下了，用户在回到调用的Task时就需要穿过所有那个栈里面的Activities。

这个模式的示例就是任何邮件客户端的收件箱或者说社交产品的时间线（编者按：QQ里面叫时光轴）。这样的Activity设计成不可以有多个实例，singleTask模式能很完美的实现这个需求。不管怎么说，这个模式需要很机智的使用，因为其他的Activities可能会在用户不知情的情况下被回收，就像上面描述的一样。

4.__singleInstance__

这个模式和singleTask有点类似，只有一个Activity实例会存在系统中，而区别就是，存放singleInstance模式的Task栈只能放一个Activity，就是这个singleInstance的Activity。如果其他的Activity被这种（singleInstance模式）Activity调用，一个新的Task会自动创建来放新的Activity。同样的，如果调用了singleInstance模式的Activity，就会创建一个新的Task来放这个Activity。

不管怎么说，结果是有的奇怪的。dumpsys命令提供的信息看来，系统里面会有两个Task，但是只有一个Task出现在了任务管理器，这个取决于哪个是最后一个置顶的。结果就是，尽管后台还有一个Task正在工作，但是我们不能返回到前台，这一点讲不通。

这就是当一个singleInstance模式的Activity被调用然而栈里面已经有些其他的Activities的时候发生的事情了。但是在任务管理器里面看确实只有一个Task。

因为这个Task里面只能有一个Activity,我们不能切换回Task#1了。要实现这个需求，我们就只有从launcher重新启动这个应用，但这样的话这个singleInstance的Task会被隐藏在后台了。

当然了，这个issue还是有方法解决的，就像我们在singleTask Activity里面做的，简单的在这个singleInstance的Activity实例指定一个taskAffinity属性，这样在任务管理器里面就能多任务了。这个模式使用的比较少，应用的示例就是Launcher的Activity或者是你百分比确定只有一个Activity的应用。我建议如果不是万不得已，别使用这个模式。

___Intent Flags___
除了在AndroidManifest.xml文件中直接指定启动模式之外，我们也可以通过称作IntentFlags的机制赋予更多的行为，比如说，

Intent intent = new Intent(StandardActivity.this, StandardActivity.class);
intent.addFlags(Intent.FLAG_ACTIVITY_SINGLE_TOP);
startActivity(intent);

这样会启动一个有singleTop启动模式的叫做StandardActivity。你可以试试，有很多这样的的Flags，在Intent里面可以发现很多。
希望这篇文章对你有用 :)

[source](http://inthecheesefactory.com/blog/understand-android-activity-launchmode/en)

























 



