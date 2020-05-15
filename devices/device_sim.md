---

copyright:
  years: 2017, 2019
lastupdated: "2019-04-05"

keywords: device simulator, devices

subcollection: IoT

---

{:new_window: target="blank"}
{:shortdesc: .shortdesc}
{:screen: .screen}
{:codeblock: .codeblock}
{:pre: .pre}
{:tip: .tip}
{:important: .important}


# Simulating device data
{: #sim_device_data}

<p>This {{site.data.keyword.cloud}} documentation collection pertains to the {{site.data.keyword.iot_full}} Lite pricing plan and includes basic getting started information, API references, and general troubleshooting information. 
For the full {{site.data.keyword.iot_short_notm}} feature documentation, see the [{{site.data.keyword.iot_short_notm}} product documentation ![External link icon](../../icons/launch-glyph.svg "External link icon")](https://www.ibm.com/support/knowledgecenter/SSQP8H/iot/overview/overview.html) on IBM Knowledge Center. More information about the various plans can be found in [{{site.data.keyword.iot_short_notm}} service plans](/docs/services/IoT?topic=IoT-plans_overview#plans_overview). 
</p>
{: important}

Use the {{site.data.keyword.iot_full}} device simulator to set up simulated events for devices to learn about, test, and demonstrate fully functioning {{site.data.keyword.iot_short_notm}} features without having to register and connect actual devices.
{: shortdesc}

By using the device simulator, you can create simulated devices for existing device types or create new device types and devices. Each simulated device can use unique event details, but you can also create a default configuration that is applied to all devices.

## Before you begin
{: #byb-simulation .sectiontitle}
Enable device simulation for your user ID.
1. Log in to {{site.data.keyword.iot_short_notm}}.
2. From the main navigation pane, select **Settings**.
3. In the **Data and Devices** section, activate the device simulator.

If device simulation is enabled for your user ID, all enabled simulated devices automatically start when you log in to the {{site.data.keyword.iot_short_notm}} dashboard.

## Simulating devices
{: #process-simulation .sectiontitle}
When activated, the device simulator is available on all dashboard pages. A message in the lower-right corner of the screen indicates the number of simulations that are running.

**Important:** The simulated devices and device types that you define for your user ID are available for other users of the {{site.data.keyword.iot_short_notm}} organization. However, to generate simulated data for your devices, you must be logged in to the {{site.data.keyword.iot_short_notm}} dashboard in an active user session.

To simulate device data:
1. From the {{site.data.keyword.iot_short_notm}} dashboard, click the "0 Simulations running" message.
3. In the **Simulations** configuration window that opens, click **Create Simulation**.
4. Configure the simulation details.  
Click **Import/Export Simulation** to import an [existing configuration](#reuse) or manually configure the details:
   1. Select an existing device type that you want to simulate data for or create a new device type by typing the device type name.
   2. Modify the default name for the event type.
   3. Under **Schedule**, set the frequency of the event.
   4. Edit the event payload.  
   Edit the sample JSON payload by adding properties and their corresponding values or use [functions](#functions) to add dynamically generated data points.  
   You can also upload a [CSV event payload file](#csv) to set up the payload.  
   {: tip}
5. Click **New Event Type** to add and configure more event types for the device type.
5. Enable **Save events as historical data** to make your simulated device state data available for later access.  
With historical data enabled, the {{site.data.keyword.iot_short_notm}} [data management ![External link icon](../../icons/launch-glyph.svg "External link icon")](https://www.ibm.com/support/knowledgecenter/SSQP8H/iot/platform/GA_information_management/ga_im_definitions.html){: new_window} components are created and the simulated device state can be accessed from the associated logical interface.  
**Important:** After you enable the device type to save historical data, you cannot add or remove event types, nor can you modify the fields present in the event payloads.
5. Click **Save** to create the device type.  
You are now ready to create one or more simulated devices.
6. Click **Create Simulated Device** to create a device and start sending data.  
**Tip:** To create more than one device, click **1 x** and select the number of devices to create.  
7. To create more simulations, click **New Simulation** and repeat the configuration steps for each device that you want to apply custom settings to.   
The message in the lower-right corner of the screen shows the number of active simulations.
8. On the **Devices** page, browse to one of the simulated devices and select the **Recent Events** tab to verify that the simulated events are working.

You can [export your simulated event configurations](#reuse) for reuse or sharing.

## Event type functions
{: #functions .sectiontitle}

You can use a number of special functions to create dynamic data for your event types.

Function | Usage | Example  
:--- | :---  | :--  
`random(lower, upper)`  | Generates a random number in the specified range.  | `{"random": random(0, 100)}`  
`$counter` | Displays the number of simulated devices of the current type. | `{"total": $counter}`  
`increment(start, increment)` | Specifies the starting value and the increment by which it increases. |`{"myNumber": increment(10, 1)}` </br> In this example, `myNumber` starts at 10 and increases by 1 each time a payload is sent.


## CSV event payload file
{: #csv .sectiontitle}

If you want to create controlled event data for certain scenarios, you can set up the data flow in a CSV input file.

### Requirements
The CSV file must meet the following requirements:
- Each value is a valid [JSON primitive ![External link icon](../../icons/launch-glyph.svg "External link icon")](https://json.org){: new_window}, except as noted:
  - string:   
  Example: "Hello world"
  - number:  
  Example: 0, 0.1, -22, -2.43
  - boolean:  
  true or false
  - null:  
  null
  - **Not supported:**
    - objects  
    Example: {}
    - arrays  
    Example: []
- Values must be comma-delimited.
- Rows must be delimited by using the newline character (`\n`).
- The header row must consist of only string values.


### Sample CSV file
```
"temperature", "confidence","status"
1, 0.1, "normal"
2, 0.2, "normal"
3, 0.3, "error"
4, 0.4, "normal"
```

The first line or "header row" determines the properties that are included in the device JSON in all generated device JSON event objects.
Each subsequent line or "data row" sets the value of those properties in each generated device JSON event object.

**Tip:** When you import the CSV file, you can select **Loop simulated data from file** to cycle through the data lines in sequence to achieve a continuous data feed. If this toggle is not set, each data row in the CSV is sent once at the frequency that is set by the schedule.

The sample CSV file results in event payloads of the following type:
```JSON
{
  "temperature": 1,
  "confidence": 0.1,
  "status": "normal"
}
```

## Sharing and reusing simulations
{: #reuse .sectiontitle}

You can export your simulation details for reuse or sharing:
1. In the **Simulations** window, click **Import/Export**.
2. Select the **Export** tab.
3. Copy the simulation details to the clipboard or download them in a JSON file.
