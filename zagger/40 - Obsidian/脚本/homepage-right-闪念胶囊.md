---
UID: 20231107205229 
aliases: 
tags: 
source: 
cssclass: 
created: 2023-11-07
---

## ✍内容


```dataviewjs
dv.table(
	["Task", "Name"],
	dv.pages("#善念胶囊").file.tasks
		.where(t => (!t.completed && t.text.indexOf("#善念胶囊") > 0))
		.map(b => ["[ ] - " + b.text], b.link)
)
```