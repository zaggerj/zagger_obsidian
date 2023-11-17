---
<%-*
// 只弹一次窗口，让用户填写名称，然后猜测用户所想，即可
// 用户可能需要做两件事情，1. 自动添加模板 2. 自动归类到文件夹
const noteName = await tp.system.prompt("给这个笔记定一个名字 ", tp.date.now("YYYY-MM-DD"))
await tp.file.rename(noteName)
const name = tp.file.title
// 日记类型笔记
const dailyReg = /日记|(\d+年)?(\d+月)?(\d+日|\d+号)/
// 笔记类型
const jsReg = /nodejs|electron|typescript|vue|webAssembly|webpack|worker|小程序|css|js|事件循环|前端|二进制/
const lowReg = /bash|linux|nginx|jenkins|docker|服务器/
const currentFolder = tp.file.folder()
if (name.match(dailyReg)) {
  tp.file.include("[[tp-每日日记模板]]")
} else {
  tp.file.include("[[tp-长青笔记模板]]")
}

const matches = name.match(jsReg)
console.log(matches)
-%>

alias: 
tags: 长青笔记
cdate: <% tp.file.creation_date() %>
uid: <% tp.date.now("YYYYMMDDHHmmss") %>
update: <%+ tp.file.last_modified_date("YYYY-MM-DD dddd HH:mm:ss") %>
searchterm: "#长青笔记"
banner: "040 - Obsidian/附件/banners/book-banner.gif"
cssclass: noyaml
banner_icon: 💌
banner_x: 0.5
banner_y: 0.38
File Folder: <% currentFolder %>
---


123
