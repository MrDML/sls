# 接入Elasticsearch监控数据

您可使用Telegraf采集Elasticsearch监控数据，再通过日志服务Logtail将Telegraf数据上传到MetricStore中，搭建Elasticsearch可视化监控方案。本文介绍如何通过日志服务来完成Elasticsearch监控数据的采集和可视化。

-   已在服务器上安装Logtail（Linux Logtail 0.16.48及以上版本）。更多信息，请参见[安装Logtail（Linux系统）](/cn.zh-CN/数据采集/Logtail采集/安装/安装Logtail（Linux系统）.md)。
-   Telegraf所在的服务器可通过内网连接Elasticsearch服务器。

## 操作步骤

1.  登录[日志服务控制台](https://sls.console.aliyun.com)。

2.  在接入数据区域，选择**Elasticsearch监控**。

3.  在选择日志空间页签中，选择目标Project和MetricStore，单击**下一步**。

    您也可以单击**立即创建**，重新创建Project和MetricStore。更多信息，请参见[创建Project](/cn.zh-CN/数据采集/准备工作/管理Project.md)和[创建MetricStore](/cn.zh-CN/时序存储/管理MetricStore.md)。

4.  在创建机器组页签中，创建机器组。

    -   如果您已有可用的机器组，请单击**使用现有机器组**。
    -   如果您还没有可用的机器组，请执行以下操作（以ECS为例）：
        1.  选择ECS实例安装Logtail。更多信息，请参见[安装Logtail（ECS实例）](/cn.zh-CN/数据采集/Logtail采集/安装/安装Logtail（ECS实例）.md)。

            如果已在ECS上安装Logtail，请单击**确认安装完毕**。

            **说明：** 如果是自建集群、其他云厂商服务器，需要手动安装Logtail。更多信息，请参见[安装Logtail（Linux系统）](/cn.zh-CN/数据采集/Logtail采集/安装/安装Logtail（Linux系统）.md#)。

        2.  安装完成后，单击**确认安装完毕**。
        3.  创建机器组。

            如何创建机器组，请参见[创建IP地址机器组](/cn.zh-CN/数据采集/Logtail采集/机器组/创建IP地址机器组.md)或[创建用户自定义标识机器组](/cn.zh-CN/数据采集/Logtail采集/机器组/创建用户自定义标识机器组.md)。

5.  在机器组配置页签中，应用机器组。

    选择一个机器组，将该机器组从**源机器组**移动到**应用机器组**。

6.  在数据源设置页签中，配置如下参数。

    |参数名称|说明|
    |----|--|
    |配置名称|Logtail配置名称。|
    |集群名称|Elasticsearch集群名称。配置该参数后，日志服务会为您的数据添加cluster=集群名称的标签。**说明：** 请确保该集群名称唯一，否则可能出现数据冲突。 |
    |服务器列表|单击**+**，添加Elasticsearch服务器信息，相关配置项如下所示：    -   地址：Elasticsearch服务器的连接地址。
    -   端口号：默认为9200，无需修改。
您可以根据业务需求，添加多台Elasticsearch服务器信息。 |
    |索引名称|单击**+**，添加Elasticsearch索引名称，用于监控Elasticsearch索引指标。配置为\_all，表示采集所有索引的指标数据。您可以根据业务需求，添加多个索引名称。 |
    |自定义标签|一个MetricStore下可创建多个Logtail配置，您可以使用**自定义标签**为通过该Logtail配置采集到的数据添加标签。单击**+**，添加自定义标签，支持添加多个标签。添加的标签将加入到每一条数据中。 |


## 常见问题

如何查看Telegraf采集是否正常？

您可以在服务器上查看/etc/ilogtail/telegraf/telegraf.log文件中记录的日志进行判断，还可以将该日志采集到日志服务中进行查询。

-   查询分析

    配置完成后，Telegraf将采集到的监控数据通过Logtail上传到日志服务MetricStore中。您可以在MetricStore查询分析页面进行查询分析操作，详情请参见[查询分析时序数据](/cn.zh-CN/时序存储/查询与分析/查询分析时序数据.md)。

-   可视化

    配置完成后，日志服务自动在对应Project中生成名为Elasticsearch监控\_集群名称的仪表盘，您可以直接使用该仪表盘，还可以进行告警设置等操作。


