---
layout: post
title:  "ssh-and-git-account"
date:   2018-01-31 
categories: [git]
---


多设备免登陆和多账号在不同项目中自动切换配置。

### 1.多台电脑提交代码的场景
> 在公司的时候，需要提交代码到GitLab上的repo；然后在家的时候，有时候也需要提交代码到公司项目中。那么push pull的时候一直输入用户名密码就比较费事了。

那么[使用ssh的方式](https://help.github.com/articles/connecting-to-github-with-ssh/)就可以解决上面这个问题。

上面的超链接，提供了如下几点：

 1. 什么是ssh
 2. 检测已经存在的ssh Key
 3. 生成新的ssh Key并添加到ssh agent中
>  一般来说我们实际场景会需要生成两种，自己项目需要使用一个 id_rsa_github，公司项目需要使用一个 id_rsa_work。这样子，提交到不同repo的时候，才会有不同的用户名。

 4. 检测是否成功
 5. 使用ssh工作

> ⚠️一定要做第四步的添加到agent中
### 2. 多个Repo提交的时候，使用不同的用户名
自己在GitHub上有项目需要维护，公司的项目也是用GitLab协作维护的，那么有时候在家用自己的电脑提交代码到公司，于是就产生需要在不同的项目应用不同`user name`的需求了；
> 简单说，我在公司提交代码里面的用户名需要是RealName；而提交代码到GitHub的时候，想要用NickName

这里涉及到的就是 `git config --global ` 还是`git config --local` 的问题

    cd  testRepo
    git config --local user.email personal@example.org
    git config --local user.name "whatf hobbyist user name"

> ⚠️email地址不需要 双引号，而 用户名是需要的

参考资料：

1.[Can I specify multiple users for myself in .gitconfig?](https://stackoverflow.com/questions/4220416/can-i-specify-multiple-users-for-myself-in-gitconfig)

2.[多个git账号之间的切换](http://happy123.me/blog/2014/12/07/duo-ge-gitzhang-hao-zhi-jian-de-qie-huan/)






> Written with [StackEdit](https://stackedit.io/).

 



