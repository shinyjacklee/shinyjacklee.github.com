---
layout: post
title:  "mipmap VS drawable"
date:   2016-04-28 
categories: [Android]
tag: [mipmap]
---

	mipmap/到底是怎么用的？drawable和它有什么区别么？

>纸上得来终觉浅，绝知此事要躬行

最近在处理一个OOM问题的时候，发现了我们用错了mipmap,正确的用法：

__简单讲，mipmap/不是为了替代drawable/而出现的，它是为`app launcher icons`显示问题做了优化，也就是安装好了之后在桌面上的那图标。而其他的图片资源，老实的放在相应的drawable/下面。__


1.关于文件夹的解释
--

> - drawable/
			For bitmap files (PNG, JPEG, or GIF), 9-Patch image files, and XML files that describe Drawable shapes or Drawable objects that contain multiple states (normal, pressed, or focused). See the Drawable resource type.
- mipmap/
For app launcher icons. The Android system retains the resources in this folder (and density-specific folders such as mipmap-xxxhdpi) regardless of the screen resolution of the device where your app is installed. This behavior allows launcher apps to pick the best resolution icon for your app to display on the home screen. For more information about using the mipmap folders, see [Managing Launcher Icons as mipmap Resources.](http://developer.android.com/tools/projects/index.html#mipmap)


上面关于项目结构的解释里面明确了两个文件夹的区别：

- drawable/
 放bitmap文件( PNG ，JPEG，或者 GIF)，`.9`图片以及XML文件(那些DrawableShape或者含有普通，按下，获取焦点状态的Drawable 对象)。
- mipmap/ 
 放应用启动的icon图标。不管你的app安装在哪个分辨率的设备,Android 系统保留了这些资源(还有对应特定的密度的文件夹如mipmap-xxxhdpi)在mipmap文件夹里面。这样launcher应用可以选择最佳分辨率的icon显示在home 界面上。更多关于使用mipmap文件夹的信息，参考[ Managing Launcher Icons as mipmap Resources](http://developer.android.com/tools/projects/index.html#mipmap),也就是下面第二点。
 
2.Managing Launcher Icons as mipmap Resources
--

>Different home screen launcher apps on different devices show app launcher icons at various resolutions. When app resource optimization techniques remove resources for unused screen densities, launcher icons can wind up looking fuzzy because the launcher app has to upscale a lower-resolution icon for display. To avoid these display issues, apps should use the mipmap/ resource folders for launcher icons. The Android system preserves these resources regardless of density stripping, and ensures that launcher apps can pick icons with the best resolution for display.

>Make sure launcher apps show a high-resolution icon for your app by moving all densities of your launcher icons to density-specific res/mipmap/ folders (for example res/mipmap-mdpi/ and res/mipmap-xxxhdpi/). The mipmap/ folders replace the drawable/ folders for launcher icons. For xxhpdi launcher icons, be sure to add the higher resolution xxxhdpi versions of the icons to enhance the visual experience of the icons on higher resolution devices.
>>Note: Even if you build a single APK for all devices, it is still best practice to move your launcher icons to the mipmap/ folders.

不同设备上的不同launcher应用显示icon的分辨率是不同的。当app的资源优化技术去掉了不用的分辨率的资源的时候，启动icon最后会看起来模糊，因为有时候会放大一个低分辨率的icon来显示。为了避免这样的显示问题，apps应该使用mipmap/资源文件夹来放icons.Android系统会保存这些资源，不会应用密度去除策略，这样就保证了launcher应用可以选择最佳分辨率的icon显示在home 界面上（因为mipmap文件夹里面的资源没有被优化技术去除掉）。

确保各个密度的icon放到对应密度的文件夹下，像`res/mipmap-mdpi`和`res/mipmap-xxxdpi`__，mipmap/下的文件夹会替换drawable/下面的对应的资源的icon的。对于xxhdpi的icon，确定把xxxhdpi版本的icon放进去，来保证在分辨率更高的设备上更好的视觉体验。
⚠️即使你已经build好了一个适用所有设备的APK，最佳实践还是把你的icons移动到mipmap/对应的文件夹下面。

______

#### 最后结论：
__mipmap/不是为了替代drawable/而出现的，它是为了解决`app launcher icons`显示问题做了优化，也就是安装好了之后在桌面上的那图标。而其他的图片资源，老实的放在相应的drawable/下面。__


参考资料：
[developer.android.com](http://developer.android.com/tools/projects/index.html#mipmap)

 



