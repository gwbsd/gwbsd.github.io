---
title: 一些常用的git指令
published: 2026-03-31
description: ''
image: ''
tags: []
category: ''
draft: false 
lang: 'zh_CN'
---
以下是小白入门最常用的 Git 指令分类总结，涵盖日常 90% 的场景：

### 一、基础配置（首次使用必做）
- **设置用户信息**（提交代码时的身份标识）
  ```bash
  git config --global user.name "你的名字"
  git config --global user.email "你的邮箱"
  ```
- **查看配置**
  ```bash
  git config --list
  ```

### 二、创建/克隆仓库
- **初始化本地仓库**（在当前文件夹生成 `.git`）
  ```bash
  git init
  ```
- **克隆远程仓库**（从线上下载完整项目）
  ```bash
  git clone <仓库地址>
  ```

### 三、日常提交（最常用流程）
1. **查看状态**（检查哪些文件修改了）
   ```bash
   git status
   ```
2. **添加到暂存区**
   ```bash
   git add .          # 添加所有修改
   git add <文件名>   # 添加指定文件
   ```
3. **提交到本地仓库**
   ```bash
   git commit -m "写清楚这次改了什么"
   ```

### 四、分支管理
- **查看分支**
  ```bash
  git branch     # 查看本地分支
  git branch -a  # 查看所有分支（含远程）
  ```
- **创建/切换分支**
  ```bash
  git branch <分支名>       # 创建新分支
  git switch <分支名>       # 切换到某分支（推荐）
  git checkout <分支名>     # 旧版切换命令
  ```
- **合并分支**
  ```bash
  git merge <要合并的分支名>  # 把该分支合并到当前分支
  ```
- **删除分支**
  ```bash
  git branch -d <分支名>
  ```

### 五、远程同步
- **关联远程仓库**
  ```bash
  git remote add origin <远程仓库地址>
  ```
- **推送代码**
  ```bash
  git push origin <分支名>
  ```
- **拉取代码**
  ```bash
  git pull origin <分支名>  # 拉取并自动合并
  git fetch origin          # 仅拉取不合并（更安全）
  ```

### 六、撤销与回退（救急用）
- **撤销工作区修改**（还没 add 时）
  ```bash
  git restore <文件名>
  ```
- **撤销暂存区**（已经 add 但没 commit）
  ```bash
  git restore --staged <文件名>
  ```
- **查看提交历史**
  ```bash
  git log --oneline  # 简洁显示一行一条
  ```

---

需要我针对某个具体指令（比如 `git rebase` 或 `git stash`）给你举个实际例子吗？