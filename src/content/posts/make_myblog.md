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
### 3.克隆仓库与连接
- 到了这步，其实是比较麻烦的，因为好多人的电脑没有装各种东西和配置环境，许多网上的教程直接开始操作，所以就会有各种报错。
- 首先安装git并且配置环境，教程链接：https://blog.csdn.net/weixin_53191752/article/details/119644206
- 接下来是npm,pnpm.教程链接：https://blog.csdn.net/weixin_45682701/article/details/147339130（后续报错可能是教程不全，检查环境配置）
- 配置好一切之后，找到仓库里的Code->SSH,复制它，我的是这样：git@github.com:gwbsd/gwbsd.github.io.git
- 打开vscode,新建一个文件夹，打开终端，运行"`gitclone git@one.github.com:gwbsd/gwbsd.github.io.git`",这里根据你的情况更改，仓库就克隆过来了
- 查看是否与 github 仓库远程连接成功"`git remote -v`"
### 4.配置 Github Pages
- 到项目仓库中，找到 Actions ，enable them 开启它
- 然后在 Settings 里面的 Pages 更改 Source 为 Github Action
### 5.安装依赖和本地查看网页
- 根据模板的教程运行代码，每个模板可能会不同，我们这里是“ `pnpm install` 并 `pnpm add sharp`”
- 再运行这个来在本地查看网页:`pnpm dev`
### 6.把本地仓库推送到远程连接的 github 仓库
- 我们通过一下两个操作来更新我们本地 git 的内容，这时左侧 VScode 显示的绿色、棕色就没了，表示本地内容已同步。其中 . 表示当前文件夹，即把当前文件夹内所有文件和飞控文件夹设置为待提交状态。`git add .` 和 `git commit -m "feat: test`
- 通过以下语句来把本地仓库，推送到远程连接的 github 仓库：`git push`
- Vscode 请求你们授权，就一路点绿色按钮，授权完成，最后页面如果没有跳转，点击它提供的超链接回到 VScode。
- 然后稍等一会儿（等到仓库里棕色的点变为绿色的勾），就完成了
### 7.让所有人都可以打开你的网页
- 进入https://app.netlify.com/，注册一个免费的账号，然后把他与你的github账号连接
- 如果有细节不会，可以查看这里https://docs.astro.build/zh-cn/tutorial/0-introduction/（注意不用按照他的步骤，做自己需要的即可）
## 写在最后
- astro.config.js：把 site 里面前缀更改为你的用户名，也就是用你的网址，其余为添加、修改或删除一些东西，根据需求配置
- src/content：这个文件夹内放的就是你写的博客文档或者项目介绍了。一些操作可以看提供的 Markdown 使用文档学习
- `pnpm new-post <filename>`这个是创建新文章的指令，具体可以仔细读一下docs文件夹里的README.zh-CN