---
UID: 20231105215716
aliases: 
tags:
  - 远程桌面/idp
  - 排查问题/idp
  - 工作
source: 
cssclasses: 
created: 2023-11-06
---

## ✍内容
![[M{994[AZF%U`8I2}DK([W4A.png]]

### 查看weboeidp服务
`systemctl status weboeidpproxy.service`

![[Pasted image 20231106174827.png]]

### 查看服务目录


![[Pasted image 20231106174947.png]]

### 父级目录查看oeidp.json配置文件
`/usr/lib/python2.7/site-packages/tcloud/thor/weboeidp
`
![[Pasted image 20231106175041.png]]

### 查看配置文件oeidp.json

![[Pasted image 20231106175220.png]]
### 查看/opt/spicehtml5proxy/static/路径

跟spice代理（spicehtml5proxy）共用一套web页面

![[Pasted image 20231106175327.png]]


### 查看日志文件

`/var/log/html5proxy/weboeidp.log`

![[Pasted image 20231106175526.png]]

#记录 问题服务器是从145上连上了155服务器的桌面。结果代理报token 失效