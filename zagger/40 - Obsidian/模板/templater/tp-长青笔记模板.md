---
<%-*
var cleanTitle = tp.user.getTitleSnippet(tp.file.title) 
var title = `${cleanTitle}`;
await tp.file.rename(`${title}`);
let filetype = await tp.system.suggester(["写作学习", "软件学习", "其他学习", "临时路径"], ["写作","软件", "其他", "临时"], false, "路径放到哪里？") 
if (filetype === "写作") { 
myFilePath = "/20 - 工作学习/01 写作学习/" +  `${title}`;
await tp.file.move(`${myFilePath}`);
} else if (filetype === "软件") { 
myFilePath = "/20 - 工作学习/02 软件学习/" +  `${title}`;
await tp.file.move(`${myFilePath}`);
} else if (filetype === "其他") { 
myFilePath = "/20 - 工作学习/03 其他/" +  `${title}`;
await tp.file.move(`${myFilePath}`);
} else if (filetype === "临时") { 
myFilePath = "/60 - 临时/" +  `${title}`;
await tp.file.move(`${myFilePath}`);
} else { 
tp.file.cursor(1);
}
-%>

alias: 
tags: 
cdate: <% tp.file.creation_date() %>
uid: <% tp.date.now("YYYYMMDDHHmmss") %> 
Update: <%+ tp.file.last_modified_date("YYYY-MM-DD dddd HH:mm:ss") %>
cssclass: 
Cover: 
---

## Metadata
Status::    <% tp.system.suggester(["🌱发芽状态", "🪴培育状态", "🌲长青状态"], ["#笔记状态/🌱发芽", "#笔记状态/🪴培育","#笔记状态/🌲长青"]) %>
Source Type::  <% tp.system.suggester(["💭想法", "📚书籍", "📰️文章", "🗣️聊天", "💻教学", "▶️视频", "🎧️播客"], ["#📥/💭想法 ", "#📥/📚书籍 ", "#📥/📰️文章", "#📥/🗣️聊天 ", " #📥/💻教学", "#📥/▶️视频", "#📥/🎧️播客"]) %>
Note Type::  <% tp.system.suggester(["笔记", "MOC"], ["#笔记", "#笔记/MOC"]) %>
Topic:: [[<% tp.system.prompt("这个笔记对应的主题MOC ", "比如：时间管理") %>]]
Author:: {原资讯的作者或者对话的人或者引起某种想法的原因}
Source URL:: 

## 长青笔记
一句话概括这篇笔记的内容
Summary:: 

## 自我重述
用自己的话去重述提取的重点内容


## 重点摘抄
摘抄部分原文后，进行筛选加粗然后对加粗的继续进行筛选荧光笔选出。


## 相关文章
Page Link::  
