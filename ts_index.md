---

copyright:
  years: 2016, 2019
lastupdated: "2019-04-05"

keywords: Watson IoT Platform, Watson IoT Platform organization, IoT Platform, troubleshooting

subcollection: IoT

---

{:new_window: target="\_blank"}
{:shortdesc: .shortdesc}
{:screen: .screen}
{:codeblock: .codeblock}
{:pre: .pre}
{:important: .important}

# {{site.data.keyword.iot_short_notm}} troubleshooting
{: #ts}

<p>This {{site.data.keyword.cloud}} documentation collection pertains to the {{site.data.keyword.iot_full}} Lite pricing plan and includes basic getting started information, API references, and general troubleshooting information. 
For the full {{site.data.keyword.iot_short_notm}} feature documentation, see the [{{site.data.keyword.iot_short_notm}} product documentation ![External link icon](../../icons/launch-glyph.svg "External link icon")](https://www.ibm.com/support/knowledgecenter/SSQP8H/iot/overview/overview.html) on IBM Knowledge Center. More information about the various plans can be found in [{{site.data.keyword.iot_short_notm}} service plans](/docs/services/IoT?topic=IoT-plans_overview#plans_overview). 
</p>
{: important}

Here are the answers to common troubleshooting questions about using {{site.data.keyword.iot_full}} on {{site.data.keyword.cloud_notm}}.
{:shortdesc}

## Problem accessing your {{site.data.keyword.iot_short_notm}} organization
{: #access-expiry-problem}

You cannot log in to a {{site.data.keyword.iot_short_notm}} organization that you own.
{:shortdesc}

You cannot log in to your {{site.data.keyword.iot_short_notm}} organization directly by using the organization URL or by using `https://internetofthings.ibmcloud.com`.
{: tsSymptoms}

Your access to your {{site.data.keyword.iot_short_notm}} organization might have expired. {{site.data.keyword.iot_short_notm}} organizations that were created by using {{site.data.keyword.cloud}} use temporary user profiles by default.
{: tsCauses}

You can resolve this problem by accessing your {{site.data.keyword.iot_short_notm}} organization by using {{site.data.keyword.cloud_notm}} and changing the expiration setting for your user profile. To change your user expiration settings:

1. From your {{site.data.keyword.cloud_notm}} dashboard, open your {{site.data.keyword.iot_short_notm}} service.
2. Click **Members** from the navigation bar.
3. Click the **Edit** icon.
4. Clear the **Access expires** check box and click **Save**.
{: tsResolve}

## Problem connecting to the {{site.data.keyword.iot_short_notm}}
{: #connection_problem}

Your connection to the {{site.data.keyword.iot_short_notm}} drops or disconnects unexpectedly.
{:shortdesc}

When you attempt to connect to the {{site.data.keyword.iot_short_notm}}, your device or application receives an error.
{: tsSymptoms}

You might have more than one device that is trying to connect with the same client ID and credentials. Only one unique connection is allowed per clientID. You cannot have multiple concurrent connections that use the same ID. Applications can share the same API key, but MQTT requires that the client ID is always unique.
{: tsCauses}

You can rule out this reason by verifying that you don't have multiple devices that are trying to connect by using the same credentials.
{: tsResolve}

## Device intermittently disconnects from {{site.data.keyword.iot_short_notm}}
{: #disconnection_problem}

Your device connection to the {{site.data.keyword.iot_short_notm}} intermittently drops unexpectedly.
{:shortdesc}

A device that is connected to the {{site.data.keyword.iot_short_notm}} service is disconnected intermittently. The device reconnects, but it is unexpectedly disconnected again after a while.
{: tsSymptoms}

It might be that when you connect, you are using a value for an MQTT ping option that is too low, which makes it look like the connection timed out. For example, if the client MQTT is set incorrectly, pings are not received in a timely manner, and the connection is closed.
{: tsCauses}

You can fix this problem by confirming that you have properly set the ping and KeepAlive parameters for your connection.   
{: tsResolve}

## Subscription to Device events fails using MQTT
{: #mqtt_subscribe}

When you subscribe to events for a device, the connection always closes so the subscription does not take effect.

You see a message like the following on the dashboard:
Closed connection. The topic is not valid: *format_string*. The topic does not match an authorized rule
{: tsSymptoms}

This error occurs if you try to subscribe using an incorrect Client ID format. 
{: tsCauses}

When you make an MQTT connection to subscribe to an events topic, you must 
- Generate and use an API Key
- Use a client ID format of `a:orgId:appId`
{: tsResolve}

Fix the ID format, then try again. For details, refer to [MQTT authentication](https://www.ibm.com/support/knowledgecenter/SSQP8H/iot/platform/applications/mqtt.html).

