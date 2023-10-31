![[obsidian使用相关1/Attachment/Pasted image 20230804152635.png]]
```
netsh advfirewall firewall add rule name="LocalSend" dir=in action=allow protocol=TCP localport=53317netsh advfirewall firewall add rule name="LocalSend" dir=in action=allow protocol=UDP localport=53317
```