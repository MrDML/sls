# 管理Project

本文介绍如何在日志服务控制台上创建、删除Project等操作。

已开通日志服务。

首次登录[日志服务控制台](https://sls.console.aliyun.com)时，根据页面提示开通日志服务。

## 创建Project

**说明：** 一个阿里云账户最多可创建50个Project。

1.  登录[日志服务控制台](https://sls.console.aliyun.com)。

2.  在**Project列表**区域，单击**创建Project**。

3.  在创建Project对话框中，配置如下参数。

    |参数|描述|
    |--|--|
    |Project名称|Project名称在阿里云地域内全局唯一，创建后不可修改。|
    |注释|Project的简单注释。|
    |所属地域|请根据日志来源等信息选择合适的阿里云地域。创建Project后，无法修改其所属地域，且日志服务不支持跨地域迁移Project。如果您要采集ECS日志，建议选择与ECS相同的地域，即可使用阿里云内网采集日志，加快日志采集速度。 |
    |开通服务日志|开通服务日志后，日志服务会将当前Project产生的所有日志保存到您指定的Project中。更多信息，请参见[服务日志](/cn.zh-CN/开发指南/监控日志服务/服务日志/简介.md)。    -   选中**详细日志**，则保存完整的操作日志到指定的Project中，按量付费。
    -   选中**重要日志**，则保存消费组延迟、Logtail心跳等日志到指定的Project中，免费使用。 |
    |日志存储位置|开通服务日志后，需要选择日志的存储位置。可以设置为：    -   自动创建（推荐）。
    -   当前Project。
    -   同一地域下的其他Project。 |

4.  单击**确定**。


## 删除Project

**警告：**

-   日志服务内置Project（例如通过日志审计服务默认创建的Project）及相关云产品Project，无法自行删除。您可以提交[工单](https://selfservice.console.aliyun.com/ticket/category/sls/today)进行删除。
-   删除Project后，其管理的所有日志数据及配置信息都会被永久释放，不可恢复。在删除Project前请慎重确认，避免数据丢失。

1.  在**Project列表**中，找到目标Project，单击**删除**。

2.  在删除Project对话框，选择删除原因，并单击**确定**。


