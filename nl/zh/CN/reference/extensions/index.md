---

copyright:
  years: 2015, 2019
lastupdated: "2019-04-10"

keywords: IoT Platform organization, SIM devices, IBM Watson

subcollection: iot-platform

---

{:new_window: target="\_blank"}
{:shortdesc: .shortdesc}
{:screen: .screen}
{:codeblock: .codeblock}
{:pre: .pre}
{:important: .important}

# 外部服务集成
{: #ref-index}

<p>该 {{site.data.keyword.cloud}} 文档集合与 {{site.data.keyword.iot_full}} 轻量价格套餐有关，并且包含基本入门信息、API 参考和一般故障诊断信息。
有关完整的 {{site.data.keyword.iot_short_notm}} 功能文档，请参阅 IBM Knowledge Center 上的 [{{site.data.keyword.iot_short_notm}} 产品文档 ![外部链接图标](../../../../icons/launch-glyph.svg "外部链接图标")](https://www.ibm.com/support/knowledgecenter/SSQP8H/iot/overview/overview.html)。可在 [{{site.data.keyword.iot_short_notm}} 服务套餐](/docs/services/IoT?topic=iot-platform-plans_overview#plans_overview)中找到有关各种套餐的更多信息。
</p>
{: important}

通过外部服务集成，可在 {{site.data.keyword.iot_full}} 组织中访问第三方或外部服务中的数据和操作。

## Jasper
{: #jasper}

Jasper 是一款用于 SIM 设备的管理平台。Jasper 集成到 {{site.data.keyword.iot_short_notm}} 仪表板中，从而可通过 {{site.data.keyword.iot_short_notm}} 组织仪表板管理 Jasper 设备。

### Jasper 的受支持操作

我们的平台所提供的内置 Jasper 集成提供了对以下 Jasper 操作的支持：

- 查看总体 Jasper 数据
  - 显示状态、费率套餐、本月至今数据使用情况、本月至今 SMS 使用情况、本月至今语音使用情况、超额限制、添加日期和修改日期。
- 更改 SIM 激活状态
  - 从以下选项中进行选择：库存、可随时激活、已激活、已取消激活和已废弃。
- 查看 SIM 使用情况
  - 显示周期开始日期、计费数据和数据总量、计费 SMS 和 SMS 总量、计费语音和语音总量。
  - 可以使用 YYYY-MM-DD 日期格式设置周期开始日期。
- 将 SMS 发送到 SIM
- 更改套餐

完成以下配置步骤后，可在连接了 Jasper 的设备的设备向下钻取中访问受支持的操作。

### 用于 Jasper 的 REST API
要访问用于 Jasper 的 REST API，请参阅 [{{site.data.keyword.iot_short_notm}} HTTP REST API ![外部链接图标](../../../../icons/launch-glyph.svg "外部链接图标")](https://docs.internetofthings.ibmcloud.com/apis/swagger/v0002/ext-jasper.html){: new_window} 文档的“Jasper 扩展”部分。

### Jasper 的配置

要将 Jasper 服务连接到 {{site.data.keyword.iot_short_notm}} 组织，必须完成两个配置阶段。首先，必须将 {{site.data.keyword.iot_short_notm}} 连接到 Jasper 服务，然后必须配置 {{site.data.keyword.iot_short_notm}} 设备。


1. 启用 Jasper 扩展。要启用 Jasper 与 {{site.data.keyword.iot_short_notm}} 组织的集成，请完成以下步骤：
  1. 从 {{site.data.keyword.iot_short_notm}} 仪表板选择**扩展**。
  2. 在**扩展**页面上，单击**添加扩展**。
  3. 单击 Jasper 旁的**添加**。
  4. 输入 Jasper 用户名、密码、访问键和域标识。
  5. 单击**完成**。

2. 配置设备。
您可以配置同时连接到您的 {{site.data.keyword.iot_short_notm}} 组织和 Jasper 帐户的设备以在 {{site.data.keyword.iot_short_notm}} 仪表板中显示 Jasper 中的数据。  
**重要信息：**在“添加设备”过程中，无法应用 Jasper 配置。只能使用 Jasper 配置先前已连接的设备。  
要配置连接了 Jasper 的设备，请完成以下步骤：
 1. 在 {{site.data.keyword.iot_short_notm}} 仪表板的“设备”页面中，查找要配置的连接了 Jasper 的设备。
 2. 选择设备以打开“设备向下钻取”视图。
 3. 向下滚动到“扩展配置”。
 4. 通过使用以下 JSON 格式输入扩展配置，然后单击**确认更改**以保存配置。  

```json  
    {
        "jasper": {
            "iccid": "string"
        }
    }

```

成功配置组织后，会在“设备向下钻取”视图中“扩展配置”部分下显示“扩展”部分。

## AT&T
{: #att}

### AT&T 的受支持操作

AT&T 扩展支持以下 AT&T 操作：

- 查看总体 AT&T 数据
  - 显示状态、费率套餐、本月至今数据使用情况、本月至今 SMS 使用情况、本月至今语音使用情况、超额限制、添加日期和修改日期。
- 更改 SIM 激活状态
  - 从以下选项中进行选择：库存、可随时激活、已激活、已取消激活和已废弃。
- 查看 SIM 使用情况
  - 显示：周期开始日期、计费数据和数据总量、计费 SMS 和 SMS 总量、计费语音和语音总量。
  - 可以使用 YYYY-MM-DD 日期格式设置周期开始日期。
- 将 SMS 发送到 SIM
- 更改套餐

### 用于 AT&T 的 REST API
要访问用于 AT&T 的 REST API，请参阅 [{{site.data.keyword.iot_short_notm}} HTTP REST API ![外部链接图标](../../../../icons/launch-glyph.svg "外部链接图标")](https://docs.internetofthings.ibmcloud.com/apis/swagger/v0002/ext-atnt.html){: new_window} 文档中的“AT&T 扩展”部分。

### AT&T 的配置

要将 {{site.data.keyword.iot_short_notm}} 组织连接到 AT&T，必须完成组织配置和设备配置。

要配置 {{site.data.keyword.iot_short_notm}} 平台，请完成以下步骤：

1. 启用 AT&T 扩展。要启用 AT&T 与 {{site.data.keyword.iot_short_notm}} 组织的集成，请完成以下步骤：
  1. 从 {{site.data.keyword.iot_short_notm}} 仪表板选择**扩展**。
  2. 在**扩展**页面上，单击**添加扩展**。
  3. 单击 AT&T 旁的**添加**。
  4. 输入 AT&T 用户名、密码、访问键和域标识。
  5. 单击**完成**。

要将 {{site.data.keyword.iot_short_notm}} 组织与 &T 帐户相连接，必须完成两个配置阶段。完成组织配置，然后配置设备。


2. 配置设备
您可以配置同时连接到您的 {{site.data.keyword.iot_short_notm}} 组织和 AT&T 帐户的设备以在 {{site.data.keyword.iot_short_notm}} 仪表板中显示 AT&T 中的数据。  
**重要信息：**在“添加设备”过程中，无法应用 AT&T 配置。只能使用 AT&T 配置先前已连接的设备。  
要配置连接了 AT&T 的设备，请完成以下步骤：
 1. 在 {{site.data.keyword.iot_short_notm}} 仪表板的“设备”页面中，查找要配置的连接了 AT&T 的设备。
 2. 选择设备以打开“设备向下钻取”视图。
 3. 向下滚动到“扩展配置”。
 4. 通过使用以下 JSON 格式输入扩展配置，然后单击**确认更改**以保存配置。  

```json  
    {
        "atnt": {
            "iccid": "string"
        }
    }

```

成功配置组织后，会在“设备向下钻取”视图中“扩展配置”部分下显示“扩展”部分。

## Arm Mbed 网桥
{: #arm}

该网桥使 Arm Mbed 设备能够与 {{site.data.keyword.iot_short_notm}} 集成，并双向交换消息。要启用此集成，首先需要注册 Arm Mbed 云帐户，然后为 {{site.data.keyword.iot_short_notm}} 配置提供请求的连接信息。

### 安装配置


1. 启用 Arm Mbed 网桥扩展。要启用该扩展，请完成以下步骤：
  1. 从 {{site.data.keyword.iot_short_notm}} 仪表板选择**扩展**。
  2. 在“扩展”页面上，单击**添加扩展**。
  3. 单击“Arm Mbed 网桥”扩展旁的**添加**。
  4. 输入 Arm Mbed 访问密钥。可以使用 [https://portal.mbedcloud.com ![外部链接图标](../../../../icons/launch-glyph.svg "外部链接图标")](https://portal.mbedcloud.com){: new_window} 中的 Arm Mbed 门户网站来创建此密钥。
  5. 通过单击**检查连接**按钮来检查凭证。
  6. 单击**完成**。

### 有效内容格式

Arm Mbed 平台使用两种类型的入局消息：通知和异步响应。{{site.data.keyword.iot_short_notm}} 可以向已连接到 Arm Mbed 平台的设备发送命令。

#### 通知

通知根据设备或传感器数据的更改而生成。{{site.data.keyword.iot_short_notm}} 处理消息后，会按照与直接连接到 {{site.data.keyword.iot_short_notm}} 的设备相同的方式将该消息发送到设备事件主题。对于在连接到 Arm Mbed 平台的设备上发起的通知，使用的事件类型为 `notify`。

以下代码样本显示了 Arm Mbed 平台 API 发送的通知的有效内容格式：

```
{
  "ep":<endpoint/deviceID>,
  "path":<resource path>,
  "ct":<content type>,
  "payload":<Base64 encoded payload>,
  "max-age":<how long the payload is valid, in seconds>
}
```

#### 异步响应

{{site.data.keyword.iot_short_notm}} 向连接到 Arm Mbed 平台的设备发送命令时，设备会将确认消息发回 {{site.data.keyword.iot_short_notm}}。此确认消息称为_异步响应_，并使用事件类型 `asyncResponse`。

以下代码样本显示了 Arm Mbed 云服务发送的异步响应的有效内容格式：

```
{
  "id":<transaction id>,
  "status":<200 is command was sucessfully executed. Check other HTTP response codes>,
  "ct":<content type>,
  "max-age":<how long the payload is valid, in seconds>,
  "payload":<base64 encoded payload>,
  "ep":<endpoint/deviceID affected by the command>,
  "path":<resource path affected by the command>
}
```

#### 向 Arm Mbed 平台发送命令

{{site.data.keyword.iot_short_notm}} 可以向已连接到 Arm Mbed 平台的设备发送命令。向 Arm Mbed 平台发送的命令必须使用以下 JSON 格式：

```
{
  "method":<PUT or POST>,
  "deviceId":<endpoint/deviceId>,
  "resourceId":<resource path>,
  "payload": <Base64 encoded payload>
}
```
所选择的方法是区分大小写的。必须跳过资源路径的第一个 `/`。


有效内容必须发布到以下主题：

```
iot-2/type/<device_type>/id/<deviceId>/cmd/<command_type>/fmt/<command_format>
```

<!--
## Orange
{: #orange}

The Orange extension allows you to view SIM card data from devices that are connected to your {{site.data.keyword.iot_short_notm}} and have an Orange SIM card installed.

### Supported operations for Orange

If you have a device that is connected to your {{site.data.keyword.iot_short_notm}} service and has an Orange SIM card, you can use the Orange extension to view the following SIM card data:

- SIM serial number
- Activation status
- Last status change
- Last status refresh
- Location status

### REST APIs for Orange
To access the REST API for Orange, see the Orange Extension section in the [{{site.data.keyword.iot_short_notm}} HTTP REST API ![External link icon](../../../../icons/launch-glyph.svg "External link icon")](https://docs.internetofthings.ibmcloud.com/apis/swagger/v0002/ext-orange.html){: new_window} documentation.

### Configuration for Orange

To enable the Orange extension:

1. From the {{site.data.keyword.iot_short_notm}} dashboard, select **Extensions**.
2. On the **Extensions** page, click **Add Extension**.
3. Click **Add** next to the Orange extension.
4. Enter your Orange user name and password.
6. Click **Done**.

After the Orange extension has been enabled, each device that has an Orange SIM card must be configured to display Orange SIM data.

1. In the devices tab of your {{site.data.keyword.iot_short_notm}} dashboard, find the Orange SIM device to configure.
2. Select the device and scroll down to **Extension Configuration**.
3. Enter the extension configuration by using the following JSON format and then click **Confirm changes** to save your configuration.

```json
    {
        "orange": {
            "serialnumber": "<serial number of Orange SIM>"
        }
    }

```
When the organization is successfully configured, the Extensions section is displayed under the Extensions Configuration section in the Device Drilldown view.
-->

## 历史数据存储
{: #historical_data}

通过历史数据存储扩展，可以找到并配置 IoT 数据的兼容消息存储服务，例如 [{{site.data.keyword.cloudantfull}} ![外部链接图标](../../../../icons/launch-glyph.svg "外部链接图标")](https://www.ibm.com/support/knowledgecenter/SSQP8H/iot/platform/cloudant_connector.html){: new_window} 或 [{{site.data.keyword.messagehub_full}} ![外部链接图标](../../../../icons/launch-glyph.svg "外部链接图标")](https://www.ibm.com/support/knowledgecenter/SSQP8H/iot/platform/message_hub.html){: new_window}。

## 定制设备管理软件包
{: #device_mgmt}

设备管理是 {{site.data.keyword.iot_short_notm}} 的核心功能，但是，也可以对其进行扩展以开发其他功能。定制设备管理软件包必须由有效的 JSON 构成，并至少定义一个定制设备管理操作。

有关定制设备管理功能的更多信息（包括必需 JSON 格式的示例），请参阅[设备管理定制扩展 ![外部链接图标](../../../../icons/launch-glyph.svg "外部链接图标")](https://www.ibm.com/support/knowledgecenter/SSQP8H/iot/platform/devices/device_mgmt/custom_actions.html){: new_window}。

### 添加定制设备管理软件包

可以使用 {{site.data.keyword.iot_short_notm}} 仪表板或 API 来添加定制设备管理软件包。

要使用 {{site.data.keyword.iot_short_notm}} 仪表板来添加定制设备管理软件包，请执行以下操作：

1. 在 {{site.data.keyword.iot_short_notm}} 仪表板的导航栏中，单击**设置**。
2. 单击**定制设备管理软件包**。
3. 单击**添加软件包**按钮。
4. 选择软件包文件，然后单击**打开**。

要使用 API 来添加定制设备管理软件包，请参阅 [{{site.data.keyword.iot_short_notm}} API 文档 ![外部链接图标](../../../../icons/launch-glyph.svg "外部链接图标")](https://docs.internetofthings.ibmcloud.com/apis/swagger/v0002/orgAdmin.html){: new_window}。

## 电子邮件
{: #email}

使用电子邮件邀请，可以将用户添加到 {{site.data.keyword.iot_short_notm}}。有关信息，请参阅[管理用户访问权](/docs/services/IoT?topic=iot-platform-managing-user-access#managing-user-access)。

要使用电子邮件邀请功能，必须配置电子邮件扩展，以使用 SendGrid 在线服务或简单电子邮件传输协议 (SMTP) 服务。扩展还可以使用 SendGrid {{site.data.keyword.cloud_notm}} 应用程序。

### SendGrid 在线服务

要配置电子邮件扩展以使用 SendGrid 在线服务，请遵循以下步骤：

1. 从 SendGrid 在线帐户检索已获授权的 API 密钥。
2. 在 {{site.data.keyword.iot_short_notm}} 仪表板的导航栏中，单击**扩展**。
3. 在**电子邮件**部分中，单击**设置**。
4. 选择**具有 API 密钥的 SendGrid**
5. 输入站点管理员的名称和电子邮件地址，以及已获授权的 API 密钥。

### SMTP 服务

要配置电子邮件扩展以使用 SMTP 服务，请遵循以下步骤：

1. 在 {{site.data.keyword.iot_short_notm}} 仪表板的导航栏中，单击**扩展**。
2. 在**电子邮件**部分中，单击**设置**。
3. 选择 **SMTP**。
4. 输入 SMTP 服务的配置详细信息。

### SendGrid {{site.data.keyword.cloud_notm}} 应用程序

要配置电子邮件扩展以使用 SendGrid {{site.data.keyword.cloud_notm}} 应用程序，请遵循以下步骤：

1. 创建哑元应用程序，并绑定 SendGrid 服务。  
要检索配置凭证，请添加 SendGrid 服务并将其绑定到哑元应用程序。

 1. 在 {{site.data.keyword.cloud_notm}} 仪表板中，单击**创建服务**。
 2. 从目录选择 SendGrid 服务并单击**创建**。
 3. 在 {{site.data.keyword.cloud_notm}}“仪表板”中，添加 {{site.data.keyword.runtime_nodejs_full}} 应用程序。
 4. 在 {{site.data.keyword.cloud_notm}}“仪表板”中，单击 {{site.data.keyword.runtime_nodejs_notm}} 应用程序，然后单击**绑定服务或 API**。
 5. 选择 SendGrid 服务并单击**添加**。
 6. 重新编译打包 {{site.data.keyword.runtime_nodejs_notm}} 应用程序。
2. 准备配置 {{site.data.keyword.iot_short_notm}} 服务。  
可以使用 {{site.data.keyword.iot_short_notm}} 仪表板或使用 {{site.data.keyword.iot_short_notm}} API 对 {{site.data.keyword.iot_short_notm}} 进行配置。  
 1. 在 {{site.data.keyword.cloud_notm}}“仪表板”中，单击 {{site.data.keyword.runtime_nodejs_notm}} 应用程序。
 2. 单击导航栏中的**环境变量**。
 3. 将显示的 JSON 复制到临时文本文件。  
此 JSON 应该具有以下格式：
```
{
  "name": "SendGridServiceName",
  "label": "user-provided",
  "credentials": {
    "password": "xxx",
    "hostname": "smtp.sendgrid.net",
    "username": "username"
  }
}
```
3. 向 {{site.data.keyword.iot_short_notm}} 组织添加配置数据。
 1. 打开 {{site.data.keyword.iot_short_notm}} 仪表板。
 2. 单击导航栏中的**扩展**。
 3. 单击**电子邮件**图标下的**设置**。
 4. 选择**具有用户名的 SendGrid**。
 5. 输入临时文本文件中的配置数据。
 6. 单击**完成**。
