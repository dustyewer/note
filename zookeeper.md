#并不存在用户管理的概念
#普通用户登录后就存在
addauth digest user:password

#查权限
getAcl /test

CREATE   c 可以创建子节点
DELETE   d 可以删除子节点（仅下一级节点）
READ     r 可以读取节点数据及显示子节点列表
WRITE    w 可以设置节点数据
ADMIN    a 可以设置节点访问控制列表权限


#设置权限,设置以用户模式的权限要先以用户登录
setAcl /test auth:user:password:cdrwa

#设置多个模式的权限用,分开
setAcl /test auth:user:password:cdrwa,ip:127.0.0.1:cdrwa,world:anyone:cdrwa

#digest是密文密码模式,感觉只是这条命令里密码是加密的而已，用户登录还是和普通的一样，这里的密文哪里来呢？得用auth模式设置一下，再用getAcl查看下
setAcl /test digest:user:tpUq/4Pn5A64fVZyQ0gOJ8ZWqkY=:cdrwa


#zookeeper的超级管理员
#linux下生成密码
echo -n super:super | openssl dgst -binary -sha1 | openssl base64
gG7s8t3oDEtIqF6DM9LlI/R+9Ss=
#修改Zookeeper的启动脚本zkServer.sh或zkServer.cmd  添加 "-Dzookeeper.DigestAuthenticationProvider.superDigest=super:gG7s8t3oDEtIqF6DM9LlI/R+9Ss="   例如：
nohup "$JAVA" "-Dzookeeper.log.dir=${ZOO_LOG_DIR}" "-Dzookeeper.root.logger=${ZOO_LOG4J_PROP}" "-Dzookeeper.DigestAuthenticationProvider.superDigest=super:gG7s8t3oDEtIqF6DM9LlI/R+9Ss=" \
-cp "$CLASSPATH" $JVMFLAGS $ZOOMAIN "$ZOOCFG" > "$_ZOO_DAEMON_OUT" 2>&1 < /dev/null &
#重启后登录认证，可以操作所有节点
addauth digest super:super