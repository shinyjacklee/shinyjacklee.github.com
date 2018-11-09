---
layout: post
title:  "SublimeText2快捷键整理"
date:   2015-12-10 
categories: [DevTool]
tag: [shortcut,sublimeText2,Mac]
---
	是的，掌握快捷键是一个开发者最基本的要求。今天我么要掌握的是sublimeText2的快捷键，不光可以提高便携编辑代码抑或文档的效率，也可以让你很专业，不要老是试图点鼠标。

快捷键依据：`Default (OSX).sublime-keymap`，这是在OSX下默认的keymap，这份map是最权威的。如果不够用了，你也可以自定义 。
然后我在Dash里面下了一份快捷键的小抄，无奈总让我等待8秒钟。遂花点时间整理下来吧。

------

> ⚠️： 数据来源[Kapeli/cheatsheets](https://github.com/Kapeli/cheatsheets#readme)

#### Edit 编辑

`CMD+SHIFT+V`
Paste and indent粘贴并缩进

`CMD+]`
Indent缩进

`CMD+[`
Unindent取消缩进

`CMD+CTRL+Arrow Up`
Swap line up**向上换行**

`CMD+CTRL+Arrow Down`
Swap line down**向下换行**

`CMD+SHIFT+D`
Duplicate line**复制行**

`CMD+J`
Join lines拼接行

`CMD+Arrow Left`
Beginning of line**光标跳到行首**

`CMD+Arrow Right`
End of line**光标跳到行尾**

`CMD+/`
Toggle comment**加注释**

`CMD+CTRL+/`
Toggle comment block**加方法注释块**

`CTRL+SHIFT+K`
Delete line**删除行**

`CTRL+K`
Delete to end**删除光标之后**

`CTRL+T`
Transpose


`CMD+ALT+.`
Close tag关闭标签

`CMD+SHIFT+A`
Expand selection to tag

`CTRL+SHIFT+W`
Wrap selection with tag

`CMD+ALT+Q`
Wrap paragraph at ruler

`F5`
Sort lines行排序

`CTRL+F5`
Sort lines (case sensitive)行排序(大小写敏感)

`CMD+ALT+T`
Special characters**特殊字符**
 

-------

#### Selection 选择

`CMD+SHIFT+L`
Split into lines分行

`CTRL+SHIFT+Arrow Up`
Add previous line  
注：此组合键和系统快捷键冲突

`CTRL+SHIFT+Arrow Down`
Add next line  
注：此组合键和系统快捷键冲突

`Esc`
Single selection退出选中模式

Cancel multiple selections取消多选

`CMD+L`
Expand selection to line**选中所在行**

`CMD+D`
Expand selection to words**选中光标旁边单词**

`CTRL+SHIFT+M`
Expand selection to brackets**选中所在方法体**

`CMD+SHIFT+J`
Expand selection to indentation

`CMD+SHIFT+A`
Expand selection to tag  
注：此组合键似乎无效


----------

#### Find 查找

`CMD+F`
Find**查找**

`CMD+G`
Find next**查找下一个**

`CMD+SHIFT+G`
Find previous**查找上一个**

`CMD+I`
Incremental find

`CMD+ALT+F`
Replace**替换**

`CMD+ALT+E`
Replace next**替换下一个**

`CMD+ALT+G`
Quick find快速查找

`CMD+CTRL+G`
Quick find all快速查找所有

`CMD+D`
Quick add next快速增加下一个

`CMD+E`
Use selection for find**查找选中的单词**

`CMD+SHIFT+E`
Use selection for replace**替换选中的单词**

`CMD+SHIFT+F`
Find in files在文件中查找

--------

#### View 视图

`CTRL+` `
Show console显示控制台

`CMD+CTRL+F`
Enter full screen**全屏**

`CMD+CTRL+SHIFT+F`
Enter distraction free mode**内容全屏**

`CMD+ALT+1-4`
Single layout1-4列布局

`CMD+ALT+2-4`
2-4 column layout2-4列布局

`CMD+ALT+SHIFT+2-3`
2-3 row layout行布局

`CMD+ALT+5`
Grid layout格子布局

`CTRL+1`
Group 1第一组

`CTRL+SHIFT+1`
Group 2第二组

`F6`
Spell check**检查拼写**

-------

#### Go to 跳转

`CMD+P`
Go to anything强跳转

`CMD+R`
Go to symbol**跳转到符号处**

`CTRL+G`
Go to line**跳到行**

`CMD+ALT+Arrow Right`
Next file下一个文件

`CMD+ALT+Arrow Left`
Previous file上一个文件

`CMD+ALT+Arrow Up`
Switch header / implementation

`CMD+1`
Go to first file到首行  
注：此组合键似乎无效

`CTRL+L`
Scroll to selection滚动到选中行

`CTRL+ALT+Arrow Up`
Scroll line up光标不动向上滚动

`CTRL+ALT+Arrow Down`
Scroll line down光标不动向下滚动

`CMD+F2`
Toggle bookmark增加书签

`F2`
Next bookmark下一个书签

`SHIFT+F2`
Previous bookmark上一个书签

`CMD+SHIFT+F2`
Clear bookmarks清除书签

`CTRL+M`
Jump to matching bracket**跳转到匹配的括号**

-------

#### Tools 工具


`CMD+SHIFT+P`
Command palette 命令行

`CTRL+ALT+V`
View in browser在浏览器中打开

`CMD+B`
Build**编译**  
注：那就可以直接编译运行C代码啦：）

`CTRL+Q`
Record macro录制宏

`CTRL+R`
Run`运行`

`CTRL+ALT+R`
Run with arguments带参运行

`CTRL+D`
Debug调试

`CTRL+ALT+D`
Debug with arguments带参调试

-------

#### Project

`CMD+CTRL+P`
Switch project window切换工程窗口

--------

但是太多了，常用的或许就那么几个，感觉常用的部分我加粗了。
还有个别补充：

复制光标所在整行，插入在该行之前:`CMD+SHIFT+D`

改为大写`CMD+KU`

改为小写`CMD+KL`

-------

**bing出来的觉得不错的搜索结果：**

- [整理的很好的带GIF图的快捷键](http://blog.jobbole.com/82527/)
- [win下Sublime Text2 常用快捷键](http://www.oschina.net/question/565065_70734)




 




