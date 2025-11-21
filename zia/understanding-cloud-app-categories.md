# Understanding Cloud App Categories
Source: https://help.zscaler.com/zia/understanding-cloud-app-categories
PDF: https://help.zscaler.com/pdf/com/en/1399341.pdf

Cloud app categories are a key part of [Cloud App Control](/zia/about-cloud-app-control). The service organizes cloud applications into 19 categories. For 11 of the categories, you can [create rules](/zia/adding-rules-cloud-app-control-policy) to allow or block applications per category. For the other 8 categories, in addition to creating rules to allow or block applications per category, you can also apply granular controls (i.e., the specific actions a user can take within the application) as per your organizational requirements.
Cloud App Categories with Allow or Block Options
Following are the cloud application categories with the allow or block options. To learn how to view the list of supported cloud applications for each category, see [Viewing Supported Cloud Applications](#view-cloud-apps).
- **Consumer**
- **Custom Applications**
- **DNS Over HTTPS Services**
- **Finance**
- **Health Care**
- **Hosting Providers**
- **Human Resources**
- **IT Services**
- **Legal**
- **Productivity & CRM Tools**
- **Sales & Marketing**
Cloud App Categories with Granular Controls
Following are the cloud application categories with granular controls. To learn how to view the list of supported cloud applications for each category, see [Viewing Supported Cloud Applications](#view-cloud-apps).
- **AI & ML Applications**: Granular controls appear when ChatGPT or Microsoft Copilot are chosen with Application Access set to Allow.
- **Collaboration & Online Meetings**: Granular controls appear when Microsoft Teams, SharePoint Online, Slack, or Webex Meetings are chosen with Application Access set to Allow.
- **File Sharing**: Granular controls appear for all the applications and additional granular controls appear when Box, Dropbox, OneDrive, OneDrive for Business, or Google Drive are chosen with Viewing set to Allow.
- **Instant Messaging**: Granular controls appear for all the applications with Chatting set to Allow.
- **Social Networking**: Granular controls appear for all the applications and additional granular controls appear when LinkedIn is chosen with Viewing set to Allow.
- **Streaming Media**: Granular controls appear for all the applications with Viewing/Listening set to Allow.
- **System & Development**: Granular controls appear for all the applications and additional granular controls appear when GitHub is chosen with Viewing set to Allow.
- **Webmail**: Granular controls appear for all the applications with Viewing Mail set to Allow.
If more than one cloud application with granular controls is selected for a category, then only the actions that are common among the selected applications are displayed.
[]Viewing Supported Cloud Applications
To view the supported cloud applications for a cloud app category from the ZIA Admin Portal:
- Go to **Policy** > **URL Filtering & Cloud App Control**.
- From the **Cloud App Control Policy** tab, click **Add** and select a cloud app category.
-
From the Cloud App Category Rule window, click and open the **Cloud Applications **drop-down menu.
The drop-down menu lists the supported cloud applications for the selected cloud app category.
You can look up a cloud application for a URL using the [URL Lookup](/zia/lookup-urls-admin-portal) tool or the [urlLookup](/zia/url-categories#/urlLookup-post) API.
![Screenshot of the Add Cloud App Control Rule Window.](/downloads/zia/documentation-knowledgebase/creating-and-managing-policies/cloud-apps/configuring-cloud-app-policies/cloud-app-categories/ZIA-Add-Cloud-App-Control-Rule-window.png)