---

copyright:
  years: 2015, 2016

---

{:new_window: target="\_blank"}
{:shortdesc: .shortdesc}
{:screen: .screen}
{:codeblock: .codeblock}
{:pre: .pre}


# Feature overview
{: #features}

Last updated: 28 July 2016
{: .last-updated}


## Device registry
{: #device-registry}

Manage your inventory, configure security, and store metadata for millions of unique devices.  Define
device types to represent individual device models and apply default metadata to all devices of that type.


## Connectivity
{: #connectivity}

Securely connect your devices, gateways and applications directly to the {{site.data.keyword.iot_short}} via MQTT.  For more information about the advantages of using
the MQTT protocol, see the [MQTT](../reference/mqtt/index.html) reference information.
Model the data from your device as events and control the flow of events into your applications.


## Gateway support
{: #gateway-support}

In many cases where a direct connection can not be made between the service and a device, the {{site.data.keyword.iot_short}} allows
gateway devices to connect that can provide indirect connectivity for multiple devices.


## Device management
{: #device-management}

Optionally, allow the {{site.data.keyword.iot_short}} to manage the lifecycle of your devices by implementing support for
the {{site.data.keyword.iot_short}}'s device management protocol in your devices.  The means by which the device
connects to the service does not affect the device management protocol, which functions the
same for directly connected, indirectly connected, and gateway devices.


## External service integration
{: #external-service-int}

The {{site.data.keyword.iot_short}} supports integration with external services to bring data and operations supported by
other online services into the platform, allowing your application and device developers to
seamlessly interact with those services without ever leaving the comfort of the {{site.data.keyword.iot_short}} APIs.

**Important:** This feature is currently available as part of a limited beta. Future updates  
may include changes incompatible with the current version of this feature. Try it out and [let us know what you think](https://developer.ibm.com/answers/smart-spaces/17/internet-of-things.html).


## Last event cache
{: #last-event-cache}

By using the {{site.data.keyword.iot_short_notm}} Last Event Cache API, you can retrieve the last event that was sent by a device. This works whether the device is online or offline, which allows you to retrieve device status regardless of the device's physical location or use status. You can retrieve the last recorded value of an event ID for a specific device, or the last recorded value for each event ID that was reported by a specific device. Last event data of a device can be retrieved for any specific event that occurred up to 365 days ago.

To request the most recent value for a specific event ID, use the following API request, which returns the last recorded value for the “power” event ID.

```
GET /api/v0002/device/types/<device-type>/devices/<device-id>/events/power
```

The response is returned in the following JSON format:

```
{
    "deviceId": "<device-id>",
    "eventId": "power",
    "format": "json",
    "payload": "eyJzdGF0ZSI6Im9uIn0=",
    "timestamp": "2016-03-14T14:12:06.527+0000",
    "typeId": "<device-type>"
}
```

**Note:** While the API response is in JSON format, event payloads can be written in any format. Payloads returned by Last Event Cache API are encoded in base64.

To request the most recent value for each event ID that was reported by a device, use the following API request:

```
GET /api/v0002/device/types/<device-type>/devices/<device-id>/events
```

The response will include all event IDs that were sent by the device. In the following example, values are returned for the “power” and “temperature” events.

```
[
    {
        "deviceId": "<device-id>",
        "eventId": "power",
        "format": "json",
        "payload": "eyJzdGF0ZSI6Im9uIn0=",
        "timestamp": "2016-03-14T14:12:06.527+0000",
        "typeId": "<device-type>"
    },
    {
        "deviceId": "<device-id>",
        "eventId": "temperature",
        "format": "json",
        "payload": "eyJpbnRlcm5hbCI6MjIsICJleHRlcm5hbCI6MTZ9",
        "timestamp": "2016-03-14T14:17:44.891+0000",
        "typeId": "<device-type>"
    }
]
```
