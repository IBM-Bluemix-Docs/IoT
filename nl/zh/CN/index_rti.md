---

copyright:
  years: 2016, 2018
lastupdated: "2017-12-21"

---

{:new_window: target="_blank"}
{:shortdesc: .shortdesc}
{:screen: .screen}
{:codeblock: .codeblock}
{:pre: .pre}

# {{site.data.keyword.iot_short_notm}} 入门
{: #gettingstartedtemplate}

{{site.data.keyword.iot_full}} for {{site.data.keyword.Bluemix_notm}} 为您提供多功能工具箱，其中包括网关设备、设备管理和强大的应用程序访问。通过使用 {{site.data.keyword.iot_short_notm}}，您可以从组织收集已连接的设备数据，并对实时数据执行分析。
{:shortdesc}

## 开始之前
{: #byb}

连接设备并利用数据之前，请注册 {{site.data.keyword.Bluemix_notm}} 帐户，并在您的 {{site.data.keyword.Bluemix_notm}} 组织中创建 {{site.data.keyword.iot_short_notm}} 服务的实例。可以直接从 [IBM Cloud 服务目录中的 {{site.data.keyword.iot_short_notm}} 页面 ![外部链接图标](../../icons/launch-glyph.svg "外部链接图标")](https://console.{DomainName}/catalog/services/internet-of-things-platform/){:new_window}，创建 {{site.data.keyword.iot_short_notm}} 实例。  

有关如何在 {{site.data.keyword.Bluemix_notm}} 上注册帐户并配置区域以及有关其他帐户管理设置的详细信息，请参阅[管理 IBM Cloud 帐户](https://console.ng.bluemix.net/docs/admin/account.html#signup)。

可以在仪表板中设置并配置 {{site.data.keyword.iot_short_notm}} 实例。要打开仪表板，请转至 {{site.data.keyword.Bluemix_notm}} 中的 {{site.data.keyword.iot_short_notm}} 服务实例，然后单击**启动**。

## 关于此任务

以下步骤描述如何快速开始使用 {{site.data.keyword.iot_short_notm}} 服务。

此外，还提供了一组更详细的入门指南和样本应用程序，这些指南和样本应用程序可逐步完成使用 {{site.data.keyword.iot_short_notm}} 开发现成可用的端到端 IoT 原型系统。如果您是使用 {{site.data.keyword.iot_short_notm}} 的新开发人员，请使用[入门指南](https://console.bluemix.net/docs/services/IoT/getting_started/getting-started-iot-overview.html#getting-started)部分的逐步过程。

## 步骤 1：连接设备
{: #up_and_running}

要快速入门和熟悉运用此服务，请根据具体情况研究以下选项：

   | 服务已部署 | 服务未部署
  ------------- | -------------
  **我有一个要连接的设备** | [将你的设备连接到 {{site.data.keyword.iot_short_notm}}](iotplatform_task.html#iotplatform_task)。| 在[播放组织演示 ![外部链接图标](../../icons/launch-glyph.svg "外部链接图标")](http://discover-iot.eu-gb.mybluemix.net/?cm_mc_uid=44491599487314618721024&cm_mc_sid_50200000=1462798151#/play){:new_window} 中探索设备连接。
  **我没有要连接的设备** | [创建和连接 Node-RED 设备模拟器](nodereddevice_sample.html){:new_window}。| [Watson IoT Platform Starter](https://console.ng.bluemix.net/docs/starters/IoT/iot500.html) 入门。
有关如何将特定设备类型连接到 {{site.data.keyword.iot_short_notm}} 的更多信息，请参阅 [developerWorks 诀窍 ![外部链接图标](../../icons/launch-glyph.svg "外部链接图标")](https://developer.ibm.com/recipes/tutorials/category/internet-of-things-iot/){:new_window}。  

有关设备连接开发者文档，请参阅：
- [设备的 MQTT 连接](devices/mqtt.html)。
- [网关的 MQTT 连接](gateways/mqtt.html)。

## 步骤 2：分析设备数据
{: #analyzing_data}

开始浏览设备正在向 {{site.data.keyword.iot_short_notm}} 发送的实时数据。

{{site.data.keyword.iot_short_notm}} 包括以下分析工具：  
- 用于可视化实时设备数据的[板和卡](data_visualization.html)。
- 由实时设备数据触发的[规则和操作](analytics.html)。

有关快速入门示例，请参阅 [UsingRules and Actions with IBM Watson IoT Platform Cloud Analytics ![外部链接图标](../../icons/launch-glyph.svg "外部链接图标")](https://developer.ibm.com/recipes/tutorials/using-rules-and-actions-with-ibm-watson-iot-platform-cloud-analytics/){:new_window} developerWorks 诀窍。

## 步骤 3：创建应用程序以使用设备数据
{: #develop_applications}

通过创建并连接您自己的应用程序以使用实时和历史设备数据，从而扩展 {{site.data.keyword.iot_short_notm}} 的数据分析功能。

有关更多信息，请参阅以下主题：   
- 浏览[应用程序开发者文档](applications/api.html)和 [{{site.data.keyword.iot_short_notm}} API 文档](reference/api.html)。
- 浏览 [{{site.data.keyword.iot_short_notm}} 客户机库](iot_platform_client_lib.html)，此库提供了工具和文件来构建和开发代码，从而集成和连接设备及应用程序。
- [连接 {{site.data.keyword.cloudantfull}} 服务](cloudant_connector.html)到 {{site.data.keyword.iot_short_notm}} 以存储历史设备数据。
