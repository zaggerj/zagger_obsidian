---
created: 2023-11-06T08:20
updated: 2023-11-10T12:43
---
![[Pasted image 20230804152635.png]]
```
netsh advfirewall firewall add rule name="LocalSend" dir=in action=allow protocol=TCP localport=53317netsh advfirewall firewall add rule name="LocalSend" dir=in action=allow protocol=UDP localport=53317
```