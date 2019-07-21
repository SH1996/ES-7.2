<h2>Getting started with Elasticsearch</h2>

准备好接受ElasticSearch进行试驾了吗？自己看看如何使用RESTAPI来存储、搜索和分析数据？

逐步学习本入门教程：

*启动并运行ElasticSearch实例  
*索引一些示例文档  
*使用ElasticSearch查询语言搜索文档  
*使用bucket和metrics聚合分析结果  

需要更多上下文？

查看ElasticSearch简介，了解ElasticSearch的行话，了解ElasticSearch的工作原理。如果您已经熟悉ElasticSearch，并且希望了解它如何与堆栈的其余部分一起工作，那么您可能希望跳到ElasticSearch教程，了解如何使用ElasticSearch、Kibana、Beats和Logstash设置系统监控解决方案。

TIP:启动ElasticSearch的最快方法是在云中启动一个为期14天的免费ElasticSearch服务试用。

<h3>Installation</h3>

TIP:您可以不必在弹性云上使用我们的托管弹性搜索服务来安装ElasticSearch。ElasticSearch服务可在AWS和GCP上使用。免费试用ElasticSearch服务。

NOTE:ElasticSearch包括来自JDK维护人员（GPLv2+CE）的OpenJDK捆绑版本。要使用您自己的Java版本，请参阅JVM版本要求

二进制文件可从www.slastic.co/downloads获得。Windows、Linux和MacOS提供了平台相关的存档。此外，DEB和RPM软件包可用于Linux，而MSI安装软件包可用于Windows。您也可以使用弹性自制水龙头在MacOS上使用BREW软件包管理器进行安装。

<h3>Installation example on Linux</h3>

为了简单起见，让我们使用tar文件。

让我们下载ElasticSearch 7.2.0 Linux tar，如下所示：

```
curl -L -O https://artifacts.elastic.co/downloads/elasticsearch/elasticsearch-7.2.0-linux-x86_64.tar.gz
```
然后提取如下：

```
tar -xvf elasticsearch-7.2.0-linux-x86_64.tar.gz
```
然后它将在当前目录中创建一组文件和文件夹。然后我们进入bin目录，如下所示：

```
cd elasticsearch-7.2.0/bin
```

现在我们准备启动节点和单个集群：

```
./elasticsearch
```

<h3>Installation example with MSI Windows Installer</h3>

对于Windows用户，我们建议使用msi安装程序包。该包包含一个图形用户界面（GUI），指导您完成安装过程。

首先，从https://artures.elastic.co/downloads/elasticsearch/elasticsearch-7.2.0.msi下载Elasticsearch 7.2.0 msi。

然后双击下载的文件以启动GUI。在第一个屏幕中，选择部署目录：

![](./image/installer_1.png)

然后选择是作为服务安装，还是根据需要手动启动ElasticSearch。要与Linux示例保持一致，请选择不作为服务安装：

![](./image/installer_2.png)

对于配置，只需保留默认值：

![](./image/installer_3.png)

同样，要与tar示例保持一致，请取消选中所有插件以不安装任何插件：

![](./image/installer_4.png)

单击“安装”按钮后，将安装ElasticSearch：

![](./image/installer_5.png)

默认情况下，ElasticSearch将安装在%ProgramFiles%\Elastic\ElasticSearch。导航到此处并按如下方式进入bin目录：

<h4>with Command Prompt:</h4>

```
cd %PROGRAMFILES%\Elastic\Elasticsearch\bin
```

<h4>with PowerShell:<h4>

```
cd $env:PROGRAMFILES\Elastic\Elasticsearch\bin
```

<h5>And now we are ready to start our node and single cluster:</h5>

```
.\elasticsearch.exe
```

<h3>Successfully running node</h3>

如果安装一切顺利，您将看到下面的一堆消息：

```
[2018-09-13T12:20:01,766][INFO ][o.e.e.NodeEnvironment    ] [localhost.localdomain] using [1] data paths, mounts [[/home (/dev/mapper/fedora-home)]], net usable_space [335.3gb], net total_space [410.3gb], types [ext4]
[2018-09-13T12:20:01,772][INFO ][o.e.e.NodeEnvironment    ] [localhost.localdomain] heap size [990.7mb], compressed ordinary object pointers [true]
[2018-09-13T12:20:01,774][INFO ][o.e.n.Node               ] [localhost.localdomain] node name [localhost.localdomain], node ID [B0aEHNagTiWx7SYj-l4NTw]
[2018-09-13T12:20:01,775][INFO ][o.e.n.Node               ] [localhost.localdomain] version[7.2.0], pid[13030], build[oss/zip/77fc20e/2018-09-13T15:37:57.478402Z], OS[Linux/4.16.11-100.fc26.x86_64/amd64], JVM["Oracle Corporation"/OpenJDK 64-Bit Server VM/10/10+46]
[2018-09-13T12:20:01,775][INFO ][o.e.n.Node               ] [localhost.localdomain] JVM arguments [-Xms1g, -Xmx1g, -XX:+UseConcMarkSweepGC, -XX:CMSInitiatingOccupancyFraction=75, -XX:+UseCMSInitiatingOccupancyOnly, -XX:+AlwaysPreTouch, -Xss1m, -Djava.awt.headless=true, -Dfile.encoding=UTF-8, -Djna.nosys=true, -XX:-OmitStackTraceInFastThrow, -Dio.netty.noUnsafe=true, -Dio.netty.noKeySetOptimization=true, -Dio.netty.recycler.maxCapacityPerThread=0, -Dlog4j.shutdownHookEnabled=false, -Dlog4j2.disable.jmx=true, -Djava.io.tmpdir=/tmp/elasticsearch.LN1ctLCi, -XX:+HeapDumpOnOutOfMemoryError, -XX:HeapDumpPath=data, -XX:ErrorFile=logs/hs_err_pid%p.log, -Xlog:gc*,gc+age=trace,safepoint:file=logs/gc.log:utctime,pid,tags:filecount=32,filesize=64m, -Djava.locale.providers=COMPAT, -XX:UseAVX=2, -Dio.netty.allocator.type=unpooled, -Des.path.home=/home/manybubbles/Workspaces/Elastic/master/elasticsearch/qa/unconfigured-node-name/build/cluster/integTestCluster node0/elasticsearch-7.0.0-alpha1-SNAPSHOT, -Des.path.conf=/home/manybubbles/Workspaces/Elastic/master/elasticsearch/qa/unconfigured-node-name/build/cluster/integTestCluster node0/elasticsearch-7.0.0-alpha1-SNAPSHOT/config, -Des.distribution.flavor=oss, -Des.distribution.type=zip]
[2018-09-13T12:20:02,543][INFO ][o.e.p.PluginsService     ] [localhost.localdomain] loaded module [aggs-matrix-stats]
[2018-09-13T12:20:02,543][INFO ][o.e.p.PluginsService     ] [localhost.localdomain] loaded module [analysis-common]
[2018-09-13T12:20:02,543][INFO ][o.e.p.PluginsService     ] [localhost.localdomain] loaded module [ingest-common]
[2018-09-13T12:20:02,544][INFO ][o.e.p.PluginsService     ] [localhost.localdomain] loaded module [lang-expression]
[2018-09-13T12:20:02,544][INFO ][o.e.p.PluginsService     ] [localhost.localdomain] loaded module [lang-mustache]
[2018-09-13T12:20:02,544][INFO ][o.e.p.PluginsService     ] [localhost.localdomain] loaded module [lang-painless]
[2018-09-13T12:20:02,544][INFO ][o.e.p.PluginsService     ] [localhost.localdomain] loaded module [mapper-extras]
[2018-09-13T12:20:02,544][INFO ][o.e.p.PluginsService     ] [localhost.localdomain] loaded module [parent-join]
[2018-09-13T12:20:02,544][INFO ][o.e.p.PluginsService     ] [localhost.localdomain] loaded module [percolator]
[2018-09-13T12:20:02,544][INFO ][o.e.p.PluginsService     ] [localhost.localdomain] loaded module [rank-eval]
[2018-09-13T12:20:02,544][INFO ][o.e.p.PluginsService     ] [localhost.localdomain] loaded module [reindex]
[2018-09-13T12:20:02,545][INFO ][o.e.p.PluginsService     ] [localhost.localdomain] loaded module [repository-url]
[2018-09-13T12:20:02,545][INFO ][o.e.p.PluginsService     ] [localhost.localdomain] loaded module [transport-netty4]
[2018-09-13T12:20:02,545][INFO ][o.e.p.PluginsService     ] [localhost.localdomain] no plugins loaded
[2018-09-13T12:20:04,657][INFO ][o.e.d.DiscoveryModule    ] [localhost.localdomain] using discovery type [zen]
[2018-09-13T12:20:05,006][INFO ][o.e.n.Node               ] [localhost.localdomain] initialized
[2018-09-13T12:20:05,007][INFO ][o.e.n.Node               ] [localhost.localdomain] starting ...
[2018-09-13T12:20:05,202][INFO ][o.e.t.TransportService   ] [localhost.localdomain] publish_address {127.0.0.1:9300}, bound_addresses {[::1]:9300}, {127.0.0.1:9300}
[2018-09-13T12:20:05,221][WARN ][o.e.b.BootstrapChecks    ] [localhost.localdomain] max file descriptors [4096] for elasticsearch process is too low, increase to at least [65535]
[2018-09-13T12:20:05,221][WARN ][o.e.b.BootstrapChecks    ] [localhost.localdomain] max virtual memory areas vm.max_map_count [65530] is too low, increase to at least [262144]
[2018-09-13T12:20:08,355][INFO ][o.e.c.s.MasterService    ] [localhost.localdomain] elected-as-master ([0] nodes joined)[, ], reason: master node changed {previous [], current [{localhost.localdomain}{B0aEHNagTiWx7SYj-l4NTw}{hzsQz6CVQMCTpMCVLM4IHg}{127.0.0.1}{127.0.0.1:9300}{testattr=test}]}
[2018-09-13T12:20:08,360][INFO ][o.e.c.s.ClusterApplierService] [localhost.localdomain] master node changed {previous [], current [{localhost.localdomain}{B0aEHNagTiWx7SYj-l4NTw}{hzsQz6CVQMCTpMCVLM4IHg}{127.0.0.1}{127.0.0.1:9300}{testattr=test}]}, reason: apply cluster state (from master [master {localhost.localdomain}{B0aEHNagTiWx7SYj-l4NTw}{hzsQz6CVQMCTpMCVLM4IHg}{127.0.0.1}{127.0.0.1:9300}{testattr=test} committed version [1] source [elected-as-master ([0] nodes joined)[, ]]])
[2018-09-13T12:20:08,384][INFO ][o.e.h.n.Netty4HttpServerTransport] [localhost.localdomain] publish_address {127.0.0.1:9200}, bound_addresses {[::1]:9200}, {127.0.0.1:9200}
[2018-09-13T12:20:08,384][INFO ][o.e.n.Node               ] [localhost.localdomain] started
```

在不太详细的情况下，我们可以看到名为“localhost.localdomain”的节点已经在单个集群中启动并选择自己作为主节点。现在别担心大师是什么意思。这里最重要的是我们已经在一个集群中启动了一个节点。

如前所述，我们可以覆盖集群或节点名。当启动ElasticSearch时，可以从命令行执行此操作，如下所示：

```
./elasticsearch -Ecluster.name=my_cluster_name -Enode.name=my_node_name
```

还请注意标记为http的行，其中包含可从中访问节点的http地址（192.168.8.112）和端口（9200）的信息。默认情况下，ElasticSearch使用端口9200提供对其RESTAPI的访问。如有必要，此端口可配置。
