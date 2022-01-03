linux centos yum报错 To address this issue please refer to the below wiki article 解决方法

<img src="img/image-20220101212939753.png" alt="image-20220101212939753" style="zoom:33%;float:left" />

报错原因：国外[yum](https://so.csdn.net/so/search?q=yum)镜像源 国内下载不了 修改为国内阿里yum镜像源

解决方法：

```bash
cd /etc/yum.repos.d/
mkdir repo_bak
mv *.repo repo_bak/
wget http://mirrors.aliyun.com/repo/Centos-7.repo
yum clean all
yum makecache
```

详细参考：《[centos7](https://so.csdn.net/so/search?q=centos7) 配置国内yum源和epel源》https://blog.csdn.net/whatday/article/details/106107168

解析不不了配置文件中的$releasever

![image-20220101213224717](img/image-20220101213224717.png)

```shell
vim Centos-7.repo
vim CentOS-Base.repo
#用vim的查找替换命令 将$releasever都替换为7（因为我的是centos7）
%s/\$releasever/7/g
```

#### Vim 字符串替换

查找和替换是任意一款文本编辑器的一组常见和必备功能。下面就来讲解 Vim 中的字符串替换功能。

Vim 使用以下命令结构实现替换功能。

```
:<range> s/<search_string>/<replace_string>/<modifier>
```

- range - 定义执行“查找和替换”函数的范围，有两个不同的值
  - ％ - 对整个文件执行
  - < start _line > < end_line > - 在一组特定的行上面执行操作
- search_string - 需要替换的字符串
- replace_string - 替换旧字符串的新字符串
- modifier - 确定替换行为，有几个不同的值
  - g - 全局替换
  - gc - 在每次更换之前要求确认
  - gn - 忽略替换功能并突出显示查找结果。





NameNode无法启动，报错原因：

 1、 java.net.BindException: Port in use: master:9001

 2、Caused by: java.net.BindException: Cannot assign requested address

<img src="img/image-20220101223611130.png" alt="image-20220101223611130" style="zoom:33%;float:left;" />

端口被占用是直接原因，但起因是不能分配所需的地址，跟地址有关的就联想到 /etc/hosts文件

云服务器的IP要换成内网的IP，内网可以比作一个局域网。 



hadoop集群部署上后，在服务器中运行hadoop自带的jar包中的实例报错

![image-20220103164220531](img/image-20220103164220531.png)

解决方法：按错误提示，在mapred-site.xml配置文件中添加hadoop根目录

1.先运行hadoop classpath得到classpath

将得到的classpath全部复制到mapred-site.xml中，配置

```xml
<property> 
    <name>mapreduce.application.classpath</name>    <value>/home/hadoop/app/hadoop/etc/hadoop:/home/hadoop/app/hadoop/share/hadoop/common/lib/*:/home/hadoop/app/hadoop/share/hadoop/common/*:/home/hadoop/app/hadoop/share/hadoop/hdfs:/home/hadoop/app/hadoop/share/hadoop/hdfs/lib/*:/home/hadoop/app/hadoop/share/hadoop/hdfs/*:/home/hadoop/app/hadoop/share/hadoop/mapreduce/*:/home/hadoop/app/hadoop/share/hadoop/yarn:/home/hadoop/app/hadoop/share/hadoop/yarn/lib/*:/home/hadoop/app/hadoop/share/hadoop/yarn/*
</value>
</property>

```

配置结束关闭mapred-site.xml

重新启动集群，再在share文件中运行