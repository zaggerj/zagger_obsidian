---
banner: 40 - Obsidian/附件/banners/daily-note-banner.gif
created: 2023-11-11T10:58
updated: 2023-11-11T18:18
---
---
searchType: tpl
banner: 40 - Obsidian/附件/banners/daily-note-banner.gif
number headings: auto, first-level 1, max 6, start-at 1, 1.1.
created: 2023-11-09T20:40
updated: 2023-11-10T15:21
---

---
creation date: <% tp.file.creation_date() %>
modification date: <%+ tp.file.last_modified_date("dddd Do MMMM YYYY HH:mm:ss") %>
tags: DailyNote

banner: "40 - Obsidian/附件/banners/daily-note-banner.gif"
cssclass: noyaml
banner_icon: 💌
banner_x: 0.5
banner_y: 0.38
week: <% tp.date.now("YYYY-WW") %>
---

# 1. <% tp.file.title %>

<< [[<% tp.date.now("YYYY年MM月DD日", -1, tp.file.title, "YYYY-MM-DD") %>]] | [[<% tp.date.now("YYYY年MM月DD日", 1, tp.file.title, "YYYY-MM-DD") %>]]>>

## 1.1. Metadata
Status::    <% tp.system.suggester(["🌱发芽状态", "🪴培育状态", "🌲长青状态"], ["#笔记状态/🌱发芽", "#笔记状态/🪴培育","#笔记状态/🌲长青"]) %>
Source Type::  <% tp.system.suggester(["💭想法", "📚书籍", "📰️文章", "🗣️聊天", "💻教学", "▶️视频", "🎧️播客"], ["#📥/💭想法 ", "#📥/📚书籍 ", "#📥/📰️文章", "#📥/🗣️聊天 ", " #📥/💻教学", "#📥/▶️视频", "#📥/🎧️播客"]) %>
Note Type::  <% tp.system.suggester(["笔记", "MOC"], ["#笔记", "#笔记/MOC"]) %>
Topic:: [[<% tp.system.prompt("这个笔记对应的主题MOC ", "比如：时间管理") %>]]
Author:: {原资讯的作者或者对话的人或者引起某种想法的原因}
Source URL:: 
Modify:: `=dateformat(this.file.mtime, "yyyy-MM-dd HH:MM:ss")`

## 1.2. 长青笔记
*一句话概括这篇笔记的内容*
* Summary:: 

## 1.3. 自我重述
*用自己的话去重述提取的重点内容*

## 1.4. 重点摘抄
*摘抄部分原文后，进行筛选加粗然后对加粗的继续进行筛选荧光笔选出。*
### 1.4.1. 事件
**[[<% tp.date.now("YYYY年MM月DD日", 0, tp.file.title, "YYYY年MM月DD日") %>]]**
#跟踪 
#重要 
#记录 
^1

本周记录：[[<%tp.date.now("YYYY年第WW周记录",0, tp.file.title, "YYYY年MM月DD日")%>]]

### 1.4.2. 清单
#官方文档
#记录博客
#学习知识点
#计划任务
#远程协助
#会议
#管理任务 
^2

### 1.4.3. 专题笔记
#idp
#spice
^3


## 1.5. 相关文章
*摘抄来源，引用出处，参考链接，文档查询*
Page Link::  
