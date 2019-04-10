---

copyright:

years: 2017, 2019
lastupdated: "2019-04-10"

keywords: own organization, Extension HTTP APIs, API Use, AT&T Extension, Administer AT&T

subcollection: iot-platform

---

{:new_window: target="\_blank"}
{:shortdesc: .shortdesc}
{:screen: .screen}
{:codeblock: .codeblock}
{:pre: .pre}
{:important: .important}


# APIs
{: #api_overview}

<p>This {{site.data.keyword.Bluemix}} documentation collection pertains to the {{site.data.keyword.iot_full}} Lite pricing plan and includes basic getting started information, API references, and general troubleshooting information. 
For the full {{site.data.keyword.iot_short_notm}} feature documentation, see the [{{site.data.keyword.iot_short_notm}} product documentation ![External link icon](../../icons/launch-glyph.svg "External link icon")](https://www.ibm.com/support/knowledgecenter/SSQP8H/iot/overview/overview.html) on IBM Knowledge Center. More information about the various plans can be found in [{{site.data.keyword.iot_short_notm}} service plans](/docs/services/IoT?topic=iot-platform-plans_overview#plans_overview). 
</p>
{: important}

Several APIs are available for developing code for devices, gateways, and applications that connect to {{site.data.keyword.iot_full}}.

The HTTP APIs are protected with HTTP basic authentication. When you generate an API key by using the dashboard, you are presented with a key and an authentication token. For more information about API keys and tokens, see [API key connection ![External link icon](../../../icons/launch-glyph.svg "External link icon")](https://www.ibm.com/support/knowledgecenter/SSQP8H/iot/platform/platform_authorization.html#api-key).


## About HTTP APIs
{: #api_about}

After registering for your own organization, you are provided with a 6 character organization ID which is required in the hostname for any HTTP API calls. The base URL for your organization can be accessed at the following address:

https://<**orgId**>.internetofthings.ibmcloud.com/docs/index.html

From this landing page you can access the documentation for the available {{site.data.keyword.iot_short_notm}} APIs.

You will be prompted to log in to your organization, and when logged in you have access to execute API calls directly from the documentation.

<!-- To authenticate requests to the application API, set the username to the API key and the password to the authentication token. -->

## HTTP APIs
{: #api_http}

API                     | Use to ...       
------------- | -------------
[Organization Administration ![External link icon](../../../icons/launch-glyph.svg)](https://docs.internetofthings.ibmcloud.com/apis/swagger/v0002/orgAdmin.html){: new_window} | Configure an organization (including creating and deleting devices), check usage, see service status, and diagnose device connection problems.
[Security ![External link icon](../../../icons/launch-glyph.svg)](https://docs.internetofthings.ibmcloud.com/apis/swagger/v0002/security.html){: new_window} | Manage the authentication and authorization of users, API keys, and devices.
[Information Management ![External link icon](../../../icons/launch-glyph.svg)](https://docs.internetofthings.ibmcloud.com/apis/swagger/v0002/info-mgmt.html){: new_window} |  Access device event data and also get and update device location and obtain weather information for that location.
[Data Management  ![External link icon](../../../icons/launch-glyph.svg)](https://docs.internetofthings.ibmcloud.com/apis/swagger/v0002/state-mgmt.html){: new_window}   |   Organize and integrate data coming in to and going out of {{site.data.keyword.iot_short_notm}}.
[Device Management ![External link icon](../../../icons/launch-glyph.svg)](https://docs.internetofthings.ibmcloud.com/apis/swagger/v0002/deviceMgmt.html){: new_window} | Interact with managed devices by using the device management protocol.
[Messaging ![External link icon](../../../icons/launch-glyph.svg)](https://docs.internetofthings.ibmcloud.com/apis/swagger/v0002/http-messaging.html){: new_window}   | Publish events and send commands by using HTTP.
[Risk Management ![External link icon](../../../icons/launch-glyph.svg)](https://docs.internetofthings.ibmcloud.com/apis/swagger/v0002/riskmgmt.html){: new_window}   | Manage the risk management policies and reports.

## Extension HTTP APIs
{: #api_extension}

API                     | Use to ...       
------------- | -------------
[AT&T Extension ![External link icon](../../../icons/launch-glyph.svg)](https://docs.internetofthings.ibmcloud.com/apis/swagger/v0002/ext-atnt.html){: new_window} | Administer AT&T devices.
[Jasper Extension  ![External link icon](../../../icons/launch-glyph.svg)](https://docs.internetofthings.ibmcloud.com/apis/swagger/v0002/ext-jasper.html){: new_window} | Administer Jasper devices.
<!--[Orange Extension  ![External link icon](../../../icons/launch-glyph.svg)](https://docs.internetofthings.ibmcloud.com/apis/swagger/v0002/ext-orange.html){: new_window} | View SIM card data from devices that are connected to your {{site.data.keyword.iot_short_notm}} organization and have an Orange SIM card installed.-->

## Beta HTTP APIs
{: #api_beta}

API                     | Use to ...       
------------- | -------------
[Client Connection Status ![External link icon](../../../icons/launch-glyph.svg)](https://docs.internetofthings.ibmcloud.com/apis/swagger/v0002-beta/clientstate-beta.html#/){: new_window}   | Retrieve and query the client connection state for devices, gateways and applications that have connected to {{site.data.keyword.iot_short_notm}}.
[Restore Deleted Devices ![External link icon](../../../icons/launch-glyph.svg)](https://docs.internetofthings.ibmcloud.com/apis/swagger/v0002-beta/restore-device-beta.html){: new_window}   | If a device deleted by mistake, you can restore it within 14 days.
