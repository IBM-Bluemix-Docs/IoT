---

copyright:
 years: 2015, 2017
lastupdated: "2017-05-24"

---

{:new_window: target="blank"}
{:shortdesc: .shortdesc}

{:screen: .screen}
{:codeblock: .codeblock}
{:pre: .pre}

# 閘道裝置的 HTTP 傳訊 API（測試版）
{: #api}

**重要事項：**閘道裝置的 {{site.data.keyword.iot_full}} HTTP API 功能僅隨限定的測試版程式提供。未來更新可能包含與此特性的目前版本不相容的變更。請試用，並且[讓我們知道您的想法 ![外部鏈結圖示](../../../icons/launch-glyph.svg)](https://developer.ibm.com/answers/smart-spaces/17/internet-of-things.html){: new_window}。

## 存取閘道裝置的 HTTP 傳訊 API 文件
{: #rest_messaging_api}

若要存取「{{site.data.keyword.iot_short_notm}} HTTP 傳訊 API」文件，以及尋找從閘道裝置傳送事件的相關資訊，請參閱 [{{site.data.keyword.iot_short_notm}} HTTP 傳訊 API ![外部鏈結圖示](../../../icons/launch-glyph.svg)](https://docs.internetofthings.ibmcloud.com/apis/swagger/v0002/http-messaging.html){: new_window}。


## 用戶端連線
{: #client_connections}

如需用戶端安全以及如何將用戶端連接至 {{site.data.keyword.iot_short_notm}} 中閘道裝置的相關資訊，請參閱[將應用程式、裝置及閘道連接至 {{site.data.keyword.iot_short_notm}}](../reference/security/connect_devices_apps_gw.html)。


## 發佈事件
{: #event_publication}

除了使用 MQTT 傳訊通訊協定之外，您也可以使用「HTTP 傳訊 API」指令來配置閘道裝置，以透過 HTTP 將事件發佈至 {{site.data.keyword.iot_short_notm}}。

若要從連接至 {{site.data.keyword.iot_short_notm}} 的裝置來提交 `POST` 要求，請使用下列其中一個 URL：

### 未受保護的 POST 要求
<pre class="pre"><code class="hljs">http://<var class="keyword varname">orgId</var>.messaging.internetofthings.ibmcloud.com:1883/api/v0002/device/types/<var class="keyword varname">typeId</var>/devices/<var class="keyword varname">deviceId</var>/events/<var class="keyword varname">eventId</var></code></pre>

### 安全的 POST 要求
<pre class="pre"><code class="hljs">https://<var class="keyword varname">orgId</var>.messaging.internetofthings.ibmcloud.com:8883/api/v0002/device/types/<var class="keyword varname">typeId</var>/devices/<var class="keyword varname">deviceId</var>/events/<var class="keyword varname">eventId</var></code></pre>

**重要注意事項：**
- 您只能使用 HTTP 傳訊來提交閘道裝置事件。若要提交其他閘道裝置管理及控制特性的要求，請使用 MQTT 傳訊通訊協定。
- 您也可以指定埠 443（預設 SSL 埠）來進行安全 HTTP API 呼叫。
- 如果未指派*標準閘道*角色給閘道，則該閘道可以代表組織中的任何裝置來發佈事件。如果連接到閘道的裝置未經過登錄，閘道會自動登錄該裝置。
- 如果您想要檢查裝置授權層級，請指派*標準閘道*角色。

如需閘道及資源群組角色的相關資訊，請參閱[閘道存取控制（測試版）](../gateways/gateway-access-control.html)。

### 鑑別

所有要求都必須包含授權標頭。基本鑑別是唯一支援的方法。當裝置使用 {{site.data.keyword.iot_short_notm}} HTTP REST API 提出 HTTP 要求時，需要下列認證：

|認證|必要輸入|
|:---|:---|
|使用者名稱| `g/{orgId}/{gwType}/{gwDevId}` or `g-{orgId}-{gwType}-{gwDevId}`
|密碼| 在登錄閘道裝置時，自動產生或手動指定的鑑別記號。


其中：

<dl>
<dt>orgId</dt>  
<dd>組織名稱，必須符合主機標頭中指定的名稱。</dd>

<p></p>
<dt>gwType</dt>  
<dd>閘道的類型。</dd>
<dd>如果您使用連字號 "-" 字元作為使用者名稱的定界字元，則此值不得包括連字號字元。</dd>
<p></p>
<dt>gwDevId</dt>  
<dd>閘道的裝置 ID。</dd>
</dl>


### Content-Type 要求標頭

`Content-Type` 要求標頭必須隨要求提供。下表顯示支援的類型如何對映至 {{site.data.keyword.iot_short_notm}} 內部格式：

|Content-Type 標頭|{{site.data.keyword.iot_short_notm}} 中的格式|
|:---|:---|
|text/plain|"text"
|application/json| "json"
|application/xml | "xml"
|application/octet-stream|"bin"

### 服務品質

與 MQTT 服務品質「最多一次」遞送服務水準 0 類似，HTTP REST 傳訊提供非持續性訊息遞送，但會驗證要求正確無誤，而且可以先遞送至伺服器，再傳送 HTTP 回應。包含 HTTP 狀態碼 200 的回覆會確認已將訊息遞送至伺服器。當您使用「最多一次」的 MQTT 服務品質水準或 HTTP 對等項目來遞送事件訊息時，裝置或應用程式必須實作重試邏輯以保證遞送。

如需 {{site.data.keyword.iot_short_notm}} 的 MQTT 通訊協定及服務品質水準的相關資訊，請參閱 [MQTT 傳訊](../reference/mqtt/index.html)。

如需使用 API 來管理閘道裝置的相關資訊，請參閱[閘道裝置的 HTTP REST API](../gateways/gw_api.html)。

## 接收指令
{: #receive_commands}

除了使用 MQTT 傳訊通訊協定之外，您也可以使用「HTTP 傳訊 API」指令來配置閘道裝置，透過 HTTP 接收來自 {{site.data.keyword.iot_short_notm}} 的指令。閘道裝置可以接收指向其相關聯資源群組內裝置的指令。如需閘道資源群組的相關資訊，請參閱[閘道存取控制（測試版）](../gateways/gateway-access-control.html)。

請使用下列其中一個 URL，來提交來自連接至 {{site.data.keyword.iot_short_notm}} 之閘道的 `POST` 要求：

### 未受保護的 POST 要求
<pre class="pre"><code class="hljs">http://<var class="keyword varname">orgId</var>.messaging.internetofthings.ibmcloud.com:1883/api/v0002/device/types/<var class="keyword varname">typeId</var>/devices/<var class="keyword varname">deviceId</var>/commands/<var class="keyword varname">command</var>/request</code></pre>

### 安全的 POST 要求

<pre class="pre"><code class="hljs">https://<var class="keyword varname">orgId</var>.messaging.internetofthings.ibmcloud.com:8883/api/v0002/device/types/<var class="keyword varname">typeId</var>/devices/<var class="keyword varname">deviceId</var>/commands/<var class="keyword varname">command</var>/request</code></pre>

**附註：**您也可以指定埠 443（預設 SSL 埠）來進行安全 HTTP API 呼叫。

您可以選擇性地在 HTTP 要求主體中包括參數 *waitTimeSecs* 來指定一個整數，這個整數代表等待指令的秒數上限：
<pre class="pre"><code class="hljs">{"waitTimeSecs": 5} </code></pre>


**重要注意事項：**
- *waitTimeSecs* 的值必須是 0 - 3600 秒範圍內的整數。預設值為 0。
- 若要接收任何裝置類型的指令，請針對 `typeId` 元件使用「任何」萬用字元 (+)。如果使用萬用字元，則會在回應標頭欄位 *X-deviceType* 中包含裝置類型。
- 若要接收任何裝置的指令，請針對 `deviceId` 元件使用「任何」萬用字元 (+)。如果使用萬用字元，則會在回應標頭欄位 *X-deviceId* 中包含裝置 ID。
- 若要接收任何指令，請針對 `command` 元件使用「任何」萬用字元 (+)。如果使用萬用字元，則會在回應標頭欄位 *X-commandId* 中包含指令 ID。
- 如果 HTTP 回應狀態碼是 200，則會在回應主體中包含指令資料。請檢閱回應標頭欄位 *Content-Type*，以尋找內容類型。
- 如果 HTTP 回應狀態碼是 204，則沒有可用的指令資料。
