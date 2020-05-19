---

copyright:
  years: 2016, 2019
lastupdated: "2019-04-05"

keywords: user access, Add function, members dashboard

subcollection: iot-platform

---

{:new_window: target="blank"}
{:shortdesc: .shortdesc}
{:screen: .screen}
{:codeblock: .codeblock}
{:pre: .pre}
{:important: .important}

# Managing user access
{: #managing-user-access}

<p>This {{site.data.keyword.cloud}} documentation collection pertains to the {{site.data.keyword.iot_full}} Lite pricing plan and includes basic getting started information, API references, and general troubleshooting information. 
For the full {{site.data.keyword.iot_short_notm}} feature documentation, see the [{{site.data.keyword.iot_short_notm}} product documentation ![External link icon](../../icons/launch-glyph.svg "External link icon")](https://www.ibm.com/support/knowledgecenter/SSQP8H/iot/overview/overview.html) on IBM Knowledge Center. More information about the various plans can be found in [{{site.data.keyword.iot_short_notm}} service plans](/docs/services/IoT?topic=IoT-plans_overview#plans_overview). 
</p>
{: important}

From the Members page of the dashboard, you can control and manage access to your {{site.data.keyword.iot_full}} organization. You can add users by adding, inviting, or importing them. You can also give different levels of access to your users by assigning roles.
{:shortdesc}

## Adding users
{: #adding-new-users}

From the **Members** page of the dashboard, you can add individual members by using the Add function. You can also add members simultaneously by using the Import function.

By default, members accounts do not expire. When you add users to your {{site.data.keyword.iot_short_notm}} org, you can optionally set an expiry date for their account.

### Adding members to your {{site.data.keyword.iot_short_notm}} organization

To add a member to your organization, you will need the IBMid of the member. To add a member, you do not need confirmation from the member.

To add a single member to your {{site.data.keyword.iot_short_notm}} organization:
1. In your {{site.data.keyword.iot_short_notm}} dashboard, click **Members** from the navigation bar.
2. Click **Add Members** and select the **Add** tab.
3. Enter the IBMid of the member.
4. Select a role for the member.
5. Optional: Set an expiry date.
6. Click **Add**.

To add multiple members simultaneously, you must upload a `.csv` file that contains the IBMid, the role, and the optional expiry date for each member. For information, see [Constructing your CSV file](#constructing-your-csv).
1. In your {{site.data.keyword.iot_short_notm}} dashboard, click **Members** from the navigation bar.
2. Click **Add Members** and select the **Import** tab.
3. Browse your files or drag the `.csv` file into the **Upload CSV** window.
4. Select a default role to use if a role specified in the CSV file is not recognized.
5. Map the column numbers in your CSV file to the corresponding IBMid, role, and optional expiry date entries.
6. Select the appropriate comma or semicolon column separator to match the separator used in your `.csv` file.
7. Click **Import** to import the IBMids and create the members.


### Constructing your CSV file
{: #constructing-your-csv}

When you construct a CSV file to import members into your organization, ensure that you include the required information for the method that you are using. Use either commas or semicolons to separate columns.  
**Important:** When you upload the CSV file, under **CSV settings**, ensure that you select the correct column separator.

Sample CSV file with comma delimitation:  
```
user1@sample.com,PD_DEVELOPER_USER,2018-03-13
user2@sample.com,PD_OPERATOR_USER,2018-03-13
user3@sample.com,PD_ADMIN_USER,2018-03-13
```
Where the following column entries are used:  
- Column 1: The email address of the user.  
If you are adding members, make sure that you use the email address that corresponds to a valid IBMid. If you are inviting members, you can use any valid email address.
- Column 2: The role to be assigned to the user.  
Enter one of the following roles:
 - PD_ADMIN_USER
 - PD_OPERATOR_USER
 - PD_DEVELOPER_USER
 - PD_ANALYST_USER
 - PD_READER_USER  
 For more information about user roles, see [User, application, and gateway roles ![External link icon](../../icons/launch-glyph.svg "External link icon")](https://www.ibm.com/support/knowledgecenter/SSQP8H/iot/platform/roles_index.html#user_roles){: new_window}.
- Column 3: The ISO 6801 date (for example, `2018-03-13`) that corresponds to the user expiry date.

## Editing users
{: #editing-users}

Users can be edited to change their role, add, remove, or change an access expiration date, or add or remove access to the organization.

1. In your {{site.data.keyword.iot_short_notm}} dashboard, click **Members** from the navigation bar.
2. Click the **Edit** icon next to the user you wish to edit.
3. Make the desired changes to the user.
4. Click **Save**.

## Blocking user access
{: #blocking-users}

Users can be blocked from accessing the {{site.data.keyword.iot_short_notm}} organization, while still maintaining organization membership.

1. In your {{site.data.keyword.iot_short_notm}} dashboard, click **Members** from the navigation bar.
2. Click the toggle next to the user you wish to block from accessing the {{site.data.keyword.iot_short_notm}} organization.

## Limiting user access
{: #limiting-users}

Resource-level access control enables you to limit access to devices in an organization. You can use resource groups to specify the devices that each user or API key can manage. For information on how to configure resource-level access control, see [Configuring resource-level access control ![External link icon](../../icons/launch-glyph.svg "External link icon")](https://www.ibm.com/support/knowledgecenter/SSQP8H/iot/platform/reference/rlac.html#configure_RLAC){: new_window}.

## Removing users
{: #removing-users}

Users can be removed entirely from the {{site.data.keyword.iot_short_notm}} organization. Removing users cannot be undone, and users must be [added to the platform](#adding-new-users) to restore access.

1. In your {{site.data.keyword.iot_short_notm}} dashboard, click **Members** from the navigation bar.
2. Click the **Delete** icon next to the user to remove.
3. Click **Delete** in the confirmation dialog box.
