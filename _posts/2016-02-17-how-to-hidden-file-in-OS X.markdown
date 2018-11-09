---
layout: post
title:  "How to hide and unhide file in OS X"
date:   2016-02-17
categories: [DevTool]

---
	之前在大win下面，做点小花样扰乱一下来达到隐藏某些文件，比如帐号的密码还是很有效果的。可是切换到OS X的时候，发现没有这个选择啊。
搜了一下，不是让你装某软件就是告诉你哪里有破解版 : (

果断Google了下，找到了符合需求的方案：不用安装什么软件，如何隐藏和取消隐藏文件(夹)。
直接`terminal`啦 ：）

对于某个文件：
--
- 隐藏
  > chflags hidden [file path]
- 显示
  > chflags nohidden [file path]
 
 ⚠️:
1. [filePath]就是目标文件的路径，直接敲出前面命令，然后拖拽文件到`terminal`就有了。
 2. 这里命令行是 __nohidden__ not _unhidden_! 
对于所有隐藏了的文件：
--
- 显示所有隐藏文件(夹)
> defaults write com.apple.finder AppleShowAllFiles FALSE
   killall Finder
- 隐藏所有文件(夹)
 > defaults write com.apple.finder AppleShowAllFiles TRUE
   killall Finder
⚠️ `defaults` 不要忘了 `s`


1. switch hide or not 
 - hide file 
 > chflags hidden [file path]

 - unhide file
 > chflags nohidden [file path]
 >ps.it is `nohidden` not `unhidden` ! 

2.  switch show all hidden files
 - show all hidden files in finder:
 > defaults write com.apple.finder AppleShowAllFiles FALSE
   killall Finder

 - do not show hidden files in finder:
 > defaults write com.apple.finder AppleShowAllFiles TRUE
   killall Finder
 ps. it is `defaults` ,do not forget the `s`


[sourcePage](http://www.howtogeek.com/211496/how-to-hide-files-and-view-hidden-files-on-mac-os-x/)


