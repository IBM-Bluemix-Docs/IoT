---

copyright:
  years: 2018, 2019
lastupdated: "2019-11-19"

keywords: Cloud IAM Authentication, IAM OAuth token, IBM Watson

subcollection: IoT

---

{:new_window: target="\_blank"}
{:shortdesc: .shortdesc}
{:screen: .screen}
{:codeblock: .codeblock}
{:pre: .pre}
{:important: .important}


# {{site.data.keyword.iamshort}} authentication and authorization for {{site.data.keyword.iot_short_notm}} (Beta)
{: #cloud_iam}

<p>This {{site.data.keyword.cloud}} documentation collection pertains to the {{site.data.keyword.iot_full}} Lite pricing plan and includes basic getting started information, API references, and general troubleshooting information. 
For the full {{site.data.keyword.iot_short_notm}} feature documentation, see the [{{site.data.keyword.iot_short_notm}} product documentation ![External link icon](../../../../icons/launch-glyph.svg "External link icon")](https://www.ibm.com/support/knowledgecenter/SSQP8H/iot/overview/overview.html) on {{site.data.keyword.IBM_notm}} Knowledge Center. More information about the various plans can be found in [{{site.data.keyword.iot_short_notm}} service plans](/docs/services/IoT?topic=IoT-plans_overview#plans_overview). 
</p>
{: important}

{{site.data.keyword.iot_full}} APIs support the authentication and authorization of users by using {{site.data.keyword.iamshort}} (IAM).

The {{site.data.keyword.iamlong}} authentication and authorization for {{site.data.keyword.iot_short_notm}} is available only as part of a limited beta program. Future updates might include changes that are incompatible with the current version of this feature.
{: important}

{{site.data.keyword.iamshort}} is built into {{site.data.keyword.cloud_notm}} and is used for authenticating and authorizing administrative and developer users that need to configure and manage their {{site.data.keyword.IBM_notm}} services. Users who need access to the {{site.data.keyword.iot_short_notm}} dashboard are authenticated by using {{site.data.keyword.iamshort}}. The source of identity for {{site.data.keyword.iamshort}} can be registered IBMid users, or it can be a customer’s directory service that supports SAML.  

{{site.data.keyword.iot_short_notm}} also supports authenticating users through {{site.data.keyword.appid_short_notm}}. {{site.data.keyword.appid_short_notm}} is used for authenticating users who need access to applications that are hosted in the {{site.data.keyword.cloud_notm}}. {{site.data.keyword.appid_short_notm}} users do not typically perform administrative or development activities on a cloud service. For more information, see [{{site.data.keyword.appid_short_notm}} Authentication for Watson IoT Platform ![External link icon](../../../../icons/launch-glyph.svg "External link icon")](https://www.ibm.com/support/knowledgecenter/SSQP8H/iot/platform/app_id.html#app_id){: new_window}.

IAM enables users to obtain an IAM OAuth token and use it to authenticate API calls. For example, a user with the {{site.data.keyword.containershort_notm}} CLI installed might use the following command:

`bx iam oauth-tokens`

The command returns the logged-in user's IAM token in the following format:

`IAM Token: Bearer <some token>`

A user can also use the IAM token endpoint to log in and retrieve their IAM token, as shown in the following example:
`curl -s 'https://iam.cloud.ibm.com/identity/token?grant_type=urn:ibm:params:oauth:grant-type:apikey&response_type=cloud_iam&apikey=<apikey>' -H'Content-Type:x-www-form-urlencoded' -XPOST`

This API example uses an IAM API key to request the IAM token and returns the `Bearer <token>`.

Then, when a user calls a {{site.data.keyword.iot_short_notm}} API, they can provide the authorization header `Authorization: Bearer <token>` in their API calls.

## Generating an IAM token
{: #iam_generate}

You can choose how to automate the creation of the IAM token, depending on how you authenticate with {{site.data.keyword.cloud_notm}} and the type of {{site.data.keyword.cloud_notm}} ID that you use.

If you use an unfederated ID, you can choose one of the following options for creating an IAM token:
 - **{{site.data.keyword.cloud_notm}} user name and password:** You can create a token to fully automate the creation of your IAM access token.
 - **Generate an {{site.data.keyword.cloud_notm}} API key:** Use {{site.data.keyword.cloud_notm}} API keys, which are dependent on the {{site.data.keyword.cloud_notm}} account that they are generated for. You cannot combine your {{site.data.keyword.cloud_notm}} API key with a different account ID in the same IAM token. To access clusters that were created with an account other than the one your {{site.data.keyword.cloud_notm}} API key is based on, you must log in to the account to generate a new API key.

If you use a federated ID, you can choose one of the following options for creating an IAM token:
 - **Generate an {{site.data.keyword.cloud_notm}} API key:** {{site.data.keyword.cloud_notm}} API keys are dependent on the {{site.data.keyword.cloud_notm}} account they are generated for. You cannot combine your {{site.data.keyword.cloud_notm}} API key with a different account ID in the same IAM token. To access clusters that were created with an account other than the one your {{site.data.keyword.cloud_notm}} API key is based on, you must log in to the account to generate a new API key.
 - **Use a one-time passcode:** If you authenticate with {{site.data.keyword.cloud_notm}} by using a one-time passcode, you cannot fully automate the creation of your IAM token because the retrieval of your one-time passcode requires a manual interaction with your web browser. To fully automate the creation of your IAM token, you must create an {{site.data.keyword.cloud_notm}} API key instead.

When you create your access token, the body information that is included in your request varies based on the {{site.data.keyword.cloud_notm}} authentication method that you use. Replace the following values:
- `<my_username>` = Your {{site.data.keyword.cloud_notm}} user name.
- `<my_password>` = Your {{site.data.keyword.cloud_notm}} password.
- `<my_api_key>` = Your {{site.data.keyword.cloud_notm}} API key.
- `<my_passcode>` = Your {{site.data.keyword.cloud_notm}} one-time passcode. Run `bx login --sso` and follow the instructions in your CLI output to retrieve your one-time passcode by using your web browser.

Example:
`POST https://iam.<region>.cloud.ibm.com/identity/token`

To specify an {{site.data.keyword.cloud_notm}} region, review the region abbreviations that are used in the API endpoints. See [{{site.data.keyword.cloud_notm}} region API endpoints ![External link icon](../../../../icons/launch-glyph.svg)](https://cloud.ibm.com/docs/containers/cs_regions.html#bluemix_regions){: new_window} for more information.

Input parameter	 | Values
---------------- | -----------
Header	| Content-Type:application/x-www-form-urlencoded<br>Authorization: Basic Xng7Png=<br>Note: You are provided with `Xng7Png=`, the URL-encoded authorization for the username bx and the password bx.
Body for {{site.data.keyword.cloud_notm}} user name and password	|	grant_type: password<br>response_type: cloud_iam, uaa<br>username: `<my_username>`<br>password: `<my_password>`<br>uaa_client_id: cf<br>uaa_client_secret:<br>Note: Add the uaa_client_secret key with no value specified.
Body for {{site.data.keyword.cloud_notm}} API keys	|	grant_type: urn:ibm:params:oauth:grant-type:apikey<br>response_type: cloud_iam<br>uaa<br>apikey: `<my_api_key>`<br>uaa_client_id: cf<br>uaa_client_secret:<br>Note: Add the uaa_client_secret key with no value specified.
Body for {{site.data.keyword.cloud_notm}} one-time passcode	|	grant_type: urn:ibm:params:oauth:grant-type:passcode<br>response_type: cloud_iam, uaa<br>passcode: `<my_passcode>`<br>uaa_client_id: cf<br>uaa_client_secret:<br>Note: Add the uaa_client_secret key with no value specified.

Example API output:

```
{
"access_token": "<iam_token>",
"refresh_token": "<iam_refresh_token>",
"uaa_token": "<uaa_token>",
"uaa_refresh_token": "<uaa_refresh_token>",
"token_type": "Bearer",
"expires_in": 3600,
"expiration": 1493747503
}
```
You can find the IAM token in the **access_token** field of your API ouput.

The following example shows how to use IAM token while calling APIs.

```
GET https://org.domain/api/v0002/bulk/devices
```

Input parameter   |	Values
----------------- | -----------
Headers	|	Content-Type: application/json<br>Authorization: bearer `<iam_token>`
