# ApplyConfigToMachineGroup

调用ApplyConfigToMachineGroup接口将Logtail配置应用到机器组。

## 请求语法

```
PUT /machinegroups/groupName HTTP/1.1
Authorization: LOG yourAccessKeyId:yourSignature 
Date: GMT Date
Host: ProjectName.Endpoint
x-log-apiversion: 0.6.0
x-log-signaturemethod: hmac-sha1
```

其中，Host由Project名称和日志服务Endpoint构成，您需要在Host中指定Project。

## 请求参数

-   请求头

    ApplyConfigToMachineGroup接口无特有请求头。关于Log Service API的公共请求头，请参见[公共请求头](/intl.zh-CN/开发指南/API 参考/公共请求头.md)。

-   参数列表

    |参数名称|数据类型|是否必填|示例值|描述|
    |:---|:---|:---|---|:-|
    |projectName|String|是|ali-test-project|Project名称。|
    |groupName|String|是|sample-group|机器组名称。|
    |configName|String|是|logtail-config-sample|Logtail配置名称。|


## 返回数据

-   响应头

    ApplyConfigToMachineGroup接口无特有响应头。关于Log Service API的公共响应头，请参见[公共响应头](/intl.zh-CN/开发指南/API 参考/公共响应头.md)。

-   响应元素

    返回HTTP状态码200，则表示请求成功。该接口调用成功后无任何响应元素。


## 示例

-   请求示例

    ```
    PUT /machinegroups/sample-group/configs/logtail-config-sample
    Header :
    {
        "Content-Length": 0, 
        "x-log-signaturemethod": "hmac-sha1", 
        "x-log-bodyrawsize": 0, 
        "User-Agent": "log-python-sdk-v-0.6.0", 
        "Host": "ali-test-project.cn-hangzhou-devcommon-intranet.sls.aliyuncs.com", 
        "Date": "Mon, 09 Nov 2015 09:44:43 GMT", 
        "x-log-apiversion": "0.6.0", 
        "Authorization": "LOG yourAccessKeyId:yourSignature"
    }
    ```

-   正常返回示例

    ```
    HTTP/1.1 200 OK
    Header ：
    {
        "date": "Mon, 09 Nov 2015 09:44:43 GMT", 
        "connection": "close", 
        "x-log-requestid": "56406B0B99248CAA230BA094", 
        "content-length": "0", 
        "server": "nginx/1.6.1"
    }
    ```


## 错误码

|HTTP状态码|错误码|错误信息|描述|
|:------|:--|:---|--|
|404|ProjectNotExist|The Project does not exist : projectName|Project不存在。|
|404|GroupNotExist|group groupName does not exist.|机器组不存在。|
|404|ConfigNotExist|Config configNamdoes not exist.|Logtail配置不存在。|
|500|InternalServerError|Internal server error.|内部服务调用错误。|

更多错误码，请参见[通用错误码](/intl.zh-CN/开发指南/API 参考/通用错误码.md)。

