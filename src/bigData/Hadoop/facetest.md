# 常用端口号及配置文件

- hadoop3.x
  - HDFS NameNode 内部常用端口：8020/9000/9820
  - HDFS NameNode 对用户的查询端口：9870
  - Yarn查看任务运行情况的：8088
  - 历史服务器：19888

- hadoop2.x
  - HDFS NameNode 内部常用端口：8020/9000
  - HDFS NameNode 对用户的查询端口：50070
  - Yarn查看任务运行情况的：8088
  - 历史服务器：19888

- 常用配置文件
  - 3.x
    - core-site.xml
    - hdfs-site.xml
    - yarn-site.xml
    - mapred-site.xml
    - wokers
  - 2.x
    - core-site.xml
    - hdfs-site.xml
    - yarn-site.xml
    - mapred-site.xml
    - slaves 