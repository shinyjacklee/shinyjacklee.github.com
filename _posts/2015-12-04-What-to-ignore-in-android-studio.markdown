---
layout: post
title:  "What-to-ignore-in-android-studio"
date:   2015-12-04 
categories: [Android,git]
tags: [Android Studio,gitignore]
---
Android studio 使用git 来控制版本需要忽略的文件：
经过检索，一般来说通用的如下：

    gitignore.properties
    -------------------
    #built application files编译产生的apk文件等
	*.apk
	*.ap_

	# files for the dex VM编译产生的dex文件
	*.dex

	# Java class files编译产生的字节码
	*.class

	# generated files自动产生的文件
	bin/
	gen/

	# Local configuration file (sdk path, etc)本地配置文件
	local.properties

	# Windows thumbnail Windows的文件
	Thumbs.db

	# OSX files OS X的文件
	.DS_Store

	# Eclipse project files  
	.classpath
	.project

	# Android Studio
	*.iml
	.idea
	#.idea/workspace.xml - remove # and delete .idea if it better suit your needs.
	.gradle
	build/

	# Log Files
	*.log
	
	#NDK
	obj/
	


还有一个自动生成的站点[gitignore.io](https://www.gitignore.io/),好像很厉害的样子。

一句话就是，需要ignore什么文件，那么就把它加入到ignore，我把`appcompat_v7`这样的也忽略了，详细的参考廖雪峰大大的解释。


>参考资料：

[1.What should be in my .gitignore for an Android Studio project?](http://stackoverflow.com/questions/16736856/what-should-be-in-my-gitignore-for-an-android-studio-project)

[2.liaoxuefeng's blog](http://www.liaoxuefeng.com/wiki/0013739516305929606dd18361248578c67b8067c8c017b000/0013758404317281e54b6f5375640abbb11e67be4cd49e0000)

[3.Android Studio中gitignore编写](http://www.bubuko.com/infodetail-918029.html)