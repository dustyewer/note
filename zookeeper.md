#���������û�����ĸ���
#��ͨ�û���¼��ʹ���
addauth digest user:password

#��Ȩ��
getAcl /test

CREATE   c ���Դ����ӽڵ�
DELETE   d ����ɾ���ӽڵ㣨����һ���ڵ㣩
READ     r ���Զ�ȡ�ڵ����ݼ���ʾ�ӽڵ��б�
WRITE    w �������ýڵ�����
ADMIN    a �������ýڵ���ʿ����б�Ȩ��


#����Ȩ��,�������û�ģʽ��Ȩ��Ҫ�����û���¼
setAcl /test auth:user:password:cdrwa

#���ö��ģʽ��Ȩ����,�ֿ�
setAcl /test auth:user:password:cdrwa,ip:127.0.0.1:cdrwa,world:anyone:cdrwa

#digest����������ģʽ,�о�ֻ�����������������Ǽ��ܵĶ��ѣ��û���¼���Ǻ���ͨ��һ��������������������أ�����authģʽ����һ�£�����getAcl�鿴��
setAcl /test digest:user:tpUq/4Pn5A64fVZyQ0gOJ8ZWqkY=:cdrwa


#zookeeper�ĳ�������Ա
#linux����������
echo -n super:super | openssl dgst -binary -sha1 | openssl base64
gG7s8t3oDEtIqF6DM9LlI/R+9Ss=
#�޸�Zookeeper�������ű�zkServer.sh��zkServer.cmd  ��� "-Dzookeeper.DigestAuthenticationProvider.superDigest=super:gG7s8t3oDEtIqF6DM9LlI/R+9Ss="   ���磺
nohup "$JAVA" "-Dzookeeper.log.dir=${ZOO_LOG_DIR}" "-Dzookeeper.root.logger=${ZOO_LOG4J_PROP}" "-Dzookeeper.DigestAuthenticationProvider.superDigest=super:gG7s8t3oDEtIqF6DM9LlI/R+9Ss=" \
-cp "$CLASSPATH" $JVMFLAGS $ZOOMAIN "$ZOOCFG" > "$_ZOO_DAEMON_OUT" 2>&1 < /dev/null &
#�������¼��֤�����Բ������нڵ�
addauth digest super:super