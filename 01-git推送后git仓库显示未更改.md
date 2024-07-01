---
title: git推送后git仓库显示未更改
description: 在使用vscode推送到github后显示提交成功，本地没有更改项，仓库不显示提交的信息，没有记录贡献。
slug: git推送后git仓库显示未更改
authors: happlay
hide_table_of_contents: false
sidebar-position: 3
---

## 事件起因
我在`add`代码前修改了`github`中对应仓库的名字，然后本地用`git remote rm origin`命令移除了和远程仓库的关联。

## 原因
接着运行`git remote add origin github:github.com:用户名/仓库名.git`命令：

- 使用`git remote add origin github:github.com:用户名/仓库名.git` 只是添加了一个名为 origin 的远程仓库，并没有设置本地分支与远程分支之间的跟踪关系。为了设置跟踪关系，你需要明确地告诉 Git 你的本地分支要跟踪哪个远程分支。

## 解决
通过`git branch --set-upstream-to=origin/master master`命令连接本地及远程分支

## 建议
在推送分支前先用`git pull`命令或
![Snipaste_2024-07-01_09-38-00](https://happlay-docs.oss-cn-beijing.aliyuncs.com/docs/Snipaste_2024-07-01_09-38-00.png)
拉取远程分支最新代码再使用`git push`推送到远程仓库