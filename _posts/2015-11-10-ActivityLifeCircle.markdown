---
layout: post
title:  "Activity生命周期和启动模式"
date:   2015-11-12 
categories: [Android]
tags: [Activity,生命周期]
---

1.关于生命周期

	1.1 Activity生命周期 ? 处理任务？

	* onCreate()做一下初始化工作，包含界面和数据
	* onRestart()一般是Home键回去的时候，生命周期是onPause()->onStop()->onRestart()->onResume()
	* onStart()是正在启动，还未可见
	* onResume()是可见了
	* onPause()正在停止，正常情况下onStop()紧接着会调用，此时可以做一下存储数据停止动画。但是不能太耗时。因为会影响下一个Activity的显示，可以在onStop()里面。
	* onDestroy()即将销毁，做回收工作和资源释放。

在配置变化和内存不足情况下，系统配置发生变化 ，屏幕旋转了等，在onSaveInstanceState()和onRestoreInstance State()里面做View的保存和恢复操作。**这个方法只会在异常停止的情况下出现，正常不会回调的。**


	*数据保存的时机*

一般在onPause做短时的数据存储，停止动画，在onStop()做稍微耗时的。
onDestory()释放资源等。

2.关于启动模式

	1.1 几个启动模式，区别

	* standard每次都会new,默认进去启动他的Activity的栈中，但是如果是以application为context的时候，要加个FLAG_ACTIVITY_NEW_TASK，因为application是没有任务栈的
	* singleTop栈顶复用
	如果栈内是ABCD，新加D(singleTop模式)则为ABCD，会调用D的onNewIntent() But D的onCreate() onStart()不会调用
	如果是standard标准模式，那么就是ABCDD.
	* singleTask栈内复用
	__singleTask默认自带clearTop__，对应flag是NEW_TASK|CLEAR_TOP; 
	如果是ADBC，然后新加D(singleTask模式)，那么栈会是AD，这点比较特殊。
	* singleInstance单独在一个栈内，整个周期单例。

	1.2 Activity的Flag

	* NEW_TASK---singleTask
	* SINGLE_TOP---singleTop
	* CLEAR_TOP清理掉上面所有的
	* FROM_RECENTS不会加到历史任务栈中

3.关于IntentFilter的匹配规则

 显示和隐式

 action ，category，data










 



