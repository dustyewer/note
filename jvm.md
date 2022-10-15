#jvm
MinHeapFreeRadio 占用heap总量的最小比率 40
MaxHeaoFreeRadio 占用heap总量的最大比率 70

内存使用超过70% 自动扩容，降到40%，自动缩容

默认 新生代：老年代 1:2 ,伊甸园：幸存者 8:1:1
默认 堆内存 初始容量为物理内存的1/64 最大 物理内存的1/4

伊甸园区满 minorgc
老年代，方法区 空间不足 fullgc

-Xms10g -Xmx10g

jstack -l pid

jmap -histo pid

jstat (-gc -gcuitl -gccapacity) pid

jps -v

jmpa -dump
这个命令执行jvm会将整个heap的信息dump到一个文件，heap比较大，会导致过程耗时很长，会暂停应用

jmap -permstat
jvm会统计perm区的状况，会暂停应用

jmap -histo:live
jvm会先触发gc，再统计信息