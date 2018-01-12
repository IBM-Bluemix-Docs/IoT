---

copyright:
  years: 2016, 2018
lastupdated: "2017-11-03"

---

{:new_window: target="\_blank"}
{:shortdesc: .shortdesc}
{:screen: .screen}
{:codeblock: .codeblock}
{:pre: .pre}

# {{site.data.keyword.iot_short_notm}} troubleshooting
{: #ts}

Here are the answers to common troubleshooting questions about using {{site.data.keyword.iot_full}} on {{site.data.keyword.Bluemix_notm}}.
{:shortdesc}

## Problem accessing your {{site.data.keyword.iot_short_notm}} organization
{: #access-expiry-problem}

You cannot log in to a {{site.data.keyword.iot_short_notm}} organization that you own.
{:shortdesc}

You cannot log in to your {{site.data.keyword.iot_short_notm}} organization directly by using the organization URL or by using `https://internetofthings.ibmcloud.com`.
{: tsSymptoms}

Your access to your {{site.data.keyword.iot_short_notm}} organization might have expired. {{site.data.keyword.iot_short_notm}} organizations that were created by using {{site.data.keyword.Bluemix}} use temporary user profiles by default.
{: tsCauses}

You can resolve this problem by accessing your {{site.data.keyword.iot_short_notm}} organization by using {{site.data.keyword.Bluemix_notm}} and changing the expiration setting for your user profile. To change your user expiration settings:

1. From your {{site.data.keyword.Bluemix_notm}} dashboard, open your {{site.data.keyword.iot_short_notm}} service.
2. Click **Members** from the navigation bar.
3. Click the **Edit** icon.
4. Clear the **Access expires** box and click **Save**.
{: tsResolve}

## Problem connecting to the {{site.data.keyword.iot_short_notm}}
{: #connection_problem}

Your connection to the {{site.data.keyword.iot_short_notm}} drops or disconnects unexpectedly.
{:shortdesc}

When you attempt to connect to the {{site.data.keyword.iot_short_notm}}, your device or application receives an error.
{: tsSymptoms}

You might have two devices trying to connect with the same clientID and credentials.Only one unique connection is allowed per clientID. You cannot have two concurrent connections using the same ID. Applications can share the same API key, but MQTT requires that the client ID is always unique.
{: tsCauses}

You can resolve this problem by confirming that you don't have two devices trying to connect by  using the same credentials.
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

