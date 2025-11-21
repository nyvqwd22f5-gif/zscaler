# Creating a ServiceNow Ticket
Source: https://help.zscaler.com/itdr/creating-servicenow-ticket
PDF: https://help.zscaler.com/pdf/com/en/1531881.pdf

You can integrate Zscaler ITDR with ServiceNow to create incidents to track and assess issues across the Zscaler ITDR Admin Portal (AD domain, Entra ID, and credential issues) and bad changes detected in the AD domain and Entra ID. You can create a ServiceNow ticket for AD domain issues, exposed credential issues, Entra ID issues or bad changes in the ITDR Admin Portal via the following dashboards:
- Active Directory Posture
- Active Directory Change Detection
- Endpoint Credential Exposure
- Entra ID Posture
- Entra ID Change Detection
To create a ServiceNow ticket:
- Go to the required dashboard:
- [Active Directory Posture](#ADdashboard)
- [Active Directory Change Detection](#ad-changedetection)
- [Endpoint Credential Exposure](#ece-dashboard)
- [Entra ID Posture](#entraid-dashboard)
- [Entra ID Change Detection](#entraID-changedetection)
-
In the **Create ServiceNow Ticket** window, the following fields are auto-populated. You can update them as required.
- **Short Description**: The issue name.
- **Description**: The description of the issue and the link to the issue.
- **Impact**: The impact (**High**, **Medium**, or **Low**) of the issue in the ITDR Admin Portal.
- **Urgency**: The urgency (**High**, **Medium**, or **Low**) of the issue in the ServiceNow portal.
[See image.](#create-servicenowticket)
- Click **Submit**.
You can view the list of tickets on the [ServiceNow ](https://help.zscaler.com/itdr/v4_29/viewing-incident-details)page.
-
[]On the **Active Directory Posture** dashboard:
- Select an AD domain from the **Result for** drop-down menu.
- Select a timestamp from the **scanned on** the drop-down menu.
The scan result for the AD domain appears.
- Click **Detailed Findings and Recommendations**, or click an issue for which you want to create a ServiceNow ticket.
-
Click **Actions **and select **Create ServiceNow Ticket**.
[See image.](#ad-posture-dashboard)
- []Go to **ITDR** > **Dashboard **> **Active Directory Change Detection** > **Default**.
- Select an AD domain from the **Result for** drop-down menu.
-
Click the **Create ServiceNow Ticket** icon under **Actions **for the bad change you want to track.
[See image.](#ad-cd-servicenow)
- []Go to **ITDR** > **Dashboard** > **Endpoint Credential Exposure**.
- Select a date from the **As of Date** calendar to view the total number of exposed credential issues on that scan date.
- Click **Detailed Findings and Recommendations**,** **or click an exposed credential issue for which you want to create a ServiceNow ticket.
-
Click **Actions **and select **Create ServiceNow Ticket**.
[See image.](#ece-ticket)
- []On the **Entra ID Posture **dashboard:
- Select an Entra ID tenant from the **Result for** drop-down menu.
- Select a timestamp from the **scanned on** drop-down menu.
- Click **Detailed Findings and Recommendations**, or click an issue for which you want to create a ServiceNow ticket.
-
Click **Actions **and select **Create ServiceNow Ticket**.
[See image.](#entra-ID-posture)
- []Go to **ITDR** > **Dashboard **> **Entra ID Change Detection** > **Default**.
- Select an AD domain from the **Result for** drop-down menu.
-
Click the **Create ServiceNow Ticket** icon under **Actions **for the bad change you want to track.
[See image.](#entra-ID-change-detection)
[]![The Entra ID Posture dashboard listing the detailed findings of posture issues, the Actions menu, and the Create ServiceNow Ticket option.](/downloads/itdr/third-party-integrations/creating-servicenow-ticket/itdr-entraID-posture.png)
[]![The Entra ID Change Detection dashboard with the Create ServiceNow Ticket icon.](/downloads/itdr/third-party-integrations/creating-servicenow-ticket/itdr-entraID-changedetection.png)
[]![The Endpoint Credential Exposure dashboard listing the detailed findings of credential issues, the Actions menu, and the Create ServiceNow Ticket option.](/downloads/itdr/third-party-integrations/creating-servicenow-ticket/itdr-ece-dashboard.png)
[]
![The Active Directory Posture dashboard listing the detailed findings of AD domain issues, the Actions menu, and the Create ServiceNow Ticket option.](/downloads/itdr/third-party-integrations/creating-servicenow-ticket/itdr-active-directory-posture.png)
[]![The Create ServiceNow Ticket window with fields populated.](/downloads/itdr/third-party-integrations/creating-servicenow-ticket/itdr-create-servicenow-ticket-window.jpg)
[]
![The Active Directory Change Detection dashboard with the Create ServiceNow Ticket icon.](/downloads/itdr/third-party-integrations/creating-servicenow-ticket/itdr-change-detection-icon.png)