---
creation date: <% tp.file.creation_date() %>
tags:
  - 周记
searchterm: "#周记"
banner: "040 - Obsidian/附件/banners/daily-note-banner.gif"
cssclass: noyaml
banner_icon: 💌
banner_x: 0.5
banner_y: 0.38
week: <% tp.date.now("YYYY-WW") %>
---

# 1. <% tp.file.title %>

_本文件主旨，并链接到前一天和后一天文件_

记录日期：{{monday:YYYY年MM月DD日}} ~ {{friday:YYYY年MM月DD日}}

## 1.1. Metadata

_添加一些元数据，方便后续搜索查看等等_

Status::    <% tp.system.suggester(["🌱发芽状态", "🪴培育状态", "🌲长青状态"], ["#笔记状态/🌱发芽", "#笔记状态/🪴培育","#笔记状态/🌲长青"],false, "笔记状态是？") %>
Source Type::  <% tp.system.suggester(["💭想法", "📚书籍", "📰️文章", "🗣️聊天", "💻教学", "▶️视频", "🎧️播客"], ["#📥/💭想法 ", "#📥/📚书籍 ", "#📥/📰️文章", "#📥/🗣️聊天 ", " #📥/💻教学", "#📥/▶️视频", "#📥/🎧️播客"],false, "笔记源自哪里？") %>
Note Type::  <% tp.system.suggester(["笔记", "MOC"], ["#笔记", "#MOC"],false, "笔记类型是？") %>
Topic:: [[<% tp.system.prompt("这个笔记对应的主题MOC ", "DailyNote") %>]]
Author:: {原资讯的作者或者对话的人或者引起某种想法的原因}
Modify:: `=dateformat(this.file.mtime, "yyyy-MM-dd HH:MM:ss")`

## 1.2. 周待办

_周计划，每周计划完成的事情_

- [ ] 待办示例1
- [ ] 待办示例2

# 2. 记录

_集中记录_

## 2.1. {{DATE: gggg年ww周记录}}
![[{{monday:YYYY年MM月DD日}}#^1]] 
![[{{tuesday:YYYY年MM月DD日}}#^1]] 
![[{{wednesday:YYYY年MM月DD日}}#^1]] 
![[{{thursday:YYYY年MM月DD日}}#^1]] 
![[{{friday:YYYY年MM月DD日}}#^1]] 
![[{{saturday:YYYY年MM月DD日}}#^1]] 
![[{{sunday:YYYY年MM月DD日}}#^1]] 


## 2.2. {{DATE: gggg年ww周清单}}

_集中清单_

![[{{monday:YYYY年MM月DD日}}#^2]] 
![[{{tuesday:YYYY年MM月DD日}}#^2]] 
![[{{wednesday:YYYY年MM月DD日}}#^2]] 
![[{{thursday:YYYY年MM月DD日}}#^2]] 
![[{{friday:YYYY年MM月DD日}}#^2]] 
![[{{saturday:YYYY年MM月DD日}}#^2]] 
![[{{sunday:YYYY年MM月DD日}}#^2]] 

## 2.3. {{DATE: gggg年ww周专题笔记}}

_集中专题笔记_

![[{{monday:YYYY年MM月DD日}}#^3]] 
![[{{tuesday:YYYY年MM月DD日}}#^3]] 
![[{{wednesday:YYYY年MM月DD日}}#^3]] 
![[{{thursday:YYYY年MM月DD日}}#^3]] 
![[{{friday:YYYY年MM月DD日}}#^3]] 
![[{{saturday:YYYY年MM月DD日}}#^3]] 
![[{{sunday:YYYY年MM月DD日}}#^3]] 
