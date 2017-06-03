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
 
 


