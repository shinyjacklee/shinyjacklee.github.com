---
layout: post
title:  "AndroidStudio 多个module统一gradle文件配置"
date:   2016-08-26 
categories: [Android]
tags: [gradle配置]
---

看到AS中External Libraries有好几个同名但是版本不一样的lib的时候，真的逼死强迫症患者。
这些多个重复的lib出现的原因就是多个module各自compile了同名但是不同版本的lib（即依赖没有统一），所以统一性的确认这些依赖就好了。


### Step1:

在根目录新建一个`config.gradle`文件，里面键入要统一的依赖：

    ext {

    android = [

            compileSdkVersion: 23,
            buildToolsVersion: "23.0.3",
            minSdkVersion    : 15,
            targetSdkVersion : 22,
            versionCode      : 1,
            versionName      : "1.0"

    ]

    dependencies = [
            "gson"               : "com.google.code.gson:gson:2.6.2",
            "eventbus"           : 'org.greenrobot:eventbus:3.0.0',
            "butterknife"        : 'com.jakewharton:butterknife:7.0.1',
            "support-design"     : 'com.android.support:design:24.1.1',
            "support-appcompatV7": 'com.android.support:appcompat-v7:24.1.1',
            "support-percent"    : 'com.android.support:percent:24.1.1',
            "support-multidex"   : 'com.android.support:multidex:1.0.1',
            "glide"              : 'com.github.bumptech.glide:glide:3.7.0',
            "support-v4"         : 'com.android.support:support-v4:24.1.1',
            "okhttp3"            : 'com.squareup.okhttp3:okhttp:3.3.1',
            "nineoldandroids"    : 'com.nineoldandroids:library:2.4.0'


    ]


}

### Step2:

在根目录的`build.gradle`文件里面头部增加一句引用
`apply from: "config.gradle"`

### Step3:

在module里面开始应用：



    compileSdkVersion rootProject.ext.android.compileSdkVersion //android{}节点

    compile rootProject.ext.dependencies["support-appcompatV7"] //dependencies{}节点


### The end 

clean一下去External Libraries看看，是不是还有重复的，如果还有，说明前面config里面的依赖其他地方还有遗漏的，全局搜索一下在同样方式替换一下就好了。

_________

### 参考了的资料：

1. [正确的姿势来优化你的build.gradle](http://chenzhongjin.cn/2016/06/23/%E6%AD%A3%E7%A1%AE%E7%9A%84%E5%A7%BF%E5%8A%BF%E6%9D%A5%E4%BC%98%E5%8C%96%E4%BD%A0%E7%9A%84build-gradle/)

2. [Android Studio中 Gradle 依赖的统一管理](http://lixinwei.me/2016/04/26/AndroidStudio%E4%B8%ADGradle%E4%BE%9D%E8%B5%96%E7%9A%84%E7%BB%9F%E4%B8%80%E7%AE%A1%E7%90%86/)



 



