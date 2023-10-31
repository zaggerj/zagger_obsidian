# service httpd start

　　service httpd start

　　ps -ef \| grep httpd \| grep -v 'grep' \| awk '{print \$2}' \| xargs kill

　　ps -ef \| grep httpd \| grep -v 'grep'

　　Mac上用法：

　　netstat -anv \| grep 8080

　　netstat -anvp tcp \| grep LISTEN \| grep '808.'
