---
created: 2023-11-08T14:23
updated: 2023-11-12T13:42
searchType: tpl
---

---

<%-\*
var cleanTitle = tp.user.getTitleSnippet(tp.file.title)
var title = `${cleanTitle}`;
await tp.file.rename(`${title}`);
let filetype = await tp.system.suggester(["学习", "工作", "非开发", "代码库", "obsidian 教程" ,"临时路径"], ["学习","工作", "非开发","代码库", "obsidian 教程","临时"], false, "路径放到哪里？") 
if (filetype === "学习") { 
myFilePath = "/020 - 工作学习/学习/" +  `${title}`;
await tp.file.move(`${myFilePath}`);
} else if (filetype === "工作") { 
myFilePath = "/020 - 工作学习/工作/" +  `${title}`;
await tp.file.move(`${myFilePath}`);
} else if (filetype === "非开发") { 
myFilePath = "/020 - 工作学习/非开发/" +  `${title}`;
await tp.file.move(`${myFilePath}`);
} else if (filetype === "代码库") { 
myFilePath = "/020 - 工作学习/代码库/" +  `${title}`;
await tp.file.move(`${myFilePath}`);
} else if (filetype === "obsidian 教程") { 
myFilePath = "/040 - Obsidian/教程/" +  `${title}`;
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
update: <%+ tp.file.last_modified_date("YYYY-MM-DD dddd HH:mm:ss") %>
cssclass:
cover:

---

# 1. <% tp.file.title %>

## 1.1. Metadata

Status:: <% tp.system.suggester(["🌱 发芽状态", "🪴 培育状态", "🌲 长青状态"], ["#笔记状态/🌱 发芽", "#笔记状态/🪴 培育","#笔记状态/🌲 长青"]) %>
Source Type:: <% tp.system.suggester(["💭 想法", "📚 书籍", "📰️ 文章", "🗣️ 聊天", "💻 教学", "▶️ 视频", "🎧️ 播客"], ["#📥/💭 想法 ", "#📥/📚 书籍 ", "#📥/📰️ 文章", "#📥/🗣️ 聊天 ", " #📥/💻 教学", "#📥/▶️ 视频", "#📥/🎧️ 播客"]) %>
Note Type:: <% tp.system.suggester(["笔记", "MOC"], ["#笔记", "#笔记/MOC"]) %>
Topic:: [[<% tp.system.prompt("这个笔记对应的主题MOC ", "DailyNote") %>]]
Author:: {原资讯的作者或者对话的人或者引起某种想法的原因}
Source URL::
Modify:: `=dateformat(this.file.mtime, "yyyy-MM-dd HH:MM:ss")`

## 1.2. 长青笔记

_一句话概括这篇笔记的内容_
Summary::

## 1.3. 自我重述

_用自己的话去重述提取的重点内容_

## 1.4. 重点摘抄

_摘抄部分原文后，进行筛选加粗然后对加粗的继续进行筛选荧光笔选出。_
1. #macos/appstorrent [Поиск по сайту » Appstorrent - Игры и программы для macOS](https://appstorrent.ru/?story=Dynamic+Wallpaper+Engine&do=search&subaction=search)
2. #macos/macoshome[Dynamic Wallpaper for Mac v16.6高清4K动态壁纸中文版 - 苹果系统之家](https://macoshome.com/app/utilities/6908.html#Down)
3. #macos/ishotpro [iShot Pro For Mac v2.3.8 截图录屏录音OCR翻译取色工具 - 苹果系统之家](https://macoshome.com/app/productivity/19764.html#Down)
4. #macos/macyy[macyy.cn | Site Unreachable](https://www.macyy.cn/resources)
5. #macos/下载 mac电脑下载站：
	1. 马可波罗：[马可菠萝 - 分享你喜欢的MAC应用](https://www.macbl.com/)
	2. xclient：[精品MAC应用分享](http://Xclient.info)
	3. Mac8k：[Mac8k-Mac宝藏资源免费分享](https://www.mac8k.com/)
	4. Mac软件之家，应该是需要关注公众号，进行下载：[Mac软件之家 - Mac软件,Mac游戏,Mac破解软件,photoshop,office,Mac壁纸](https://www.macapp.so/)[Mac壁纸 - Mac高清壁纸,Retina壁纸下载](https://www.macapp.so/wallpaper/)
	5. Maceniov，需要翻墙：[MacEnjoy-macOS破解资源分享站](https://www.macenjoy.co/)
	6. [Site Unreachable](https://www.macyy.cn/resources?type=free)
6. ![image.png](https://raw.githubusercontent.com/zaggerj/obsidian_picgo/main/obsidian20231112132956.png)

7. 软件下载方式：![image.png](https://raw.githubusercontent.com/zaggerj/obsidian_picgo/main/obsidian20231112132403.png)

## 1.5. 相关文章

_摘抄来源，引用出处，参考链接，文档查询_
Page Link::

