## 1. 下载hbase安装包

自己到官网下载，我下载的是一个稳定版的hbase。
链接地址为：http://ftp.meisei-u.ac.jp/mirror/apache/dist/hbase/stable/hbase-1.2.5-bin.tar.gz
看清楚，这里是以 bin 结尾的已经编译好的文件，还有一种是以src结尾的源码文件，如果你愿意折腾就下载源码自己动手编译。

## 2.解压、改名、自定义安装位置

（1）解压 ：tar -zxvf hbase-1.2.5-bin.tar.gz

（2）解压完成后是一个hbase-1.2.5的文件夹，改不改名随你，为了方面还是改了好

mv  hbase-1.2.5  hbase

（3）选择一个你想安装hbase的位置，将hbase文件夹移动到那里，我是在/usr/local/下建立了一个 MyHadoop文件夹存放所有关于hadoop生态圈的所有东西，
以方便日后管理。

 mv hbase /usr/local/MyHadoop
 
 ## 3.添加环境变量
 
 打开/etc/profile文件，最后添加以下内容保存，并使之立刻生效
 export HBASE_HOME=/usr/local/MyHadoop/hbase 
 
 export PATH=$PATH:$HBASE_HOME/bin

 shell 命令:
 
 `echo "export HBASE_HOME=/usr/local/MyHadoop/hbase 
       export PATH=$PATH:$HBASE_HOME/bin" >>/etc/profile
 `
 
  使之生效：
  
 `
 source /etc/profile
 `

 
 
 ## 4.修改配置文件
 
 修改配置比较费神，因为这个分　单机　伪分布　和集群所以相对较难
 
 
 ＃＃＃　单机配置
 
 1.不管是什么模式，你都需要编辑 conf/hbase-env.sh来告知HBase java的安装路径.在这个文件里你还可以设置HBase的运行环境，诸如 heapsize和其他 JVM有关的选项, 还有Log文件地址，等等. 设置 JAVA_HOME指向 java安装的路径.
 
 在单机模式中，HBase使用本地文件系统，而不是HDFS ，所有的服务和zooKeeper都运作在一个JVM中。zookeep监听一个端口，这样客户端就可以连接HBase了。
 
 2.需要先编辑 conf/hbase-site.xml 去配置hbase.rootdir，来选择HBase将数据写到哪个目录 .
 
｀ 
<?xml version="1.0"?>
<?xml-stylesheet type="text/xsl" href="configuration.xsl"?>
<configuration>
  <property>
    <name>hbase.rootdir</name>
    <value>file:///DIRECTORY/hbase</value>
  </property>
</configuration>
｀
 file:///DIRECTORY/hbase　这里替换成你期望写文件的目录. 默认 hbase.rootdir 是指向 /tmp/hbase-${user.name} ，也就说你会在重启后丢失数据(重启的时候操作系统会清理/tmp目录)，你可以自己选择一个本地目录即可，也可以放到hdfs上，这在后面伪分布和集群搭建上会提及。
 
 
 
 
 
 
 
 
 
 
 
 

