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


--hive-site.xml 在hive安装目录下的conf目录下新建文件
---
配置远程的mysql
<?xml version="1.0" encoding="UTF-8" standalone="no"?>
<?xml-stylesheet type="text/xsl" href="configuration.xsl"?>
<configuration>
  <property>
  	<name>javax.jdo.option.ConnectionURL</name>
  	<value>jdbc:mysql://ip:3306/hive</value>
  </property>
  <property>
  	<name>javax.jdo.option.ConnectionDriverName</name>
  	<value>com.mysql.jdbc.Driver</value>
  </property>
  <property>
  	<name>javax.jdo.option.ConnectionUserName</name>
  	<value>root</value>
  </property>
  <property>
  	<name>javax.jdo.option.ConnectionPassword</name>
  	<value>123456</value>
  </property>
</configuration>
--hive.env.sh 配置hadoop的路径
执行hive命令-先把路径加到path路径下
需要先启动hadoop
--cli命令
---
hive
hive --service cli
清屏
ctrl + L 或者!clear
查看数据仓库中的表
show tables; --这个是注释
查看数据仓库中的内置的函数
show functions;
查看表结构
desc 表名;
查看HDFS上的文件1
dfs -ls 目录; dfs -ls -R /user;
执行操作系统的命令
!命令;
执行HQL语句
select *** from ***;
执行SQL的脚本
source SQL文件; source /root/my.sql
进入静默模式
hive -s

--错误
---
1、创建表失败，return code 1 from org.apache.hadoop.hive.ql.exec.DDLTask. MetaException
mysql的hive数据库的字符集需要改为latin1
https://blog.csdn.net/u011812294/article/details/53674720
2、去掉native-hadoop的警告
https://blog.csdn.net/l1028386804/article/details/51538611
3、启动hadoop没有datanode节点
删掉temp的文件重新hadoop namenode -format
https://blog.csdn.net/love666666shen/article/details/74350358

Hive入门小结
https://www.cnblogs.com/lym0805/p/7684549.html

