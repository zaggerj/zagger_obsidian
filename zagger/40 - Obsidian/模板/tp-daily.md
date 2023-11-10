---
number headings: auto, first-level 1, max 6, start-at 1, 1.1
---
<%*
let today = tp.date.now("YYYY-MM-DD")
let inputDate = await tp.system.prompt("输入示例："+today,today)
titleName = window.moment(inputDate, "YYYY-MM-DD", true).format("YYYY-MM-DD_ddd")

before_date = window.moment(inputDate, "YYYY-MM-DD", true).add(-1,"days").format("YYYY-MM-DD_ddd")

after_date = window.moment(inputDate, "YYYY-MM-DD", true).add(1,"days").format("YYYY-MM-DD_ddd")

let createTime = tp.file.creation_date()
let modificationDate = tp.file.last_modified_date("dddd Do MMMM YYYY HH:mm:ss")
-%>

---
create time : <% createTime %>
modification date: <% modificationDate %>

---

<< [[<% before_date %>]] | [[<% after_date %>]] >>

<%-* /* 需要翻墙 */ -%>
<% tp.web.daily_quote() %>
<% tp.web.random_picture("200x200", "landscape,water") %>

## 0.1 Metadata
Status::    <% tp.system.suggester(["🌱发芽状态", "🪴培育状态", "🌲长青状态"], ["#笔记状态/🌱发芽", "#笔记状态/🪴培育","#笔记状态/🌲长青"]) %>
Source Type::  <% tp.system.suggester(["💭想法", "📚书籍", "📰️文章", "🗣️聊天", "💻教学", "▶️视频", "🎧️播客"], ["#📥/💭想法 ", "#📥/📚书籍 ", "#📥/📰️文章", "#📥/🗣️聊天 ", " #📥/💻教学", "#📥/▶️视频", "#📥/🎧️播客"]) %>
Note Type::  <% tp.system.suggester(["笔记", "MOC"], ["#笔记", "#笔记/MOC"]) %>
Topic:: [[<% tp.system.prompt("这个笔记对应的主题MOC ", "比如：时间管理") %>]]
Author:: {原资讯的作者或者对话的人或者引起某种想法的原因}
Source URL:: 
Modify:: `=dateformat(this.file.mtime, "yyyy-MM-dd HH:MM:ss")`

## 0.2 重点关注
-  ==早上 7 件事==
	- [ ] 花点时间回顾和反思
	- [ ] 查看「反向链接」和「工作待办」
	- [ ] 扫一眼邮件
	- [ ] 确定最困难的工作，拆分成多个小任务
	- [ ] 写下需要思考的东西
	- [ ] 忽略人际关系冲突
	- [ ] 不开会/少开会
- 工作效率
	- [[会议检查清单]]
	- [[Workbench]]
	
## 0.3 阅读笔记 & 会议纪要
通常记录一些需要技术阅读的内容

## 0.4 间歇日记
- 今日重点任务 
- xxxxx
<%*
await tp.file.move("/00 - 每日日记/DailyNote/" + titleName)
tp.file.cursor()
-%>