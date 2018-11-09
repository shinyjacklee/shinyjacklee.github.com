---
layout: post
title:  "Android studio 快捷键 Mac OS X 10.5+"
date:   2015-12-03 
categories: [DevTool]
tags: [Android Studio,shortcut,Mac]

---
    首先上一遍高频的符号和对应的键位

  - ⌥—> option/alt 
  - ⇧—>shift 
  - ⌃—>control 
  - ⌘—>command 
  - ⎋—>esc 


----------
对于IDE来说，掌握其快捷键是基本的要求，下面整理一下平时用的比较多的keyMap。

1. 返回上一次所在  ⌘＋[ ,去下一次所在⌘+]
3. 查找当前类里面方法 ⌘ F12
5. 找调用者⌥ F7,跳到调用处 ⌘ ⌥ F7 
5. 写一个功能打开多个类和布局文件，tab间直接切换，用 ⌘＋⇧＋］or[
5. 整行上下移 ⇧ option +上下 
5. 自动生成get() set() 方法 ⌘ n
6. 类层级：⌃h ，这个可以清晰看层次Hierarchy,类似于XML里面的ComponentTree一样。
8. 在当前project(一个project可以含多个moudle)中搜索class：⌘o
    再按一次⌘o，搜索结果可包含非project中的class，如external libraries中的android.jar里的class
    可以在搜索文本后跟:lineNumber   从而定位到某行
9. 在当前project中搜索file(包含上面的class结果)：⌘⇧o
    再按一次⌘⇧o，搜索结果可包含非project中的flie，如external libraries中的res里的file
    可以在搜索文本后跟:lineNumber   从而定位到某行
10. 在当前project中搜索file(包含上面的class、file结果及method) ⌘⌥o
11. 如eclipse中的⌘1的action(即win上的ctrl+1)：⌥⏎    即alter+enter (需要光标移动到分号之前，可以在代码内容里，当该代码行下标红时)
13. 如eclipse中的⌘o(查看当前类成员):     ⌘f12， 显示内部成员
      ⌘i 显示/取消息匿名类
      ⌘f12 显示继承自父类、父接口的成员
14. 选择能重写(override)或实现(implement)的方法 ：⌃o
16. 关于加上javadoc的快捷键 ，这个需要手动设置一下：
cmd+ ,  进入首选项，然后输入关键词 keymap , 然后搜索comment，找到other下面的fix doc comment ,选中它，两手指点击一下，就出现了上下文菜单，add keyboard shortcut ,就可以设置你喜欢的键位了，对应的是eclipse里面用的shift ＋alt＋ j   [参考](http://www.xuebuyuan.com/2035619.html)
然后就可以这样了：

    
        /**
         * @return 你的注释
         */
        public String method() {
        return "hello world";
    }

16. ⌘j ：快捷代码片段
      psf => public static fina 
      ifn => if (a == null)
      inn=> if (a != null)
     fori=> for(int i = 0; i < .....)
     I(大写i)=> for(Object o : ) 
    ..... 其它 
17. shift+option+c, 打开as里面改动过的文件，点击进去就可以看到每次改动了；
我自己用的时候感觉还不如直接在git checkout 好使，如果还想看一下具体改动的地方，我是用了GitHub Desktop客户端看的。
18. 把代码封到方法method里面，方法名在弹出的对话框种设置option cmd M
19. Eclipse 里面寻找同个变量CTRL＋K，在as里面是光标选中变量，然后cmd F,查找之后是cmd G 慢慢跳到本类改变量处。
20. 快速打开Terminal： option＋F12，再按一下就关闭了。
21. 如果再报错平台上看到了报错在哪一个类的那一行，cmd+L直接输入行数就直接去了。

---------- 

___详细版本:___
   
__Code__

- alt+F7：找使用的地方 
- alt+command+L：格式化代码 
- alt+command+O：优化import（去掉无用的import） 
- command+O：Override Methods 
- command+I：Implement Methods 
- command+B：Declaration查看定义 
- alt+command+B：Implementations查看其实现 
- command+U：Super Method（Class） 
- control+上下方向键：Previous/Next Method 
- (shift+)F2：快递定位并高亮错误（deprecate，unused） 
- command+Z：Undo撤销 
- shift+command+Z：Redo Typing 
- **alt+enter：引入包，添加注释**
- control+enter：generate setter，getter… 
- shift+command+T：添加Test 
- command+W：Extend Selection 
- shift+command+W：Shrink Selection 
- command+P：参数提示 
- command+Y（X）：删除当前行（剪切当前行） 
- command+F11：添加/取消bookmark 
- shift+F11：显示bookmark列表 
- command++/-：展开收缩代码 
- shift+command+上下方向键：Move Line Up/Move Line Down

__Search__

- command+F：Find 
- command+R：Replace 
- control+shift+F：Find in Path 
- control+shiftÏ+R：Replace in Path 
- alt+command+左右方向键：Back/Forward操作 
- command+E：Recent File 
- shift+command+E：Recently Change Files 
- shift+shift：Search Method或者Class (Search Everywhere：command+N,shift+command+N,shift+alt+command+N) 
- command+N：Search Class 
- shift+command+N：Search File 
- shift+alt+command+N：Search Symbol

__Run/Debug__

- shift+F10：Run 
- shift+F9：Debug 
- command+F9：Make Project 
- shift+command+F9：Make Module 
- command+F2：关闭当前的执行的task 
- command+F8：添加/取消断点 
- shift+command+F8：查看所有断点 

__Debug__

- F7：Step Into 
- F8：Step Over 
- shift+F8：Step out 
- F9：resume 
- alt+F9：Run to Cursor

__Refactor__

- shift+F6：重命名 
- command+F6：快速修改函数的参数，返回值或者类添加泛型等 
- F6：Move快速的移动方法或者类 
- F5：Copy快速的移动类 
- alt+command+C：提取Constant变量 
- alt+command+V：提取Variable（Local变量） 
- alt+command+F：提取Field变量 
- alt+command+M：提取Method

__Setting__

- command+，：Android Studio Preferences 
- command+；：Project Structure

----------
再来一次OS X符号

- ⌥—> option/alt 
- ⇧—>shift 
- ⌃—>control 
- ⌘—>command 
- ⎋—>esc 


首次从大Win切换过来除了快捷键的困扰之外，还有看不懂的符号，参考下面这就get√了，还是对ctrl和⌘有阴影，虽然只是理解了option ＝＝alt .

>  [认识Mac 的键位和符号](http://softu.cn/457)







