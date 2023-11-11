---
created: 2023-11-03T22:29
updated: 2023-11-06T12:24
---
# a docker实战 - 禅道卫士维护 2023.0606

1. 地址：[禅道卫士](http://192.168.0.161:8090/)
2. 代码仓库：[https://mystorp.coding.net/p/oseasyfe/d/zentao-doctor/git](https://mystorp.coding.net/p/oseasyfe/d/zentao-doctor/git)
3. [zaggerzj@163.com](http://zaggerzj@163.com)
4. 帐号：192.168.0.161
5. root/[oseasy@123](http://oseasy@123)
6. config.json

```js
{
    "host": "172.16.203.12",
    "port": 80,
    "username": "admin",
    "password": "oseasy@2018",
    "verbose": false,
    "code": "test",
    "key": "2d802945902cd6b3081bb9df4fe0553f",
    "requestType": "PATH_INFO"
}
```

7. 
```bash
# /xx/yy/url.html 等于  /xx/yy/url.json
# fe.os-easy.com是代码仓库，暂时不用管
npm run dev # 进行开发
npm run start # 用于生产
npm run pack # 用于打包镜像,执行命令之前确保docker已经启动
docker save fe.os-easy.com:5000/zentao-doctor:1.0.15 > zentao-doctor.tar # 进行打包
scp -r zentao-doctor.tar root@192.168.0.161:/root
ssh root@192.168.0.161 # 输入密码
docker load -i zentao-doctor.tar # 加载完镜像
```



16. ​![image](40%20-%20Obsidian/附件/Attachment/assets%206-zagger/image-20230705213808-7ck8gb8.png)​

17. docker ps -a
18. ​![image](40%20-%20Obsidian/附件/Attachment/assets%206-zagger/image-20230705213819-bgypwz1.png)​

19. docker stop xxx
20. docker rm xxx

　　​![image](40%20-%20Obsidian/附件/Attachment/assets%206-zagger/image-20230705213844-jn73zvh.png)​

```bash
docker run -d --name zentao-doctor -p 8090:3000 fe.os-easy.com:5000/zentao-doctor:1.0.15 # 出现容器id，表示成功
docker restart zentao-doctor

# 问题1：解决禅道admin账号密码被修改的问题
history | grep docker # 找到最近的zentao-doctor相关的命令
run -d --name zentao-doctor -p 8090:3000 fe.os-easy.com:5000/zentao-doctor:1.0.14
docker exec -it zentao-doctor /bin/sh
# 将目录中的config.json改为自己的账号
docker restart zentao-doctor

# 问题2 ：解决 docker load -i zentao-doctor.tar 无法加载镜像
# Authorization not available. Check if polkit service is running or see debug message for more information.
# Cannot connect to the Docker daemon at unix:///var/run/docker.sock. Is the docker daemon running?
# systemctl start docker systemctl enable docker 都失效
reboot # centos 系统执行重启

```
`

```js
docker-compose start  vsftpd

docker-compose logs  vsftpd

docker start frontend-docs

docker stop frontend-docs

cd /usr/local/vsftpd-compose/vsftpd/data/oseasy/trunk/V5.5.0-VPC版本/docker/docker安装包/

md5sum VPC-1.6-X86_64-dev-5.5.0-docker.bin

service docker status

docker status showdoc

chmod 777 VDI-0.5-X86_64-dev-5.5.0-docker.bin

df -h

df -lh

df -all

tar -xzvf 0.0.112.tar.gz

find / -name cloudos-kvm-1.24.11.0-r5971.zip

find -type d -name 'fedoc'
/usr/share/nginx/html/fedoc
systemctl status nginx
systemctl start nginx


# 重启showdoc
cd /
chmod 777 showdoc
chmod 644 showdoc
# 4表示读取权限，2表示写入权限，1表示执行权限。

```
[chmod 权限-rw-r--r--表示什么含义_程序员杰森的博客-CSDN博客](https://blog.csdn.net/weixin_43670802/article/details/105272266)
[Linux chmod 命令 | 菜鸟教程 (runoob.com)](https://www.runoob.com/linux/linux-comm-chmod.html)