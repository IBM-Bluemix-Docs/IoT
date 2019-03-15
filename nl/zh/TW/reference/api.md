---

copyright:

years: 2017, 2019
lastupdated: "2019-02-13"

---

{:new_window: target="\_blank"}
{:shortdesc: .shortdesc}
{:screen: .screen}
{:codeblock: .codeblock}
{:pre: .pre}
{:important: .important}


# API
{: #api_overview}

<p>此 {{site.data.keyword.Bluemix}} 文件集合與 {{site.data.keyword.iot_full}}「精簡」定價方案相關，包括基本入門資訊、API 參考資料及一般疑難排解資訊。
如需完整的 {{site.data.keyword.iot_short_notm}} 特性文件，請參閱 IBM Knowledge Center 上的 [{{site.data.keyword.iot_short_notm}} 產品文件 ![外部鏈結圖示](../../icons/launch-glyph.svg "外部鏈結圖示")](https://www.ibm.com/support/knowledgecenter/SSQP8H/iot/overview/overview.html)。您可以在 [{{site.data.keyword.iot_short_notm}} 服務方案](/docs/IoT/plans_overview.html#plans_overview)中找到各種方案的相關資訊。
</p>
{: important}

數個 API 適用於開發連接至 {{site.data.keyword.iot_full}} 的裝置、閘道及應用程式的程式碼。

HTTP API 是以 HTTP 基本鑑別來進行保護。當您使用儀表板來產生 API 金鑰時，會出現金鑰及鑑別記號。如需 API 金鑰及記號的相關資訊，請參閱 [API 金鑰連線![外部鏈結圖示](../../../icons/launch-glyph.svg "外部鏈結圖示")](https://www.ibm.com/support/knowledgecenter/SSQP8H/iot/platform/platform_authorization.html#api-key)。


## 關於 HTTP API
{: #api_about}

針對您自己的組織進行登錄之後，會提供您 6 個字元的組織 ID，在用於任何 HTTP API 呼叫的主機名稱中，都需要此 ID。您可以在下列位址存取您組織的基本 URL：

https://<**orgId**>.internetofthings.ibmcloud.com/api/v0002

若要向應用程式 API 鑑別要求，請將使用者名稱設為 API 金鑰，將密碼設為鑑別記號。

如需「傳訊 API」，請使用下列位址：

https://<**orgId**>.messaging.internetofthings.ibmcloud.com/api/v0002

## HTTP API
{: #api_http}

API|用來...
------------- | -------------
[組織管理 ![外部鏈結圖示](../../../icons/launch-glyph.svg)](https://docs.internetofthings.ibmcloud.com/apis/swagger/v0002/orgAdmin.html){: new_window} |配置組織（包括建立及刪除裝置）、檢查用法、查看服務狀態，以及診斷裝置連線問題。
[安全 ![外部鏈結圖示](../../../icons/launch-glyph.svg)](https://docs.internetofthings.ibmcloud.com/apis/swagger/v0002/security.html){: new_window} |管理使用者、API 金鑰和裝置的鑑別與授權。
[資訊管理 ![外部鏈結圖示](../../../icons/launch-glyph.svg)](https://docs.internetofthings.ibmcloud.com/apis/swagger/v0002/info-mgmt.html){: new_window} |存取裝置事件資料，同時取得並更新裝置位置，以及取得該位置的天氣資訊。
[Data Management ![外部鏈結圖示](../../../icons/launch-glyph.svg)](https://docs.internetofthings.ibmcloud.com/apis/swagger/v0002/state-mgmt.html){: new_window}   |組織及整合在 {{site.data.keyword.iot_short_notm}} 之間往返的資料。
[裝置管理 ![外部鏈結圖示](../../../icons/launch-glyph.svg)](https://docs.internetofthings.ibmcloud.com/apis/swagger/v0002/deviceMgmt.html){: new_window} |使用裝置管理通訊協定來與受管理裝置互動。
[傳訊 ![外部鏈結圖示](../../../icons/launch-glyph.svg)](https://docs.internetofthings.ibmcloud.com/apis/swagger/v0002/http-messaging.html){: new_window}   |使用 HTTP 來發佈事件及傳送指令。
[風險管理 ![外部鏈結圖示](../../../icons/launch-glyph.svg)](https://docs.internetofthings.ibmcloud.com/apis/swagger/v0002/riskmgmt.html){: new_window}   |管理風險管理原則及報告。

## 延伸規格 HTTP API
{: #api_extension}

API|用來...
------------- | -------------
[AT&T 延伸規格 ![外部鏈結圖示](../../../icons/launch-glyph.svg)](https://docs.internetofthings.ibmcloud.com/apis/swagger/v0002/ext-atnt.html){: new_window} |管理 AT&T 裝置。

[Jasper 延伸規格  ![外部鏈結圖示](../../../icons/launch-glyph.svg)](https://docs.internetofthings.ibmcloud.com/apis/swagger/v0002/ext-jasper.html){: new_window} |管理 Jasper 裝置。

[Orange 延伸規格 ![外部鏈結圖示](../../../icons/launch-glyph.svg)](https://docs.internetofthings.ibmcloud.com/apis/swagger/v0002/ext-orange.html){: new_window} |從連接至 {{site.data.keyword.iot_short_notm}} 組織的裝置檢視 SIM 卡資料，以及安裝 Orange SIM 卡。



## 測試版 HTTP API
{: #api_beta}

API|用來...
------------- | -------------
[還原已刪除的裝置 ![外部鏈結圖示](../../../icons/launch-glyph.svg)](https://docs.internetofthings.ibmcloud.com/apis/swagger/v0002-beta/restore-device-beta.html){: new_window}   |如果誤刪了裝置，您可以在 14 天內將它還原。
