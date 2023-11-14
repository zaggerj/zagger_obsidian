---
tags: DailyNote
searchterm: "#周记"
banner: "040 - Obsidian/附件/banners/daily-note-banner.gif"
cssclass: noyaml
banner_icon: 💌
banner_x: 0.5
banner_y: 0.38
week: <% tp.date.now("YYYY-WW") %>
created: 2023-11-14T08:18
updated: 2023-11-14T11:21
---

# 1. <% tp.file.title %>

_本文件主旨，并链接到前一天和后一天文件_

<< [[<% tp.date.now("YYYY年MM月DD日", -1, tp.file.title, "YYYY-MM-DD") %>]] | [[<% tp.date.now("YYYY年MM月DD日", 1, tp.file.title, "YYYY-MM-DD") %>]]>>

## 1.1. Metadata

_添加一些元数据，方便后续搜索查看等等_

Status:: <% tp.system.suggester(["🌱 发芽状态", "🪴 培育状态", "🌲 长青状态"], ["#笔记状态/🌱 发芽", "#笔记状态/🪴 培育","#笔记状态/🌲 长青"]) %>
Source Type:: <% tp.system.suggester(["💭 想法", "📚 书籍", "📰️ 文章", "🗣️ 聊天", "💻 教学", "▶️ 视频", "🎧️ 播客"], ["#📥/💭 想法 ", "#📥/📚 书籍 ", "#📥/📰️ 文章", "#📥/🗣️ 聊天 ", " #📥/💻 教学", "#📥/▶️ 视频", "#📥/🎧️ 播客"]) %>
Note Type:: <% tp.system.suggester(["笔记", "MOC"], ["#笔记", "#笔记/MOC"]) %>
Topic:: [[<% tp.system.prompt("这个笔记对应的主题MOC ", "DailyNote") %>]]
Author:: {原资讯的作者或者对话的人或者引起某种想法的原因}
Source URL::
Modify:: `=dateformat(this.file.mtime, "yyyy-MM-dd HH:MM:ss")`

## 1.2. 长青笔记

_一句话概括这篇笔记的内容_

- Summary::

## 1.3. 自我重述

_用自己的话去重述提取的重点内容_

## 1.4. 重点摘抄

_摘抄部分原文后，进行筛选加粗然后对加粗的继续进行筛选荧光笔选出。_

### 1.4.1. 事件

_记录当天出现的事件_

**[[<% tp.date.now("YYYY年MM月DD日", 0, tp.file.title, "YYYY年MM月DD日") %>]]** 
#跟踪 
#重要 
#记录

#### 1.4.1.1. 每日工时

_记录禅道工时，最终摘抄到禅道_

- [ ] 08:30 - 09:30 #工时  1h
- [ ] 09:30 - 10:30 #工时  1h
- [ ] 10:30 - 12:00 #工时  1.5h
- [ ] 14:00 - 15:30 #工时  1.5h
- [ ] 15:30 - 16:30 #工时  1h
- [ ] 16:30 - 17:30 #工时  1h
^1

本周记录：[[<%tp.date.now("YYYY年第WW周记录",0, tp.file.title, "YYYY年MM月DD日")%>]]

### 1.4.2. 清单

_备注当前学习文档，计划任务，每天看前一天的计划任务，每天都有延续_

#官方文档 
#记录博客
#学习知识点
#计划任务
#远程协助
#会议 
#管理任务
^2

### 1.4.3. 专题笔记

_主要是专题问题备注查看_

#idp
#spice
^3

## 1.5. 相关文章

_摘抄来源，引用出处，参考链接，文档查询_

Page Link::

