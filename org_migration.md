---

copyright:
  years: 2016, 2019
lastupdated: "2019-11-18"

keywords: Lite plan, migrate, Watson IoT Platform

subcollection: iot-platform

---

{:new_window: target="\_blank"}
{:shortdesc: .shortdesc}
{:screen: .screen}
{:codeblock: .codeblock}
{:pre: .pre}
{:tip: .tip}
{:important: .important}

# Migrating {{site.data.keyword.iot_short_notm}} Lite to {{site.data.keyword.iot_short_notm}} Non-production or Production
{: #org_migration}

<p>This {{site.data.keyword.cloud}} documentation collection pertains to the {{site.data.keyword.iot_full}} Lite pricing plan and includes basic getting started information, API references, and general troubleshooting information. 
For the full {{site.data.keyword.iot_short_notm}} feature documentation, see the [{{site.data.keyword.iot_short_notm}} product documentation ![External link icon](../../icons/launch-glyph.svg "External link icon")](https://www.ibm.com/support/knowledgecenter/SSQP8H/iot/overview/overview.html) on {{site.data.keyword.IBM}} Knowledge Center. More information about the various plans can be found in [{{site.data.keyword.iot_short_notm}} service plans](/docs/services/IoT?topic=iot-platform-plans_overview#plans_overview). 
</p>
{: important}

After you 'kick the tires' of Watson IoT Platform Lite and have a good understanding of how it fits in with your IoT environment, you can upgrade to [Watson IoT Platform Non-production or to one of the production plans ![External link icon](../../icons/launch-glyph.svg "External link icon")](https://www.ibm.com/support/knowledgecenter/SSQP8H/iot/overview/overview.html){: new_window}.
{:shortdesc}

**Note:** This document is intended only for users who have a Lite instance. If you previously created instances of the IoT Platform with either the Standard or Advanced Security plans, {{site.data.keyword.IBM}} will work with you to migrate your existing {{site.data.keyword.iot_short_notm}} instance to the new non-production or production plans.

## Migration process overview
{: #org_migration_overview}

By migrating to {{site.data.keyword.iot_short_notm}} you remove the Lite plan limits of 500 devices and monthly data consumption.

The {{site.data.keyword.iot_short_notm}} plans include the following additional components to support end-to-end IoT application architecture:

- {{site.data.keyword.messagehub}} - an {{site.data.keyword.IBM_notm}} hosted version of the Kafka streaming platform that your applications can use to receive IoT data.
- {{site.data.keyword.dashdbshort}} for analytical data storage.
- {{site.data.keyword.cloudantfull}} DB for time series data.
- {{site.data.keyword.cos_full}} for long term data retention.

This document describes the types of data you might want to migrate from an existing Lite instance to a full version.

**Note:** Generally it is easiest to set up your {{site.data.keyword.iot_short_notm}} non-production or production environment from scratch, as it includes components and features beyond the {{site.data.keyword.iot_short_notm}} Lite service. Also the devices and users created for testing in the Lite version will likely not be the same ones you'll use for production.

If, however, you want to transfer some of your existing Lite settings, the following sections take you through the process.

Documentation on the [{{site.data.keyword.iot_short_notm}} APIs](/docs/services/IoT?topic=iot-platform-api_overview#api_overview) provides instructions on how to invoke the APIs and their full set of parameters.


## Before you begin
{: #org_migration_byb}

Before you can start the migration process you must purchase {{site.data.keyword.iot_short_notm}} (either production or non-production). Upon purchase, the {{site.data.keyword.IBM_notm}} operations team will provision a new {{site.data.keyword.iot_short_notm}} instance for you. This will include a new, six character, alphanumeric org ID.


## Migrating users
{: #user_migration}

[User Management APIs ![External link icon](../../icons/launch-glyph.svg "External link icon")](https://docs.internetofthings.ibmcloud.com/apis/swagger/v0002/security.html#!/Authorization_-_User_Management){: new_window} provide bulk export and import of {{site.data.keyword.iot_short_notm}} users and can be used to export and import the users you wish to preserve in your new org.

1. Export the users from the Lite org.  
Use the `GET /authorization/users` command to export all of your users from your Lite account org as a JSON object.
2. Clean up the user list.  
If needed, edit the JSON structure to remove any users you do not want to migrate to your new org.
3. Import the users to the new org.  
Use the `POST /authorization/users/multiple` command to import the edited JSON list of users to the new org.

The users now have access to the new org, which will show up in the org selector on the {{site.data.keyword.iot_short_notm}} dashboard.

##  Migrating devices  
{: #device_migration}

Migrating devices may be accomplished in these steps:  
1. Migrate the Device Types that you wish to preserve to the new org.  
2. Migrate the devices themselves to the new org.  
3. Update the hostname that the devices use to connect to {{site.data.keyword.cloud_notm}} to start with your new org id.
4. Migrate any Data Management information you created in the Lite platform.   
This might include Device Physical and Logical Interfaces, Things, and Rules.

<p>Device Types and Devices can be migrated in bulk with the following APIs:
<table>
<tr>
<th> API Documentation </th>
<th> Export API </th>
<th> Import API </th>
</tr>
<tr>
<td> [Device Type API ![External link icon](../../icons/launch-glyph.svg "External link icon")](https://docs.internetofthings.ibmcloud.com/apis/swagger/v0002/org-admin.html) </td>
<td> `GET /device/types` </td>
<td> `POST /device/types` </td>
</tr>
<tr>
<td>  [Device API ![External link icon](../../icons/launch-glyph.svg "External link icon")](https://docs.internetofthings.ibmcloud.com/apis/swagger/v0002/org-admin.html#!/Device_Bulk_Configuration) </td>
<td> `GET /bulk/devices` </td>
<td>  `POST /bulk/devices/add`</td>
</tr>
</table>
</p>
{: tip}


**Important:** {{site.data.keyword.iot_short_notm}} does not store device authentication tokens, only salted version of these. The `GET /bulk/devices` call is thus unable to return the authentication tokens for stored devices. If you have a record of the device authentication tokens you can add these to the JSON object before doing the bulk load. Otherwise, you must generate new device authentication tokens for each device and copy them to the devices.  

If you are using device-side certificates to authenticate devices, rather than authentication tokens, you do not need to do this. However if you are using device-side certificates you must upload the certificates that were used to sign them to the new org.


## Updating devices
{: #update_devices}

When your devices are registered in the new org you must update the configuration or code present on each of your existing devices to use the hostname of the new org.

For MQTT and HTTP messaging clients, use the following hostname:  
`<orgId>.messaging.internetofthings.ibmcloud.com`

Point REST API clients at the following hostname:  
`<orgId>.internetofthings.ibmcloud.com`

**Important:** If you generated new authentication tokens for your devices, you must copy these to each device.


## Device management migration
{: #device_management}

The [Data Management APIs ![External link icon](../../icons/launch-glyph.svg "External link icon")](https://docs.internetofthings.ibmcloud.com/apis/swagger/v0002/state-mgmt.html){: new_window} include APIs for exporting and importing device physical and logical interfaces, thing definitions, and rules.

**Important:** {{site.data.keyword.iot_short_notm}} does not currently support the asset twins concept for data ingestion.

## Boards and cards
{: #boards_cards}

{{site.data.keyword.iot_short_notm}} does not include APIs for importing and exporting definitions and customizations of boards and cards. You must manually recreate these in the new org.

## Enable any required extensions
{: #extensions}

You must recreate any extensions that you have enabled in the Lite platform, such as links to {{site.data.keyword.messagehub}} and {{site.data.keyword.cloudant_short_notm} in the new org.

**Important:** The {{site.data.keyword.messagehub}} and {{site.data.keyword.cloudant_short_notm}} extensions feature has been updated to use [Data Store Connectors (DSC)](https://www.ibm.com/support/knowledgecenter/SSQP8H/iot/platform/reference/dsc/index.html){: new_window}. For more information about migrating your service bindings to DSC, see [Migrating your service bindings](https://www.ibm.com/support/knowledgecenter/SSQP8H/iot/platform/reference/dsc/migration.html){: new_window} in the {site.data.keyword.iot_short_notm}} documentation. 

## Migrating applications
{: #application_migration}

If you have developed applications that call APIs that are offered with the {{site.data.keyword.iot_short_notm}} Lite service to for example send or receive data, or to administer the service, you must update these to use your new {{site.data.keyword.iot_short_notm}} Production or Non-Production instance. This also applies to any Node-RED flows that you might be using.
The migration involves:
- Updating the applications to use a new six character organization id.
- Updating the applications to use the API key and token credentials that you create for your new service instance.

**Important:** If you have been using a Cloud Foundry binding to pass the organization id and credentials to the application, you must use a different mechanism as the new {{site.data.keyword.iot_short_notm}} instance is not provisioned to run in your Cloud Foundry space.

### Generating API connection credentials

The migration process to follow depends on the nature of your application. Generally for all cases the first step is to acquire an API Key and Authentication Token for your application to use.

1. Log in to the top-level dashboard of your new {{site.data.keyword.iot_short_notm}} service.
2. Select the **Usage** tab.
3. Click **View Details** link to bring up the {{site.data.keyword.iot_short_notm}} service information.  
The following information is displayed:
   - The six character orgID
   - API Key and Token.  
   You should generate new API Keys for each of your applications, rather than using the API Key shown here. This allows you to set appropriate permissions for each application.
   - Host URL.
4. Create an API key and authentication token combination for your application.  
You will need these when you configure the application to connect to your organization.   
   1.  Click `Launch`.  
   This will take you through to the underlying service dashboard, that you have used to administer the {{site.data.keyword.iot_short_notm}} Lite service.
   2. Select **Apps**.
   3. Click **Generate API Key**
   4. Copy the API key and authentication token values that are listed.
   5. Select  a role appropriate to your application.   
   6. Add a comment so that you can easily identify this API key and authentication token combination.
   7. Click **Generate**.
   8. **Important:** Make a local copy of the authentication token. It cannot be re-created after you close the window.


### Updating Node-RED applications
You will need to configure your Node-RED nodes to connect to your new {{site.data.keyword.iot_short_notm}} instance. Your `ibmiot` nodes will no longer be able to use the `BluemixService` authentication option so you need to select the `API Key` option instead.
1. Open the `ibmiot` node for editing.
2. Under node properties, select **API Key**.
3. For the API Key field, click the edit icon and then enter the API Key and Authentication Token that you saved from the previous step.
4. Save your changes and redeploy your Node-RED flow.

### Updating an application that doesn't use a Cloud Foundry binding
Identify the location where your application stores the org ID, API Key and Authentication Token, and replace them with the values that you saved earlier.

If your application uses one of the {{site.data.keyword.iot_short_notm}} SDKs, these values are likely to be held in a Properties file.
{: tip}

### Updating an application that uses a Cloud Foundry binding

{{site.data.keyword.cloud_notm}} provides a mechanism to bind Cloud Foundry Applications to one or more Cloud Foundry services. Bindings can be established using the {{site.data.keyword.cloud_notm}} CLI, or by creating a `Connection` between Application and Service in the {{site.data.keyword.cloud_notm}} dashboard.

When an Application is bound to a service, the service API Key and Authentication Token credentials are copied into the `VCAP_SERVICES` environment variable from where the application can retrieve them.

**Important:** This binding mechanism cannot be used with the new {{site.data.keyword.iot_short_notm}} service. You must find the code in your application that is reading from `VCAP_SERVICES` and replace it with code that reads the values from a location where you now store the API Key and Authentication token. To complete the update you must rebuild and redeploy your application.
