# 可以通过tcpdump查看指定机器指定端口是否有数据发往该处。

tcpdump -i eth0 
查看网卡eth0处理的数据
测试：本地写一个广播程序，一直向6000端口发送数据udp方式， 发送字符串长度为6。
通过tcpdump -i eth0抓取的内容含有如下内容：
22:06:17.181258 IP VM_143_centos.36249 > 255.255.255.255.6000: UDP, length 6

tcpdump port 6000
抓取内容如下
32 packets dropped by kernel
[root@VM_176_143_centos ~]# tcpdump port 6000
tcpdump: verbose output suppressed, use -v or -vv for full protocol decode
listening on eth0, link-type EN10MB (Ethernet), capture size 262144 bytes
22:11:59.238233 IP VM__143_centos.36249 > 255.255.255.255.6000: UDP, length 6
22:12:00.238444 IP VM__143_centos.36249 > 255.255.255.255.6000: UDP, length 6
22:12:01.241294 IP VM__143_centos.36249 > 255.255.255.255.6000: UDP, length 6

tcpdump -i eth0 port 6000  and host x.x.x.x -A
其中-A 表示封包的內容以 ASCII 显示，通常用来捉取 WWW 的网页封包资料。

tcpdump -i eth0 port 6000  and host x.x.x.x  -e -A -q -vv -nn   这个输出的就比较详细了。



# 参考
http://www.cnblogs.com/maifengqiang/p/3863168.html
http://www.jianshu.com/p/a62ed1bb5b20