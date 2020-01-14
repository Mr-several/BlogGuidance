# GitHub Guide

## 每个项目的说明文件都是使用md格式来写的

## git 工具学习

## Code中的标签

#### 使用branches进行比较

只要在网站的后面加入一个/compare 就能进行两个分支之间的比较

#### commits选项

表示有多少次提交，其中的下拉菜单可以看到不同的版本。

## issue标签

在这里可以进行问题的提交，每个问题后面会带有一个标签，标签表示的是这是个什么类型的问题。

## Pull request

可以使用PR功能实现自己代码和原始代码的合并，也就是发出一个合并请求。

## projects 项目管理

可以放置一些工作计划或者工作流程在project中，可以创建一个新的project之后在其中加入一些标签，标签之间的内容可以直接拖动进行调整。

## Insight

能够实现浏览的监控和控制。

## Setting

1. GitHub Pages
能够帮助建立自己的网站。就是提供一个网站部署的工具 。

2. Webhooks
当项目发生变化的时候可以发送一个消息。在企业级开发中比较常用。

3. Danger Zone
就是仓库的删除。还能实现仓库的转移，私有化等功能。

## 使用GitHub 查找开源项目

要求实现精确搜索

1. 在仓库名字中含有指定关键词的方法
`in:name spring boot`
就能实现查找名字中含有关键词的一些项目

2. 筛选项目的star数目：
`in:name spring boot star:>3000`
就能实现查找star数目大于3000的开源项目

3. 和上面一样的可以实现筛选forks数目：
`in:name spring boot star:>3000 forks:>3000`
就能同时实现查找forks数目大于3000的项目了

4. 查找在readme中出现关键词的项目
因为只是在名字中含有关键词有很多的局限性，所以很多时候还要搜索在readme中出现关键词的项目。
`in:readme spring boot star:>1500`

5. 查找在描述中出现关键词的项目以及筛选更新日期的项目
`in:description script language:python pushed:>2019-09-03`
就能实现查找在描述中含有关键词的项目，以及查找指定语言的项目同时还实现了查找最近有更新的项目。
