---
title: Web content filtering
description: Use web content filtering in Microsoft Defender ATP to track and regulate access to websites based on their content categories.
keywords: web protection, web threat protection, web browsing, monitoring, reports, cards, domain list, security, phishing, malware, exploit, websites, network protection, Edge, Internet Explorer, Chrome, Firefox, web browser 
search.product: eADQiWindows 10XVcnh
search.appverid: met150
ms.prod: w10
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
ms.author: ellevin
author: levinec
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection: M365-security-compliance 
ms.topic: article
---

# Web Content Filtering

>[!IMPORTANT]
>Some information relates to prereleased product which may be substantially modified before it's commercially released. Microsoft makes no warranties, express or implied, with respect to the information provided here.

>Want to experience Microsoft Defender ATP? [Sign up for a free trial.](https://www.microsoft.com/microsoft-365/windows/microsoft-defender-atp?ocid=docs-wdatp-main-abovefoldlink&rtc=1)

Web content filtering is part of [Web protection](web-protection-overview.md) in Microsoft Defender ATP. It enables your organization to track and regulate access to websites based on their content categories. Many of these websites, while not malicious, might be problematic due to compliance regulations, bandwidth usage, or other concerns.

You can configure policies across your machine groups to block certain categories, effectively preventing users within specified machine groups from accessing URLs within that category. If a category is not blocked, all your users will be able to access the URLs without disruption. However, web content filtering will continue to gather access statistics that you can use to understand web usage and inform future policy decisions. If an element on the page you’re viewing is making calls to a resource which is blocked, you will see a block notification.

Web content filtering is available on most major web browsers, with blocks performed by SmartScreen (Edge) and Network Protection (Internet Explorer, Chrome, Firefox, and all other browsers). See the prerequisites section for more information about browser support.

To summarize the benefits:

- Users are prevented from accessing websites in blocked categories, whether they are browsing on-premises or away
- You can conveniently deploy varied policies to various sets of users using the machine groups defined in the [Microsoft Defender ATP role-based access control settings](https://docs.microsoft.com/windows/security/threat-protection/microsoft-defender-atp/rbac)
- You can access web reports in the same central location, with visibility over actual blocks and web usage

## User experience

The standard blocking experience is provided by Network Protection, which provides a system-level toast notifying the user of a blocked connection.
For a more user-friendly experience, consider using SmartScreen on Edge.

## Prerequisites

Before trying out this feature, make sure you have the following:

- Windows 10 Enterprise E5 license
- Access to Microsoft Defender Security Center portal
- Machines running Windows 10 Anniversary Update (version 1607) or later with the latest MoCAMP update (for Network Protection on Internet Explorer, Edge, Chrome, or Firefox)
- Machines running Windows 10 May 2019 Update (version 1903) or later (for a better user experience from SmartScreen on Edge). Note that if SmartScreen is not turned on, Network Protection will take over the blocking
- A valid license with a partner data provider

## Data handling

For this feature, we will follow whichever region you have elected to use as part of your [Microsoft Defender ATP data handling settings](https://docs.microsoft.com/windows/security/threat-protection/microsoft-defender-atp/data-storage-privacy). Your data will not leave the data center in that region. In addition, your data will not be shared with any third-parties, including our data providers. However, we may send them aggregate data (across users and organizations) to help them improve their feeds.

## Partner licensing

In order to give customers access to various sources of web content categorization data, we are very excited to partner with data providers for this feature. We’ve chosen [Cyren](https://www.cyren.com/threat-intelligence) as our first partner, who we’ve worked with closely to build an integrated solution.

### About Cyren and Threat Intelligence Service for Microsoft Defender ATP

Cyren’s URL filtering includes 70 categories, providing partners with the ability to build powerful and advanced web security applications. Cyren’s comprehensive categories provide the necessary flexibility for any implementation requirement.

The broad range of categories enables numerous applications:

- Protecting users browsing the web from threats such as malware and phishing sites
- Ensuring employee productivity
- Consumer services such as parental control

Cyren's web content classification technology is integrated by design into Microsoft Defender ATP to enable web filtering and auditing capabilities.

Learn more at https://www.cyren.com/products/url-filtering.

### Cyren Permissions

"Sign in and read user profile" allows Cyren to read your tenant info from your Microsoft Defender ATP account, such as your tenant ID, which will be tied to your Cyren license.

"Read and Write Integration settings" exists under the WindowsDefenderATP scope within permissions. This line allows Cyren to add/modify/revoke Cyren license status on the Microsoft Defender ATP portal.

### Signing up for a Cyren License

Cyren is offering a 60-day free trial for all Microsoft Defender ATP customers. To sign up, please follow the steps below from the portal.

>[!NOTE]
>Make sure to add the URL you get redirected to by the signup process to the list of approved domains. 

>[!NOTE]
>A user with AAD app admin/global admin permissions is required to complete these steps.

1. Go to **Reports > Web protection** from the side navigation
2. Select the **Connect to a partner** button
3. Go through the flow from the flyout to register and connect your Cyren account

## Turn on web content filtering

From the left-hand navigation menu, select **Settings > General > Advanced Features**. Scroll down until you see the entry for **Web content filtering**. Switch the toggle to **On** and **Save preferences**.

### Configure web content filtering policies

Web content filtering policies specify which site categories are blocked on which machine groups. To manage the policies, go to **Settings > Rules > Web content filtering**.

Use the filter to locate policies that contain certain blocked categories or are applied to specific machine groups.

### Create a policy

To add a new policy:

1. Select **Add policy** on the **Web content filtering** page in **Settings**.
2. Specify a name.
3. Select the categories to block. Use the expand icon to fully expand each parent category and select specific web content categories.
4. Specify the policy scope. Select the machine groups to specify where to apply the policy. Only machines in the selected machine groups will be prevented from accessing websites in the selected categories.
5. Review the summary and save the policy. The policy may take up to 15 minutes to apply to your selected machines.

>[!NOTE]
>If you are removing a policy or changing machine groups at the same time, this might cause a delay in policy deployment.

## Web content filtering cards and details

Select **Reports > Web protection** to view cards with information about web content filtering and web threat protection. The following cards provide summary information about web content filtering.

### Web activity by category

This card lists the parent web content categories with the largest percentage change in the number of access attempts, whether they have increased or decreased. You can use this card to understand drastic changes in web activity patterns in your organization from last 30 days, 3 months, or 6 months. Select a category name to view more information about that particular category.

In the first 30 days of using this feature, your organization might not have sufficient data to display in this card.

![Image of web activity by category card](images/web-activity-by-category600.png)

### Web content filtering summary card

This card displays the distribution of blocked access attempts across the different parent web content categories. Select one of the colored bars to view more information about a specific parent web category.

![Image of web content filtering summary card](images/web-content-filtering-summary.png)

### Web activity summary card

This card displays the total number of requests for web content in all URLs.

![Image of web activity summary card](images/web-activity-summary.png)

### View card details

You can access the **Report details** for each card by selecting a table row or colored bar from the chart in the card. The report details page for each card contains extensive statistical data about web content categories, website domains, and machine groups.

![Image of web protection report details](images/web-protection-report-details.png)

- **Web categories**: Lists the web content categories that have had access attempts in your organization. Select a specific category to open a summary flyout.

- **Domains**: Lists the web domains that have been accessed or blocked in your organization. Select a specific domain to view detailed information about that domain.

- **Machine groups**: Lists all the machine groups that have generated web activity in your organization

Use the time range filter at the top left of the page to select a time period. You can also filter the information or customize the columns. Select a row to open a flyout pane with even more information about the selected item.

## Errors and issues

### Why am I seeing the error "Need admin approval" when trying to connect to Cyren?

You need to be logged in to an AAD account with either App administrator or Global Administrator privileges. Your IT admin would most likely either have these permissions and/or be able to grant them to you.

### Limitations and known issues in this preview

- Unassigned machines will have incorrect data shown within the report. In the Report details > Machine groups pivot, you may see a row with a blank Machine Group field. This group contains your unassigned machines in the interim before they get put into your specified group. The report for this row may not contain an accurate count of machines or access counts.

- The data in our reports may not be congruent with other data on the site. We currently do not support real-time data processing for this feature, so you may see inconsistencies between the data in our reports and the URL entity page.

## Related topics

- [Web protection overview](web-protection-overview.md)
- [Web threat protection](web-threat-protection.md)
- [Monitor web security](web-protection-monitoring.md)
- [Respond to web threats](web-protection-response.md)
