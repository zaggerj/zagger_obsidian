---
alias: 
tags: 
cdate: 2023-11-09 08:30
uid: 20231109083107 
Update: NaN
cssclass: 
Cover: 
---

## Metadata
Status::    #笔记状态/🌱发芽
Source Type::  #📥/💭想法 
Note Type::  #笔记
Topic:: [[dataviewjs 代码]]
Author:: {原资讯的作者或者对话的人或者引起某种想法的原因}
Source URL:: 

```dataviewjs
dv.table(
 [ "feild", "value", "path", "url"],
 dv.pages("#教程/obsidian/清单").file.lists
 .where(l => l.type)
 .sort(l => l.type, "desc")
 .map(l =>  {
  const [type, typeValue] = l.type.split("-")
  return [type, typeValue, l.path, l.url]
 })
)
```

## 长青笔记
一句话概括这篇笔记的内容
Summary:: 

## 自我重述
用自己的话去重述提取的重点内容


## 重点摘抄
摘抄部分原文后，进行筛选加粗然后对加粗的继续进行筛选荧光笔选出。


## 相关文章
Page Link::  


