---
title: 如何搭建自己的BLOG
published: 2025-11-05
description: '这个页面的由来与方法'
image: ''
tags: []
category: ''
draft: false 
lang: 'zh_CN'
---
## 什么是博客？
博客是技术佬发文章的、分享感悟的——“秀肌肉”。招聘时如果能展示一下个人博客或许会有不错的效果。它也可以是私人的“朋友圈”，通过友链与其他人的博客相连。

对于还未接触过项目的工科新生来说，搭建个人博客就可以是你的第一个项目，从中学习一些基本的项目层级常识、Git基本操作等。

## 博客的大致分类
- 第一类是在平台发博客，界面自定义程度较低，就只能发发文章、图文之类的，但大众都能接触到。（csdn,博客园，Xlog，掘金等）
- 第二类是完全自制的博客网站，通常美观程度高，包含前后端，但一般很难接触到，比较私人化。
- 第三类就是利用他人制作的模板来做自己的博客网站。在前人基础上建，制作花费时间较少；仍有很高的自定义空间。

## 搭建教程
### 说明
本人找了网上的一些学习教程，在过程中处处碰壁，一直搜素问题，解决问题，最终得以完善搭建了一个自己觉得颜值还可以的。在使用过程中通过VSCODE编辑，与github的库相连，直接上传。下面的 讲述/记录 都是自己的一步一步的流程。
### 1.创建github仓库
- 如果你没有github账号，那么需要注册一个，相关教程自己去搜素一下
- 这里选用的是基于Astro的别人的一个模板[fuwari](https://github.com/saicaca/fuwari),进入这个链接，点击 fork 到自己的仓库，仓库名称是你的用户名.github.io，Description可以自己取名
### 2.创建密钥
- 打开C:/Users/用户名/.ssh文件夹，打开终端，它可以创建公钥。这里公钥的写的是one,可以自己起名。
"`ssh-keygen -t rsa -C "one@github.com"`"
- 为了管理多个 github 账户需要这么做，你需要一个 config 文件。可以右键新建txt文件而后更改名称（不是txt文件，后缀也要删掉，全称就叫config）。在里面对刚刚新建的秘钥进行配置（注意保存），把下面这一段放进去
```
Host three.github.com
HostName github.com
PreferredAuthentications publickey
User allintky
IdentityFile ~/.ssh/id_rsa_three
```
- 打开 github 点击头像，点击 Settings ，左侧找到 SSH and GPG keys ， 点击 new SSH key
- Title 随便写，下方的 Key 的部分用你刚刚创建的秘钥中的内容填充，即 id_rsa_three.pub （在记事本中编辑）全选复制，粘贴进去。点击 add SSH key ，然后输入自己账号密码。
- 打开终端，输入："`ssh -T git@one.github.com`"