---
searchType: tpl
tags:
  - 周记
searchterm: "#bird"
duration: 1 year
cssclasses: 
created: 2023-11-09T20:40
updated: 2023-11-10T15:21
---

记录日期：{{monday:YYYY年MM月DD日}} ~ {{friday:YYYY年MM月DD日}}

## 0.1 Metadata
Status::    <% tp.system.suggester(["🌱发芽状态", "🪴培育状态", "🌲长青状态"], ["#笔记状态/🌱发芽", "#笔记状态/🪴培育","#笔记状态/🌲长青"],false, "笔记状态是？") %>
Source Type::  <% tp.system.suggester(["💭想法", "📚书籍", "📰️文章", "🗣️聊天", "💻教学", "▶️视频", "🎧️播客"], ["#📥/💭想法 ", "#📥/📚书籍 ", "#📥/📰️文章", "#📥/🗣️聊天 ", " #📥/💻教学", "#📥/▶️视频", "#📥/🎧️播客"],false, "笔记源自哪里？") %>
Note Type::  <% tp.system.suggester(["笔记", "MOC"], ["#笔记", "#MOC"],false, "笔记类型是？") %>
Topic:: [[<% tp.system.prompt("这个笔记对应的主题MOC ", "DailyNote") %>]]
Author:: {原资讯的作者或者对话的人或者引起某种想法的原因}
Modify:: `=dateformat(this.file.mtime, "yyyy-MM-dd HH:MM:ss")`
## 0.2 周待办
- [ ] 待办示例1
- [ ] 待办示例2


# 1 {{DATE: gggg年ww周记录}}
![[{{monday:YYYY年MM月DD日}}#^1]] 
![[{{tuesday:YYYY年MM月DD日}}#^1]] 
![[{{wednesday:YYYY年MM月DD日}}#^1]] 
![[{{thursday:YYYY年MM月DD日}}#^1]] 
![[{{friday:YYYY年MM月DD日}}#^1]] 
![[{{saturday:YYYY年MM月DD日}}#^1]] 
![[{{sunday:YYYY年MM月DD日}}#^1]] 

# 2 记录
## 2.1 {{DATE: gggg年ww周清单}}
![[{{monday:YYYY年MM月DD日}}#^2]] 
![[{{tuesday:YYYY年MM月DD日}}#^2]] 
![[{{wednesday:YYYY年MM月DD日}}#^2]] 
![[{{thursday:YYYY年MM月DD日}}#^2]] 
![[{{friday:YYYY年MM月DD日}}#^2]] 
![[{{saturday:YYYY年MM月DD日}}#^2]] 
![[{{sunday:YYYY年MM月DD日}}#^2]] 

## 2.2 专题笔记
![[{{tuesday:YYYY年MM月DD日}}#^3]] 
![[{{wednesday:YYYY年MM月DD日}}#^3]] 
![[{{thursday:YYYY年MM月DD日}}#^3]] 
![[{{friday:YYYY年MM月DD日}}#^3]] 
![[{{saturday:YYYY年MM月DD日}}#^3]] 
![[{{sunday:YYYY年MM月DD日}}#^3]] 
