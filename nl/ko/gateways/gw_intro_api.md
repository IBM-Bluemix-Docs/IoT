---

copyright:
 years: 2015, 2017
lastupdated: "2017-10-04"

---

{:new_window: target="blank"}
{:shortdesc: .shortdesc}

{:screen: .screen}
{:codeblock: .codeblock}
{:pre: .pre}

# 게이트웨이 디바이스용 HTTP 메시징 API
{: #api}

## 게이트웨이 디바이스용 HTTP Messaging API 문서에 액세스
{: #rest_messaging_api}

{{site.data.keyword.iot_short_notm}} HTTP Messaging API 문서에 액세스하고 게이트웨이 디바이스에서 이벤트 전송에 대한 자세한 정보를 찾으려면 [{{site.data.keyword.iot_short_notm}} HTTP Messaging API ![외부 링크 아이콘](../../../icons/launch-glyph.svg)](https://docs.internetofthings.ibmcloud.com/apis/swagger/v0002/http-messaging.html){: new_window}를 참조하십시오. 


## 클라이언트 연결
{: #client_connections}

클라이언트 보안 및 클라이언트를 {{site.data.keyword.iot_short_notm}}의 게이트웨이 디바이스에 연결하는 방법에 대한 정보는 [{{site.data.keyword.iot_short_notm}}에 애플리케이션, 디바이스 및 게이트웨이 연결](../reference/security/connect_devices_apps_gw.html)을 참조하십시오. 


## 이벤트 공개
{: #event_publication}

MQTT 메시징 프로토콜 외에도 HTTP 메시징 API 명령을 사용하여 {{site.data.keyword.iot_short_notm}}에 HTTP를 통해 이벤트를 공개하도록 게이트웨이 디바이스를 구성할 수도 있습니다. 

{{site.data.keyword.iot_short_notm}}에 연결되어 있는 디바이스에서 ``POST`` 요청을 제출하려면 다음 URL 중 하나를 사용하십시오. 

### 비보안 POST 요청
<pre class="pre"><code class="hljs">http://<var class="keyword varname">orgId</var>.messaging.internetofthings.ibmcloud.com:1883/api/v0002/device/types/<var class="keyword varname">typeId</var>/devices/<var class="keyword varname">deviceId</var>/events/<var class="keyword varname">eventId</var></code></pre>

### 보안 POST 요청
<pre class="pre"><code class="hljs">https://<var class="keyword varname">orgId</var>.messaging.internetofthings.ibmcloud.com:8883/api/v0002/device/types/<var class="keyword varname">typeId</var>/devices/<var class="keyword varname">deviceId</var>/events/<var class="keyword varname">eventId</var></code></pre>

**중요 참고사항:**
- HTTP 메시징을 사용해서만 게이트웨이 디바이스 이벤트를 제출할 수 있습니다. 기타 게이트웨이 디바이스 관리 및 제어 기능에 대한 요청을 제출하려면 MQTT 메시징 프로토콜을 사용하십시오. 
- 기본 SSL 포트인 443 포트가 보안 HTTP API 호출에 대해 지정될 수도 있습니다. 
- 게이트웨이에 *표준 게이트웨이* 역할이 지정되지 않은 경우 조직에 있는 디바이스를 대신하여 이벤트를 공개할 수 있습니다. 게이트웨이에 연결된 디바이스가 미등록 상태인 경우 게이트웨이에서 자동으로 해당 디바이스를 등록합니다. 
- 디바이스 권한 레벨을 확인하려는 경우 *표준 게이트웨이* 역할을 지정하십시오. 

게이트웨이 및 리소스 그룹의 역할에 대한 자세한 정보는 [게이트웨이 액세스 제어(베타)](../gateways/gateway-access-control.html)를 참조하십시오. 

### 인증

모든 요청에는 권한 부여 헤더가 포함되어야 합니다. 기본 인증은 지원되는 유일한 메소드입니다. 디바이스가 {{site.data.keyword.iot_short_notm}} HTTP REST API를 사용하여 HTTP 요청을 작성하는 경우 다음 신임 정보가 필요합니다. 

|신임 정보|필수 입력|
|:---|:---|
|사용자 이름| `g/{orgId}/{gwType}/{gwDevId}` 또는 `g-{orgId}-{gwType}-{gwDevId}`
|비밀번호| 게이트웨이 디바이스를 등록할 때 수동으로 지정했거나 자동으로 생성된 인증 토큰입니다.

여기서, 

<dl>
<dt>orgId</dt>  
<dd>조직의 이름이며 호스트 헤더에 지정되어 있는 이름과 일치해야 합니다. </dd>

<p></p>
<dt>gwType</dt>  
<dd>게이트웨이 유형입니다. </dd>
<dd>사용자 이름에서 하이픈 "-" 문자를 구분 기호로 사용하는 경우 이 값에 하이픈 문자가 포함되면 안됩니다. </dd>
<p></p>
<dt>gwDevId</dt>  
<dd>게이트웨이의 디바이스 ID입니다. </dd>
</dl>


### Content-Type 요청 헤더

컨텐츠가 JSON이 아닌 경우 `Content-Type` 요청 헤더는 요청과 함께 제공되어야 합니다. 다음 표에서는 지원되는 유형이 {{site.data.keyword.iot_short_notm}} 내부 형식에 맵핑되는 방법을 보여줍니다. 

|Content-Type 헤더|{{site.data.keyword.iot_short_notm}}의 형식|
|:---|:---|
|text/plain|"text"
|application/json| "json"
|application/xml| "xml"
|application/octet-stream|"bin"

### 서비스 품질(QoS)

MQTT 서비스 품질(QoS) "최대 한 번" 전달 서비스 레벨 0과 유사하게 HTTP REST 메시징은 비지속적 메시지 전달을 제공하지만, 이는 요청이 올바른지와 HTTP 응답을 전송하기 전에 이를 서버에 전달할 수 있는지 유효성을 검증합니다. HTTP 상태 코드 200이 포함된 응답은 메시지가 서버에 전달되었음을 확인합니다. "최대 한 번" MQTT 서비스 품질(QoS) 레벨 또는 HTTP 등가물을 사용하여 이벤트 메시지를 전달하는 경우, 디바이스 및 애플리케이션은 전달을 보장하기 위한 재시도 로직을 구현해야 합니다. 

MQTT 프로토콜 및 {{site.data.keyword.iot_short_notm}}의 서비스 품질(QoS) 레벨에 대한 자세한 정보는 [MQTT 메시징](../reference/mqtt/index.html)을 참조하십시오. 

API를 사용하여 게이트웨이 디바이스를 관리하는 데 대한 자세한 정보는 [게이트웨이 디바이스용 HTTP REST API](../gateways/gw_api.html)를 참조하십시오. 

## 명령 수신
{: #receive_commands}

MQTT 메시징 프로토콜 사용 외에도 HTTP 메시징 API 명령을 사용하여 HTTP를 통해 {{site.data.keyword.iot_short_notm}}에서 이벤트를 명령을 수신하도록 게이트웨이 디바이스를 구성할 수도 있습니다. 게이트웨이 디바이스는 연관된 리소스 그룹 내의 디바이스에 전달되는 명령을 수신할 수 있습니다. 게이트웨이 리소스 그룹에 대한 자세한 정보는 [게이트웨이 액세스 제어(베타)](../gateways/gateway-access-control.html)를 참조하십시오. 

다음 URL 중 하나를 사용하여 {{site.data.keyword.iot_short_notm}}에 연결된 게이트웨이에서 ``POST`` 요청을 제출하십시오. 

### 비보안 POST 요청
<pre class="pre"><code class="hljs">http://<var class="keyword varname">orgId</var>.messaging.internetofthings.ibmcloud.com:1883/api/v0002/device/types/<var class="keyword varname">typeId</var>/devices/<var class="keyword varname">deviceId</var>/commands/<var class="keyword varname">command</var>/request</code></pre>

### 보안 POST 요청

<pre class="pre"><code class="hljs">https://<var class="keyword varname">orgId</var>.messaging.internetofthings.ibmcloud.com:8883/api/v0002/device/types/<var class="keyword varname">typeId</var>/devices/<var class="keyword varname">deviceId</var>/commands/<var class="keyword varname">command</var>/request</code></pre>

**참고:** 기본 SSL 포트인 443 포트가 보안 HTTP API 호출에 대해 지정될 수도 있습니다. 

명령을 대기하는 시간의 최대수(초)를 표시하는 정수를 지정하도록 HTTP 요청의 본문에 매개변수 *waitTimeSecs*를 선택적으로 포함시킬 수 있습니다. 
<pre class="pre"><code class="hljs">{"waitTimeSecs": 5} </code></pre>


**중요 참고사항:**
- *waitTimeSecs*의 값은 0 - 3600초 범위의 정수여야 합니다. 기본값은 0입니다. 
- 디바이스 유형에 대한 명령을 수신하려면 `typeId` 컴포넌트에 대해 "any" 와일드카드 문자(+)를 사용하십시오. 와일드카드 문자가 사용되면 디바이스 유형이 응답 헤더 필드 *X-deviceType*에 포함됩니다.
- 디바이스에 대한 명령을 수신하려면 `deviceId` 컴포넌트에 대해 "any" 와일드카드 문자(+)를 사용하십시오. 와일드카드 문자가 사용되면 디바이스 ID가 응답 헤더 필드 *X-deviceId*에 포함됩니다.
- 명령을 수신하려면 `command` 컴포넌트에 대해 "any" 와일드카드 문자(+)를 사용하십시오. 와일드카드 문자가 사용되면 명령 ID가 응답 헤더 필드 *X-commandId*에 포함됩니다.
- HTTP 응답 상태 코드가 200인 경우, 명령 데이터는 응답의 본문에 포함됩니다. 컨텐츠 유형을 찾으려면 응답 헤더 필드 *Content-Type*을 검토하십시오.
- HTTP 응답 상태 코드가 204인 경우, 명령 데이터를 사용할 수 없습니다. 
