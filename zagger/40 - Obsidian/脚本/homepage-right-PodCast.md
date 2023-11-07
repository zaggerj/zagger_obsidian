---
UID: 20231107205522 
aliases: 
tags: 
source: 
cssclass: 
created: 2023-11-07
---

## ✍内容


```dataviewjs
dv.table(
	["Name","type", "Create Time" ],
	// sort(compareFn, descStr)
	dv.pages("#PodCast and #waiting")
		.map(b => [b.file.link, b.type, b.file.ctime])
)
```