---
title:  "项目的版本控制."
subtitle: "A Beautiful shot during the night."
author: "ZJT"
avatar: "img/authors/wferr.png"
image: "img/g.jpg"
date:   2018-12-1
---

###1. 版本控制
what 什么是版本控制
    why 为什么要用版本控制
    how 怎么用版本控制
什么是版本控制
 版本控制是一种记录一个或若干文件内容变化，以便将来查阅特定版本修订情况的系统.

why 为什么要用版本控制
你可以比较文件的变化细节，查出最后是谁修改了哪个地方，从而找出导致怪异问题出现的原因，又是谁在何时报告了某个功能缺陷等等。
使用版本控制系统通常还意味着，就算你乱来一气把整个项目中的文件改的改删的删，你也照样可以轻松恢复到原先的样子。 但额外增加的工作量却微乎其微.


 how 怎么用版本控制?
     版本控制系统有三大类:
        1. 本地版本控制系统
            优点: 快速备份,无需经过大脑
            缺点: 
                1. 占硬盘空间
                2. 当版本较多的时候.不方便查找对应版本
                3. 无法协作开发,大大影响开发的效率
        2. 集中式版本控制系统
            1.减少硬盘空间的占用
            2.可以协作开发,提高开发效率
            缺点:
                1. 单点故障,导致无法协作开发
                2. 数据有可能全部丢失
        3. 分布式版本控制系统
            git



### git 的使用
1. 下载git for window 
2. 第一次使用必须配置
     配置用户名 git config --global user.name "mengtuo"
     配置邮箱地址 git config --global user.email "mengtuo@outlook.com"
     查看配置结果
     git config --list

git的三种状态
    1. 已修改,表示在上次提交新的版本之后,又重新对代码进行了编写
    2. 已暂存,将已经修改过的文件,但是又没有马上提交保存到数据库的文件,放到暂存区域内,等待提交
    3. 已提交,文件所有信息都已经提交保存到数据库中.并且形成一个新的版本

三种状态对应的三个目录
    1.已修改->  工作目录
    2.已暂存->  暂存区域->文件列表,
    3.已提交->  版本数据库区域 -> 就是git仓库,存有完整代码的仓库


3. git的使用
    1. git init //初始化git仓库
    2. git add *  //跟踪文件
        git status 暂存区域的状态
    3. git commit -m "版本描述"  --提交

4. 查看提交的历史版本信息
 git log
    <!-- HEAD是指针,表示提交的时候是在主分支进行提交的 -->
    commit fb29b0649bb2af163d66f75b910326b5879a31ed (HEAD -> master) 哈希值是历史版本的唯一身份信息,可以通过该值来跳转到指定的版本或者是回溯到指定的版本
    Author: mengtuo <mengtuo@outlook.com> //作者以及联系方式
    Date:   Thu Nov 22 15:31:49 2018 +0800 //上传日期

优化显示的版本信息
git log --pretty=oneline

fb29b0649bb2af163d66f75b910326b5879a31ed (HEAD -> master) 新增test.txt文件
f43900b3578c4b72821ceb21aa6c24adf9524cef 首次提交

5. 版本回退
由于版本回退是不可逆的操作,有可能会导致你回退的版本到最新版本之间的所有版本都会丢失,所以,要慎重.
git reset --hard f43900b3578c4b72821ceb21aa6c24adf9524cef
    
6. 撤销操作
git checkout -- 要撤销操作的文件

7. 从暂存区域中移除已跟踪文件
git rm -r --cache 需要移除跟踪的文件名

8. 忽略文件,新建 .gitignore 文件,在该文件内添加要忽略的文件或者目录
    node_modules/  忽略node_modules下的所有文件
    test.js //直接忽略指定文件