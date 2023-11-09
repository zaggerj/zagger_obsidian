---
tags:
  - linux
  - 命令/linux/集合
  - 命令
aliases:
  - 服务器命令集合
---
`netstat -ano | grep 9527|awk '{print $5}' | xargs kill -9`

```shell
ps -ef | grep mysql
netstat -tunlp | grep mysql
mysql -u oseasy
mysql -u oseasy -p cloudhan
mysql -u oseasy -pcloudhan
service firewalld restart
python /var/www/console/thor-console.pyc shell
service vdi-* restart
vdi-thor-gunicorn restart
python /var/www/console/thor-console.pyc shell
service vdi-thor-gunicorn restart
```


# 快速清空工作区 #clean #empty
`git checkout -- .;git clean -fd;`

# mac干掉不要的文件 #find #\.DS_Store
`find . -type f -name ".DS_Store" | xargs rm -rf`

#查看etc目录占用比较大的目录

```shell
du -h /etc | grep G
```

![[Pasted image 20231018111633.png]]

#跳过检查
> git commit --no-verify
#终端快捷键
ctrl+u 
ctrl+k
ctrl+a
ctrl+e
![[Pasted image 20231017180331.png]]

复制spice-web-client代码到console仓库，cp -rv
```shell
# cwd code
cp -rv ./spice-web-client/dist/** ./ngconsole/js/libs/spice/ &&
	cp -rv ./spice-web-client/oeidp/** ./ngconsole/js/libs/oeidp/

# cwd spice-web-client
cp -rv ./dist/** ../ngconsole/js/libs/spice/ &&
	cp -rv ./oeidp/** ../ngconsole/js/libs/oeidp/

```

![[%_~DHG9[WVG9Y`D%~_HRHXO.png]]

xshell5登录[欧拉](https://so.csdn.net/so/search?q=%E6%AC%A7%E6%8B%89&spm=1001.2101.3001.7020)22.03时报错：找不到匹配的host key 算法
[Xshell5登录报“找不到匹配的host key 算法“的错误_mosaicwang的博客-CSDN博客](https://blog.csdn.net/mosaicwang/article/details/131693377?spm=1001.2101.3001.6661.1&utm_medium=distribute.pc_relevant_t0.none-task-blog-2%7Edefault%7ECTRLIST%7ERate-1-131693377-blog-129684562.235%5Ev38%5Epc_relevant_sort_base3&depth_1-utm_source=distribute.pc_relevant_t0.none-task-blog-2%7Edefault%7ECTRLIST%7ERate-1-131693377-blog-129684562.235%5Ev38%5Epc_relevant_sort_base3&utm_relevant_index=1)

```bash
tar -zcvf "$output_zip_file" $files
tar -zxvf update_2023-09-21.tar.gz
tar -zxvf ./patch/update_2023-09-21.tar.gz -C update
```
[Linux中tar归档命令、zip压缩、gzip压缩、bzip2压缩_linux tar_欢喜躲在眉梢里的博客-CSDN博客](https://blog.csdn.net/m0_52165864/article/details/123998531)
[Linux笔记06-压缩解压命令_tar -zcf_浮尘笔记的博客-CSDN博客](https://blog.csdn.net/rxbook/article/details/106059408)
```bash
sudo lsof -i :端口号
```
# 外网环境搭建
```bash
# 大家测试外网映射功能如果没有环境的话也可以通过ssh的方式实现  
ssh -L 0.0.0.0:1443:172.16.65.143:443 -NC root@172.16.65.143  
  
# 上面的的命令就是把本地的65.145上面的1443端口的流量转发到了143环境的443端口，模拟的就是在路由器上面设置了一个端口映射1443 到443

# 业务层接口连上
ssh -L 0.0.0.0:1443:172.16.65.143:443 -NC root@172.16.65.143
# webspice接口连上
ssh -L 0.0.0.0:6082:172.16.65.143:6082 -NC root@172.16.65.143

# 连上桌面后，断开一次业务层的通道
# 即可模拟业务层接口断开，但是spice连上在

```
![[Pasted image 20230901094555.png]]
# 修改服务器时间
```bash
# 设置服务器时间
date -s "20220622 14:30:22"
# 同步服务器时间
yum install ntpdate
ntpdate -u cn.pool.ntp.org  
```

# shutdown
```bash
shutdown -r -t 5
```

```

[[汇总所有在线文档#^548d59|spice build]]

```js
yarn build
cp dist/oevdi.min.js ../ngconsole/js/libs/spice/
```

^b70ed2

[authorized_key – Adds or removes an SSH authorized key — Ansible Documentation](https://docs.ansible.com/ansible/2.9/modules/authorized_key_module.html)

# idp服务器配置文件

```bash
> http://172.16.65.147/
> oseasy@147
> /etc/thor/thor.conf
> oeidp.enable= false
```

# wsl2

[WSL2 配置代理 - 哔哩哔哩 (bilibili.com)](https://www.bilibili.com/read/cv22203257/)

```bash
> wsl --web-download
> wsl 安装 wsl2 wsl --update --web-download # WSL 安装发行版 wsl --install -d Ubuntu-22.04 --web-download
```

　　‍

# 终端业务

[终端连桌面业务详解--ShowDoc](http://192.168.0.161:4999/web/#/3/3848)

## token 失效条件

​![image](40%20-%20Obsidian/附件/Attachment/assets%206-zagger/image-20230706085205-41m19po.png)​

## 局域网追踪网络走向命令

　　​![image](40%20-%20Obsidian/附件/Attachment/assets%206-zagger/image-20230705084016-l62i7y8.png)​

　　局域网电脑中使用 58.48.71.131 连接，走到了局域网网关，然后直接 58.48.71.131 完成 

```bash
tracert 58.48.71.131
```

# 部署前端文档 #上传

```bash
ssh-copy-id -i ~/.ssh/id_rsa.pub root@192.168.0.161
scp -r dist/* root@192.168.0.161:/usr/share/nginx/html/fedoc
```

# consoleui 打包 bash 命令 #上传

```bash
PV=$(node -p 'require("./package.json").version')
tar cf $PV.tar.gz consoleui/package.json consoleui/dist
scp -r 0.0.106.tar.gz root@192.168.0.161:/usr/local/vsftpd-compose/vsftpd/data/oseasy/trunk/console_ui
```

# 服务器代码 #上传 | [[汇总所有在线文档#^ce3eb8|scp]]

```bash
scp -r js built resources views  css fonts includes view-front img init.html Cloud_r00t@172.16.201.47:/var/www/html                
scp -r js built resources views  css fonts includes view-front img init.html Cloud_r00t@172.16.65.151:/var/www/html
scp -r js built resources views  css fonts includes view-front img init.html root@172.16.65.143:/var/www/html
scp -r js built resources views  css fonts includes view-front img init.html tspace_path.json root@172.16.65.145:/var/www/html

# 5.6.1是docker版本：欧拉 系统 里面 docker版的 centos 系统 部署的服务器
#10240端口  
# root  
# ServerR00t
scp -P 10240 -r js built resources views  css fonts includes view-front img init.html tspace_path.json root@172.21.65.148:/var/www/html
ssh -p 10240 root@172.21.65.148
ssh root@172.21.65.148 oseasy@123早的 ServerR00t晚的
docker images
docker ps

ServerR00t
Vdi&Voi@r00t
```

^e6bdc2

# ssh 服务器代码 #上传 windows

```bash
scp -r dist/* root@172.16.101.22:/var/www/edaas/
scp -r js built resources views  css fonts includes view-front img init.html root@172.16.201.120:/var/www/html
oseasy@141
```


# 获取笔记本 WiFi 密码

```bash
netsh wlan show profiles name=HUAWEI-AF1UL2 key=clear 
netsh wlan show profiles name=zagger key=clear
```

# 安装git报错

```bash
scoop install -g git@2.39.2.windows.1  
Could not install git@2.39.2.windows.1 
Select-CurrentVersion: D:\Applications\Scoop\apps\scoop\current\lib\core.ps1:239 
Line |  239 |      return $null -ne (Select-CurrentVersion -AppName $ app -Global:$gl …
```

　　‍

# 启动weboeidpproxy服务

```bash
cd weboeidpproxy/ ./html5proxy --config=./spice.json --nova-config=/etc/nova/nova.conf
```

# #修改分支名称

```bash
git branch -m oldBranchName newBranchName 
git push origin :oldBranchName 
git push --set-upstream origin newBranchName
```

# #打tags

```bash
git tag -a 5.5.0-release -m '发布版本'
git push origin 5.5.0-release
git tag -l -n
# 表示自打tag以来有n次提交(commit)
git describe --tags 
# 删除远程tag
git push origin :refs/tags/v1.4-lw
git push origin --delete <tagname>

```

```bash
git describe --tags
git tag 5.3.2-vpc f6fe53e8a35c5c09a9eaab7113adc25de606ffd8 
git push --tags
```

参考链接：
1. [GIT 中如何打标签（git tag）_git打tag__Nino的博客-CSDN博客](https://blog.csdn.net/qq_21746331/article/details/120776710)
2. [git 生成版本号 git describe_我是榜样的博客-CSDN博客](https://blog.csdn.net/zhangpeng_linux/article/details/85858841)
3. [git tag 打标签（我看过最透彻的文章）_黒客与画家的博客-CSDN博客](https://blog.csdn.net/TIAN20121221/article/details/119737274)


# 共享目录，voi 客户端包

```bash
ftp://172.16.227.19/CTSC%20files/%B2%FA%C6%B7%B0%E6%B1%BE/E-VOI/V5.5/VOI/5.5.0.6628/x86/
user
123456

ftp://172.16.227.19/CTSC%20files/%B2%FA%C6%B7%B0%E6%B1%BE/E-VOI/0_VOI%BD%CC%D3%FD%B0%E6/5.5.1/5.5.1-64/x86/
```

# 融合客户端：设置密码

```bash
 osadmin
```

# 融合端：切换命令行：

```bash
C+ALT+f1-f7 切换命令行
C+ALT+f7 切回图形界面
命令行 root账号，密码3vclientroot

端对端同传
网络要设置静态网络
要设置桥接模式
桌面不自动更新，不然会影响测试

虚拟机切换图形界面和命令行的快捷键
虚拟机centos：
ctrl+alt+f3：从图形界面进入命令行
ctrl+alt+f1：从命令行进入图形界面
虚拟机教育版融合终端：
ctrl+alt+f7：从命令行进入图形界面
ctrl+alt+f1：从图形界面进入命令行


虚拟机两种联网方式：
NAT+DHCP
桥接+静态地址

PING (Packet Internet Grope)，因特网包探索器
centos6.5设置桥接模式，虚拟机无法ping通宿主机，主机可以ping通虚拟机
需要解决！！！
(5条消息) 虚拟机ping不通的几种原因及解决办法_萌褚的博客-CSDN博客_虚拟机ping主机ping不通
```

# weboeidp 172.19.20.119 hzj 账号

```bash
ssh Cloud_r00t@172.19.20.119
Vdi&Voi@r00t
cd weboeidpproxy
./html5proxy --config=./spice.json --nova-config=/etc/nova/nova.conf
```

# weboeidp 172.16.201.136 getConnectInfo 补丁 nwy admin1

```bash
 var url = '/api/instances/connection'; var json = { instance_id: t.uuid }; s.a.post(url, json).then( function (resp) { t.instance = resp.data.instance; if (!t.instance) { return setTimeout(e, 500) } ;var data = t.instance.connect; data.port = 6082; var connectInfo = t.connectInfo; var status = connectInfo.status; if (status && status === 'ERROR') { self.onlyReset = true; return } ;t.instance = connectInfo.instance; console.log('newToken:', data.token) ;resolve(data) }, function () {} )
```

# tspace 服务，服务器修改服务名称，避免其自动重启

```bash
ssh root@172.16.65.145
ServerR00t
 mv /usr/lib/venvs/vdi/bin/tspace-agent /usr/lib/venvs/vdi/bin/tspace-agent_bak
 systemctl stop tspace-agent
mv /usr/lib/venvs/vdi/bin/tspace-agent_bak /usr/lib/venvs/vdi/bin/tspace-agent
systemctl start tspace-agent
```

　　find [路径] [条件] 文件名原文链接：[https://www.linuxcool.com/find](https://www.linuxcool.com/find)

```bash
find / -name "*.mp4" -exec rm -rf {} \;
# 搜索整个路径
find . -iregex '.*client.*'
# 搜索文件名 -name 用于指定区分大小写的文件名；然后是搜索字符串。默认情况下，搜索字符串按字面意思处理：除非你使用正则表达式语法，否则 find 命令搜索的文件名正是你在引号之间输入的字符串。
find . -iname '*client*'
# 将模式使用“或”（-o）进行组合。括号需要转义，以便使 find 命令而不是 shell 程序尝试解释它们。
find . \( -iname 'jpeg' -o -iname '*png' -o -iname '*jpg' \) # 查找项目中所有图片
find . \( -iname '*jpeg' -o -iname '*jpg' \) -type f # 查看文件
find . \( -iname '*jpeg' -o -iname '*jpg' \) -type d # 查看图片
find . \( -iname '*jpeg' -o -iname '*jpg' \) -type f -mtime -7 # 一周内修改过的图片文件
# xargs 命令从标准输入流中获取参数，并基于它们执行命令。
# 假设你要将上周修改过的家目录中的所有 JPEG 文件复制到 U 盘，以便插到电子相册上。假设你已经将 U 盘挂载到 /media/photo_display
find ~ \( -iname '*jpeg' -o -iname '*jpg' \) -type f -mtime -7 -print0 | xargs -0 cp -t /media/photo_display
# 在当前目录中 root 用户拥有的文件，以及不被指定用户（在本例中为 shs）所拥有的文件。
find . -user root -ls
# 接下来的命令显示具有 777 权限的非符号链接文件：
sudo find /home -perm 777 ! -type l -ls
# 下面的命令将查找具有特定权限的文件
find . -perm 750 -ls
# 以下命令将查找大小超过千兆字节的文件
sudo find / -size +1G -ls
# find 命令是如何描述文件类型的，就可以通过文件类型来查找文件。
# b = 块设备文件
# c = 字符设备文件
# d = 目录
# p = 命名管道
# f = 常规文件
# l = 符号链接
# s = 套接字
# D = 门（仅限 Solaris）
# 我们要寻找符号链接和套接字：
find . -type l -ls
find . -type s -ls
#  inode 号来搜索文件
find . -inum 397132 -ls
# 另一种通过 inode 搜索文件的方法是使用 debugfs 命令。在大的文件系统上，这个命令可能比 find 快得多，您可能需要安装 icheck。
sudo debugfs -R 'ncheck 397132' /dev/sda1
# 我们从主目录（~）开始，限制搜索的深度（即我们将搜索子目录的层数），并只查看在最近一天内创建或修改的文件（mtime 设置）。
find ~ -maxdepth 2 -mtime -1 -ls
# 使用 -exec 选项，在您使用 find 命令找到文件后可以以某种方式更改文件。您只需参照 -exec 选项即可运行相应的命令。
find . -name runme -exec chmod 700 {} \;
find . -name runme -ls
# 在这条命令中，{} 代表文件名。此命令将更改当前目录和子目录中任何名为 runme 的文件的权限。
# 还可以通过其他条件进行搜索：文件的修改时间、所有者、权限等。
sudo find /home -user peanut # 根据用户查找文件
sudo find /home -perm 777 # 根据权限查找文件
sudo find /home -mtime +100 # 根据修改时间查找文件
sudo find /var/log -newer /var/log/syslog 通过比较修改时间查找文件
find / -type f ! -perm 777 # Find all the files without permission 777.
# Find all Read-Only files.
find / -perm /u=r
# Find all Executable files.
find / -perm /a=x
# Find all 777 permission files and use the chmod command to set permissions to 644
find / -type f -perm 0777 -print -exec chmod 644 {} \;
# 寻找重复的文件
#如果您正在清理磁盘空间，则可能需要删除较大的重复文件。确定文件是否真正重复的最好方法是使用 
# fdupes 命令。此命令使用 md5 校验和来确定文件是否具有相同的内容。使用 
# -r（递归）选项，
# fdupes 将在一个目录下并查找具有相同校验和而被确定为内容相同的文件。
# 如果以 root 身份运行这样的命令，您可能
```

# 改變所屬群組, chgrp:change group

```bash
chgrp [-R] dirname/filename ...
選項與參數：
-R : 進行遞迴(recursive)的持續變更，亦即連同次目錄下的所有檔案、目錄
     都更新成為這個群組之意。常常用在變更某一目錄內所有的檔案之情況。
範例：
[root@study ~]# chgrp users initial-setup-ks.cfg
[root@study ~]# ls -l
-rw-r--r--. 1 root users 1864 May  4 18:01 initial-setup-ks.cfg
[root@study ~]# chgrp testing initial-setup-ks.cfg
chgrp: invalid group:  `testing' <== 發生錯誤訊息囉～找不到這個群組名～
```

# 改變檔案擁有者, chown:change owner

```bash
chown [-R] 帳號名稱 檔案或目錄
[root@study ~]# chown [-R] 帳號名稱:群組名稱 檔案或目錄
選項與參數：
-R : 進行遞迴(recursive)的持續變更，亦即連同次目錄下的所有檔案都變更
範例：將 initial-setup-ks.cfg 的擁有者改為bin這個帳號：
[root@study ~]# chown bin initial-setup-ks.cfg
[root@study ~]# ls -l
-rw-r--r--. 1 bin  users 1864 May  4 18:01 initial-setup-ks.cfg

範例：將 initial-setup-ks.cfg 的擁有者與群組改回為root：
[root@study ~]# chown root:root initial-setup-ks.cfg
[root@study ~]# ls -l
-rw-r--r--. 1 root root 1864 May  4 18:01 initial-setup-ks.cfg
```

```bash
[root@study ~]# cp .bashrc .bashrc_test
[root@study ~]# ls -al .bashrc*
-rw-r--r--. 1 root root 176 Dec 29  2013 .bashrc
-rw-r--r--. 1 root root 176 Jun  3 00:04 .bashrc_test   <==新檔案的屬性沒變
```

　　‍

# 改變權限, chmod

```bash
Linux檔案的基本權限就有九個，分別是owner/group/others三種身份各有自己的read/write/execute權限， 先複習一下剛剛上面提到的資料：檔案的權限字元為：『-rwxrwxrwx』， 這九個權限是三個三個一組的！其中，我們可以使用數字來代表各個權限，各權限的分數對照表如下：
r:4w:2x:1
每種身份(owner/group/others)各自的三個權限(r/w/x)分數是需要累加的，例如當權限為： [-rwxrwx---] 分數則是：
owner = rwx = 4+2+1 = 7group = rwx = 4+2+1 = 7others= --- = 0+0+0 = 0
[root@study ~]# chmod [-R] xyz 檔案或目錄
選項與參數：
xyz : 就是剛剛提到的數字類型的權限屬性，為 rwx 屬性數值的相加。
-R : 進行遞迴(recursive)的持續變更，亦即連同次目錄下的所有檔案都會變更
[root@study ~]# ls -al .bashrc
-rw-r--r--. 1 root root 176 Dec 29  2013 .bashrc
[root@study ~]# chmod 777 .bashrc
[root@study ~]# ls -al .bashrc
-rwxrwxrwx. 1 root root 176 Dec 29  2013 .bashrc
```

　　符號類型改變檔案權限還有一個改變權限的方法呦！從之前的介紹中我們可以發現，基本上就九個權限分別是(1)user (2)group (3)others 三種身份啦！那麼我們就可以藉由 u, g, o 來代表三種身份的權限！此外， a 則代表 all 亦即全部的身份！那麼讀寫的權限就可以寫成 r, w, x 囉！也就是可以使用底下的方式來看：

|chmod|ugoa|+(加入)-(除去)=(設定)|rwx|檔案或目錄|
| -----| ----| ---------------------| ---| ----------|

```bash
[root@study ~]# chmod  u=rwx,go=rx  .bashrc
# 注意喔！那個 u=rwx,go=rx 是連在一起的，中間並沒有任何空白字元！
[root@study ~]# ls -al .bashrc
-rwxr-xr-x. 1 root root 176 Dec 29  2013 .bashrc
[root@study ~]# ls -al .bashrc
-rwxr-xr-x. 1 root root 176 Dec 29  2013 .bashrc
[root@study ~]# chmod  a+w  .bashrc
[root@study ~]# ls -al .bashrc
-rwxrwxrwx. 1 root root 176 Dec 29  2013 .bashrc
[root@study ~]# chmod  a-x  .bashrc
[root@study ~]# ls -al .bashrc
-rw-rw-rw-. 1 root root 176 Dec 29  2013 .bashrc
[root@study ~]# chmod 644 .bashrc  # 測試完畢得要改回來喔！
```

```bash
linux权限0777代表的含义
0777前面的0是代表suid和guid的
suid意味着如果某个用户对属于自己的shell脚本设置了这种权限，那么其他用户在执行这一脚本时也会具有其属主的相应权限。
guid则表示执行相应脚本的用户将具有该文件所属用户组中用户的权限。
下面举个例子
-rwxr-xr-x 1 root root 12 09-02 15:21 my_test.sh
上面的mysql_test.sh文件权限是所属用户（root）是7
如果设置了suid，那么其他任何用户的权限都是7，
如果设置了guid，那么任何用户的权限都是5。
如何设置suid和guid：
设置suid就是把0变为4，设置guid就把0变为2，如果都设置那就是6了
```

　　‍

# 定位文件和应用

```bash
which 命令只会在系统定义的搜索路径中，查找可执行的文件，通常用于识别命令。如果您对输入 
which 时会运行哪个命令感到好奇，您可以使用命令 
which which，它会指出对应的可执行文件。

locate 命令更大方一点，它可以查找任意数量的文件，但它也有一个限制：仅当文件名被包含在由 
updatedb 命令构建的数据库时才有效。该文件可能会存储在某个位置，如 
/var/lib/mlocate/mlocate.db，但不能用 
locate 以外的任何命令读取。这个文件的更新通常是通过每天通过 cron 运行的 
updatedb 进行的。
```

　　‍

# grep使用方法

　　grep 使用格式： grep [OPTIONS] PATTERN [FILE...]

　　grep 查找文件包含某个字符串的文件名

```bash
find -type f -name '*.js' | xargs grep -rl "loss_spice_info_tips"

# grep查找 httpd服务器 并杀掉服务
ps -ef | grep httpd | grep -v 'grep' | awk '{print $2}' |xargs kill
# spicehtml5proxy代理可以让不同计算节点的桌面都在同一个ip上访问 用户网络策略设置错误导致的 其他计算节点的虚拟机无法访问的问题
systemctl status spicehtml5proxy.service
tail -f /var/log/html5proxy/spice.log
# 搜索
grep -rn 'bootstrap' ./ --exclude-dir={.git,node_modules,resources,built} --exclude={'*bundle*','*.min*',angular.js}
```

没有证书的警告

![[3%RR_1SP42(6{)_06%9QTC1.png]]

# 查看 spice 的日志

```bash
 tail -f /var/log/html5proxy/spice.log
```

# 正则表达式：

```bash
(?<=<(\w+)>).*(?=<\/\1>)

报错：改为这个就不会报错了(?<=<(td)>).*(?=<\/\1>)
```

　　[regex - lookhehind assertion length error - Stack Overflow](https://stackoverflow.com/questions/48628410/lookhehind-assertion-length-error)

　　​![image](40%20-%20Obsidian/附件/Attachment/assets%206-zagger/image-20230705091201-pfofyc9.png)​

```js
var str= '1231345345356'

str.replace(/\B(?=(?:\d{3})+\b)/g, ',');
```

```js
<(\w+)\s*(\w+(=('|&quot;).*?\4)?\s*)*>.*?
```

　　    [ 举例 3：表达式 &quot;((?!\bstop\b).)+&quot; 在匹配 &quot;fdjka ljfdl stop fjdsla fdj&quot; 时](http://www.regexlab.com/zh/workshop.htm?pat=%28%28%3F%21%5Cbstop%5Cb%29%2E%29%2B&txt=fdjka+ljfdl+stop+fjdsla+fdj)

　　将从头一直匹配到 "stop" 之前的位置，如果字符串中没有 "stop"，则匹配整个字符串。

　　(?!\bstop\b) 匹配右侧不能是stop单词的缝隙，从左侧缝隙开始，一个个缝隙开始判断，在stop的s的左侧缝隙就不符合此缝隙约束的条件

　　‍

# 远程服务器

```bash
ssh root@172.16.65.141
oseasy@141
cd /var/www/html
ssh Cloud_r00t@172.16.201.47
Vdi&Voi@r00t
Cloud_r00t
Vdi&Voi@r00t
su root
ServerR00t
vim /var/www/html/views/vdi/help/activeAuth.html
```

# dms:开发服务器

```bash
http://172.16.162.200:7735  http://172.16.65.124:7735
```

# 服务器查看日志：

```bash
tail -f -n 10 /etc/thor/log/thorconsole.log
```

# 重启 supervisor 服务：

```bash
systemctl restart thor-supervisor
```

# ssh-copy-id -i ~/.ssh/id_rsa.pub [zhangyao@172.16.103.196](mailto:zhangyao@172.16.103.196)

```bash
ssh-copy-id -i ~/.ssh/id_rsa.pub zhangyao@172.16.103.196
windows
cat ~/.ssh/id_rsa.pub | ssh Cloud_r00t@172.16.201.47 "mkdir -p ~/.ssh && cat >> ~/.ssh/authorized_keys"
chmod 644 ~/.ssh/authorized_keys
```

# console-vscode 插件

```bash
ctrl + alt + l 选中变量之后，使用这个快捷键生成 console.log
alt + shift + c 注释所有 console.log
alt + shift + u 启用所有 console.log
alt + shift + d 删除所有 console.log
```

# mac 上传代码到服务器 docker 中指定端口

```bash
rsync -avz -e 'ssh -p 10240' js built resources views p css fonts includes img init.html root@172.16.201.9:/var/www/html/
直接进入服务器的10240端口，进入docker中。
```

# ssh 动态

```bash
ssh Cloud_r00t@59.175.233.194 -p8181
我把ssh的口放开，你可以走remote_ssh的方式进行远程开发
这个对应的转发到了172.16.200.222环境
也可以通过ssh -D10101 Cloud_r00t@59.175.233.194 -p8181的方式启用本地socks5端口
```



# 端口占用问题解决

```bash
netstat -aon|findstr 8088
```

```bash
#命令格式：lsof -i :端口
lsof -i:8080
```

# 端口转发

```bash
待验证
先动态转发本地端口10101到59.175.233.194的8181端口上
ssh -D10101 Cloud_r00t@59.175.233.194 -p8181
```

### Vdi&[Voi@r00t](http://Voi@r00t)

　　​![image](40%20-%20Obsidian/附件/Attachment/assets%206-zagger/image-20230705092131-dvexqxp.png)​

　　本地端口转发：是将本地的监听一个端口通过 ssh 转发到远端主机（服务器）的某个端口。（自己本地启端口给远端用）远程端口转发：是在远端主机上监听一个端口，所有的访问远程主机的这个端口的数据都会通过 ssh 转发到本地对应的端口（让远端自己启端口给自己用）

　　首先，SSH 端口转发自然需要 SSH 连接，而 SSH 连接是有方向的，从 SSH Client 到 SSH Server 。而我们的应用也是有方向的，比如需要连接 LDAP Server 时，LDAP Server 自然就是 Server 端，我们应用连接的方向也是从应用的 Client 端连接到应用的 Server 端。如果这两个连接的方向一致，那我们就说它是本地转发。而如果两个方向不一致，我们就说它是远程转发。

　　1、Bug 产生原因阐述：代码中两年前王川用的就是 terminalCount，现在魏洪说要用 client_count，向他确认过是否其他地方使用的 terminalCount 是否也需要同步更改，没有正面回答。大概率是后端因为什么原因，terminalCount 字段数量不对了，又无法解决就需要更换字段了。

　　​![image](40%20-%20Obsidian/附件/Attachment/assets%206-zagger/image-20230705092150-90qfurd.png)​

　　2、解决思路：3、影响范围：4、Bug 归属人修改原因：长度不得小于 20 个字符

　　[git reset 详解 |reset|commit (qq.com)](https://xw.qq.com/cmsid/20200224A09I2300)

　　​![image](40%20-%20Obsidian/附件/Attachment/assets%206-zagger/image-20230705092204-535rfto.png)​

```bash
ssh zagger@外网地址 -p 端口
scp -r js views built v img css includes fonts ssh_terminal vnc zips types Cloud_r00t@172.16.201.47:/var/www/html
Vdi&Voi@r00t
```

# 清空 chatgpt 缓存

```bash
javascript:window.localStorage.removeItem(Object.keys(window.localStorage).find(i=>i.startsWith('@@auth0spajs')))
```

# [环境配置相关](siyuan://blocks/20230705103954-dsr1hc8 "环境配置相关-不常用")

　　‍


上传服务器145脚本