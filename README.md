# Hive
--下载
---
http://archive.apache.org/dist/hive/hive-0.13.0/
创建linux用户useradd -m testhive 创建用户同时创建home/testhive目录
删除用户userdel -r testhive 删除用户同时删除文件

--安装hadoop
---
先要安装hadoop，注入如果使用了主机名需要修改slaves文件的值为主机名
解压配置jdk和hadoop和hive-先开hadoop
hive不需要其他的配置了
export JAVA_HOME=/home/testhadoop/jdk1.8.0_131
export JRE_HOME=$JAVA_HOME/jre
export HADOOP_HOME=/home/testhadoop/hadoop-2.8.3
export CLASSPATH=$JAVA_HOME/lib:$JRE_HOME/lib:$CLASSPATH
export PATH=$JAVA_HOME/bin:$JRE_HOME/bin:$HADOOP_HOME/bin:$HADOOP_HOME/sbin:$PATH

export HIVE_HOME=/home/testhadoop/apache-hive-0.13.0-bin
export PATH=$HIVE_HOME/bin:$PATH
source ~/.bashrc

--安装hive
---
嵌入模式
在任意目录下执行hive，则在当前目录下生产metastroe_db目录
远程模式和本地模式很类似
使用mysql
cmd 进入mysql的bin目录下
mysql -uroot -p123456
create database hive;
show databases;
