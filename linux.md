#查看linxu
uname -a (linux查看版本当前操作系统的内核)
cat /proc/version
cat /etc/issue cat /etc/redhat-release
cat /proc/cpuinfo lscpu 

#vi查找时不区分大小写
\c

#find查找时不区分大小写
-iname 

#线程
ps -T -p pid
top -H -p pid

#vi全部删除
命令模式下输入:.,$d  回车从当前行到末尾行全部删除
gg移动到首行

#vi下撤销操作
u

#sort按列排序
-k 1 //按第一列

#UNIQ 排重
|sort|uniq 
|sort|uniq -c 获取每条重复记录出现的次数

#traceroute

#lsof
根据进程pid差端口 lsof -i|grep pid
根据端口查pid     lsof -i:port
根据用户查pid和端口 lsof -i|grep user
根据pid查端口       netstat -anp|grep pid
根据端口查pid       netstat -anp|grep port

#grep
-v 过滤
"a\|b" a或b
-w 精确匹配
-E 正则表达式
在某个目录下后缀为java的文件中查找某个关键字
比如 grep abc --include "*.java" /home/yewer/git  -r


#生成10M的文件
dd if=/dev/zero of=test.txt bs=1M count=10

#exec 和 xargs
find / -name test -exec rm -rf {} \;
find / -name test |xargs rm -rf

#mykill
ps -ef|grep idea|grep -v grep|awk {'print $2'}|xargs kill -9

A服务器上用nc监听udp模式下的1080
nc -ulp 8888

B客户端在udp模式下给A的1080端口发消息
nc -u A服务器IP 8888

#curl 访问https页面
加参数 -k --insecure

#计算一个文件的md5
md5sum

#加延时 丢包
tc qdisc add dev eth0 root netem delay 100ms
将 eth0 网卡的传输设置为延迟100 毫秒发送
tc qdisc add dev eth0 root netem delay 100ms 10ms
将 eth0 网卡的传输设置为延迟100 加减10 （90～100随机）毫秒发送
tc qdisc add dev eth0 root netem delay 100ms 10ms 30%
该命令将 eth0 网卡的传输设置为 100ms ,同时,大约有 30% 的包会延迟 ± 10ms 发送
模拟网络丢包:
tc qdisc add dev eth0 root netem loss 1%
该命令将 eth0 网卡的传输设置为随机丢掉 1% 的数据包
tc qdisc add dev eth0 root netem loss 1% 30%
该命令将 eth0 网卡的传输设置为随机丢掉 1% 的数据包,成功率为 30%
tc qdisc del dev eth0 root
删除tc规则


#监控
iostat
sar -u 3 5 
iftop
ifstat
nmon
dstat

#直接看jar包
vim
less

#grep 后面带上 -A -B -C参数可以多显示几行
grep -A 5 显示匹配内容和后面5行
grep -B 5 显示匹配内容和前面5行
grep -C 5 显示匹配内容和前后5行

#systemctl
systemctl list-unit-files --type=service

#chkconfig
普通的shell脚本不能chkconfig --add
要在前面加两句
#chkconfig: 2345 80 90
#description:auto_run


#计算
echo $((1024*2))
expr 15  / 3
十进制转16进制 printf '%x' 15
16进制转10进制 echo $((16#e))
2进制转10进制 echo $((2#1010101))



#硬盘检测
smartctl --smart=on --offlineauto=on --saveauto=on /dev/sda #启动smart 
sudo smartctl -A /dev/sda
sudo badblocks -s -v /dev/sdb    #检测坏道    
sudo hdparm -Tt /dev/sda #测试数度

#2T以上硬盘使用GTP
sudo parted /dev/sdb        
sudo mkfs.ext4 /dev/sdb1   
sudo mkfs.ext4 /dev/sdb2

编辑/etc/fstab文件
/dev/sdb1                /home/yewer/cloud        ext4    defaults        0 1
/dev/sdb2                /home/yewer/data         ext4    defaults        0 1
mount -a

#tcpdump 
在shell中 过滤条件中使用()时，需要加转义\

#yum配置安装源
/etc/yum.repos.d/xx.repo
#sudo：yum-config-manager：command not found
yum -y install yum-utils

#rpm
rpm -ivh 包全名
rpm -e 卸载
rpm -q -a 查询所有安装的软件

视频

#内网穿透
sudo systemctl enable --now snapd.socket
sudo ln -s /var/lib/snapd/snap /snap
sudo snap install zerotier 

sudo zerotier-cli join 52b337794fb708aa
sudo zerotier-cli listnetworks
( wait until you get an Earth IP )
ping earth.zerotier.net
( you should now be able to ping our Earth test IP )
Leave "Earth":

sudo zerotier-cli leave 52b337794fb708aa
List VL1 peers:

sudo zerotier-cli listpeers