---

copyright:
 years: 2015, 2018
lastupdated: "2018-05-17"

---

{:new_window: target="blank"}
{:shortdesc: .shortdesc}

{:screen: .screen}
{:codeblock: .codeblock}
{:pre: .pre}

# 针对网关设备的 HTTP 消息传递 API
{: #api}

## 访问针对网关设备的 HTTP 消息传递 API 文档
{: #rest_messaging_api}

要访问 {{site.data.keyword.iot_short_notm}} HTTP 消息传递 API 文档并找到通过网关设备发送事件的更多信息，请参阅 [{{site.data.keyword.iot_short_notm}} HTTP 消息传递 API ![外部链接图标](../../../icons/launch-glyph.svg)](https://docs.internetofthings.ibmcloud.com/apis/swagger/v0002/http-messaging.html){: new_window}。


## 客户机连接
{: #client_connections}

有关客户机安全性以及如何将客户机连接到 {{site.data.keyword.iot_short_notm}} 中网关设备的信息，请参阅[将应用程序、设备和网关连接到 {{site.data.keyword.iot_short_notm}}](../reference/security/connect_devices_apps_gw.html)。


## 发布事件
{: #event_publication}

除了使用 MQTT 消息传递协议外，还可以配置网关设备，以使用 HTTP 消息传递 API 命令通过 HTTP 将事件发布到 {{site.data.keyword.iot_short_notm}}。

要从连接到 {{site.data.keyword.iot_short_notm}} 的设备提交 ``POST`` 请求，请使用以下其中一个 URL：

### 用于发布事件的非安全 POST 请求

<pre class="pre"><code class="hljs">http://<var class="keyword varname">orgId</var>.messaging.internetofthings.ibmcloud.com:1883/api/v0002/device/types/<var class="keyword varname">typeId</var>/devices/<var class="keyword varname">deviceId</var>/events/<var class="keyword varname">eventId</var></code></pre>

### 用于发布事件的安全 POST 请求

<pre class="pre"><code class="hljs">https://<var class="keyword varname">orgId</var>.messaging.internetofthings.ibmcloud.com:8883/api/v0002/device/types/<var class="keyword varname">typeId</var>/devices/<var class="keyword varname">deviceId</var>/events/<var class="keyword varname">eventId</var></code></pre>

**重要说明：**
- 您只能使用 HTTP 消息传递来提交网关设备事件。使用 MQTT 消息传递协议可提交其他网关设备管理和控制功能的请求。
- 还可以为安全 HTTP API 调用指定端口 443（缺省 SSL 端口）。
- 如果未向网关分配*标准网关*角色，那么它可以代表组织中的任何设备发布事件。如果连接到网关的设备未注册，网关会自动注册该设备。
- 如果想要检查设备授权级别，请分配*标准网关*角色。

有关网关和资源组角色的更多信息，请参阅[网关访问控制](../gateways/gateway-access-control.html)。

### 认证

所有请求都必须包含授权头。基本认证是唯一受支持的方法。设备使用 {{site.data.keyword.iot_short_notm}} HTTP REST API 发起 HTTP 请求时，以下凭证是必需的：

|凭证|必需的输入|
|:---|:---|
|用户名|`g/{orgId}/{gwType}/{gwDevId}` 或 `g-{orgId}-{gwType}-{gwDevId}`
|密码|注册网关设备时自动生成或手动指定的认证令牌。



其中：

<dl>
<dt>orgId</dt>  
<dd>组织名称，必须与主机头中指定的名称相匹配。</dd>

<p></p>
<dt>gwType</dt>  
<dd>网关的类型。</dd>
<dd>如果您在用户名中使用连字符“-”字符作为分隔符，那么此值不得包含连字符字符。</dd>
<p></p>
<dt>gwDevId</dt>  
<dd>是网关的设备标识。</dd>
</dl>


### Content-Type 请求头

如果内容不是 JSON，那么应该向请求提供 `Content-Type` 请求头。下表显示了如何将受支持的类型映射到 {{site.data.keyword.iot_short_notm}} 内部格式：

|Content-Type 头|{{site.data.keyword.iot_short_notm}} 中的格式|
|:---|:---|
|text/plain|"text"
|application/json|"json"
|application/xml|"xml"
|application/octet-stream|"bin"



### 服务质量

与 MQTT 服务质量“最多一次”传递服务级别 0 类似，HTTP REST 消息传递提供了非持久性消息传递，但它会验证请求是否正确，并在发送 HTTP 响应之前，验证其是否可以传递到服务器。包含 HTTP 状态码 200 的回复将确认消息已传递到服务器。使用“最多一次”MQTT 服务质量级别或 HTTP 同等级别来传递事件消息时，设备或应用程序必须实现重试逻辑以保证传递。

有关 {{site.data.keyword.iot_short_notm}} 的 MQTT 协议和服务质量级别的更多信息，请参阅 [MQTT 消息传递](../reference/mqtt/index.html)。

有关使用 API 管理网关设备的更多信息，请参阅[针对网关设备的 HTTP REST API](../gateways/gw_api.html)。

## 接收命令
{: #receive_commands}

除了使用 MQTT 消息传递协议外，还可以配置网关设备，以使用 HTTP 消息传递 API 命令通过 HTTP 从 {{site.data.keyword.iot_short_notm}} 接收命令。网关设备可以接收导向到其相关联资源组内设备的命令。有关网关资源组的更多信息，请参阅[网关访问控制](../gateways/gateway-access-control.html)。

使用以下某个 URL 提交来自连接到 {{site.data.keyword.iot_short_notm}} 的网关的 ``POST`` 请求：

### 用于接收命令的非安全 POST 请求

<pre class="pre"><code class="hljs">http://<var class="keyword varname">orgId</var>.messaging.internetofthings.ibmcloud.com:1883/api/v0002/device/types/<var class="keyword varname">typeId</var>/devices/<var class="keyword varname">deviceId</var>/commands/<var class="keyword varname">command</var>/request</code></pre>

### 用于接收命令的安全 POST 请求

<pre class="pre"><code class="hljs">https://<var class="keyword varname">orgId</var>.messaging.internetofthings.ibmcloud.com:8883/api/v0002/device/types/<var class="keyword varname">typeId</var>/devices/<var class="keyword varname">deviceId</var>/commands/<var class="keyword varname">command</var>/request</code></pre>

**注：**还可以为安全 HTTP API 调用指定端口 443（缺省 SSL 端口）。

您可以选择性地在 HTTP 请求的主体中包含 *waitTimeSecs* 参数，以指定整数，代表等待命令的最大秒数：
<pre class="pre"><code class="hljs">{"waitTimeSecs": 5} </code></pre>


**重要说明：**
- *waitTimeSecs* 的值必须是 0 - 3600 秒之间的整数。缺省值为 0。
- 要接收任何设备类型的命令，请对 `typeId` 组件使用“任意”通配符 (+)。如果使用通配符，那么设备类型包含在响应头字段 *X-deviceType* 中。
- 要接收任何设备的命令，请对 `deviceId` 组件使用“任意”通配符 (+)。如果使用通配符，那么设备标识包含在响应头字段 *X-deviceId* 中。
- 要接收任何命令，请对 `command` 组件使用“任意”通配符 (+)。如果使用通配符，那么命令标识包含在响应头字段 *X-commandId* 中。
- 如果 HTTP 响应状态码为 200，那么命令数据包含在响应的主体中。请复查响应头字段 *Content-Type*，以找到内容类型。
- 如果 HTTP 响应状态码为 204，那么没有可用的命令数据。
