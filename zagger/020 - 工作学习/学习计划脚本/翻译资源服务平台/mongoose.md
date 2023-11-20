---
alias: 
tags: 长青笔记
cdate: 2023-11-20 16:20
uid: 20231120162131
searchterm: "#长青笔记"
banner: 040 - Obsidian/附件/banners/book-banner.gif
cssclass: noyaml
banner_icon: 💌
banner_x: 0.5
banner_y: 0.38
created: 2023-11-20 16:20:51
updated: 2023-11-20 17:19:28
---

# 1. mongoosejs

## 1.1. Metadata

Status:: #笔记状态/🌱 发芽
Source Type:: #📥/💭 想法 
Note Type:: #笔记
Topic:: [[00.学习-前端]]
Author:: zagger
Source URL::
Modify:: 2023-11-20 星期一 16:20:51

## 1.2. 长青笔记

_一句话概括这篇笔记的内容_
Summary::

## 1.3. 自我重述

_用自己的话去重述提取的重点内容_

## 1.4. 重点摘抄

_摘抄部分原文后，进行筛选加粗然后对加粗的继续进行筛选荧光笔选出。_

增加删除所有数据，接口，方便开发。
```js
/**
 * 删除所有翻译资源
 */
router.delete('/all', function (req, res, next) {
  ResourceModel.deleteMany({}).then(
    () => {
      res.json({ ok: true })
    },
    e => {
      return res.status(500).json({ ok: false, message: e.message })
    }
  )
})

```
# 2. 相关文章

_摘抄来源，引用出处，参考链接，文档查询_
Page Link::

[Mongoose 5.0 中文文档](http://www.mongoosejs.net/docs/api.html#deletemany_deleteMany)
