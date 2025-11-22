# Managing Custom Email Domains
Source: https://help.zscaler.com/workflow-automation/managing-custom-email-domains
PDF: https://help.zscaler.com/pdf/com/en/1517456.pdf

Adding custom email domains is optional when configuring Workflow Automation. Admins with access to Workflow Automation can manage custom email domains. Workflow Automation generates and sends email notifications for the various actions that you can perform, such as notifying the user of an incident, escalating an incident to an approver or manager, and performing bulk actions. By default, Workflow Automation uses notifications@zsworkflow.net as the sender for these email notifications. After you add a custom email domain, Workflow Automation can use that custom email domain as the sender.
In the Workflow Automation Admin Portal, on the Custom Email Domain page, admins can:
- [Add Custom Email Domains](#heading-add-custom-email-domains)
- [Specify the Default Custom Email Domain](#header-specify-default-custom-email-domain)
- [Edit Custom Email Domains](#header-edit-custom-email-domains)
- [Regenerate DNS Records for Expired Custom Email Domains](#header-regenerate-dns-records-expired-domain)
- [Reverting to the Zscaler Domain](#header-revert-back-to-Zscaler-domain)
- [View Custom Email Domains](#header-view-custom-email-domain)
[][]To add a custom email domain:
-
Go to **Setup** > **Custom Email Domain**. The **Custom Email Domain** page appears, listing all the custom email domains for your organization.
[See image.](#image-custom-email-domain-initial)
-
On the **Custom Email Domain** page, click **Add Domain**. The **Custom Email Domain Setup** wizard appears, displaying the overview page for the wizard. On the overview page, you can see the different steps required to add a custom email domain. Step 1 is highlighted with a blue circle.
[See image.](#image-custom-email-domain-setup-wizard-initial)
- Click **Initial Setup**. The **Add Custom Domain** page appears.
-
On the **Add Custom Domain** page:
- **Domain Name**: Enter the name of the custom email domain.
- **Envelope Sender Domain Name**: Enter the name of the envelope sender domain. Configuring this field improves email deliverability, helps with Sender Policy Framework (SPF) alignment, and ensures a consistent sending identity for your notifications.
- **Originating Email Address**: Enter the email address from which email notifications are sent.
[See image.](#image-add-custom-domain-page)
- Click **Add**. The **Next** button becomes available.
-
Click **Next**. Workflow Automation generates DNS records for domain verification, and the **Add DNS Record** page appears, displaying those DNS records in a table. A message is displayed on the page stating that the system verification is in progress and that it might take up to 72 hours for the verification to complete. The status of the custom email domain is set to **DNS verification pending**.
[See image.](#image-add-dns-record-page)
-
In your DNS provider, publish the DNS records that are displayed in the table. For each DNS record, click the **Copy** icon next to the **Name** field and **Value** field. You paste these values in your DNS provider. You must publish these DNS records to your DNS provider within 72 hours. If you do not publish these DNS records within 72 hours, the status of the custom email domain changes to **Expired**. After the custom email domain expires, you can regenerate DNS records for the domain. To learn more, see [Regenerate DNS Records for Expired Custom Email Domains](#link-regenerate-dns-record-section).
[See image.](#image-add-dns-record-page-copy-icons)
After you publish the DNS records to the DNS provider, the DNS server calls Amazon Web Services (AWS) to check whether the records are valid. This verification process can take some time. After the verification process is complete:
-
If the records are valid, the custom email domain is added, and the status of the custom email changes to **Success. **You can now use this custom email domain for your notifications. In addition, a message is displayed on the **Add DNS Record** page stating that the domain was successfully verified, and the **Next** button becomes available. When you click the **Next** button, the **Verify Custom Domain Setup** page appears, where you can send a test email from the custom email domain to verify that it is working correctly. This step is optional.
[See image.](#add-dns-record-page-domain-successfully-verified)
-
If the records are not valid, or if there is a technical issue with verifying the records, the custom email domain is not added and the status of the custom email domain changes to **Failed**. To use a custom domain that has a **Failed** status, you must delete the custom email domain and add it again so that the system can regenerate the DNS records.
[See image.](#add-dns-record-page-domain-verification-failed)
-
(Optional) Click **Next**. The **Verify Custom Domain Setup** page appears.
[See image.](#image-verify-custom-domain-setup-page)
- On the **Verify Custom Domain Setup** page, in the **Send Test Email To** field, enter the email address to which you want to send the test email.
- Click **Send Test Email**. The test email is sent to the email address you entered.
-
Click **Finish**. The **Custom Email Domain** page appears, listing the custom email domain with a **Success **status, and the **Make Default** icon appears in the **Action** column.
[See image.](#image-custom-email-domain-page-after-add)
[]To specify the default custom email domain:
- Go to **Setup** > **Custom Email Domain**. The **Custom Email Domain** page appears, listing all the custom email domains for your organization.
-
On the **Custom Email Domain** page, in the **Action** column, click the **Make Default** icon next to a domain name with a status of **Success**. You can only specify one custom email domain as the default. The status of the custom email domain changes to **In Use**.
[See image.](#custom-email-domain-make-default-icon)
[]To edit a custom email domain:
- Go to **Setup** > **Custom Email Domain**. The **Custom Email Domain** page appears, listing all the custom email domains for your organization.
- On the **Custom Email Domain** page, in the **Action** column, click the **Edit** icon next to a domain name that has a status of **Success**, **In Use**, or **DNS verification pending**.
- If the custom email domain has a **DNS verification pending **status, the **Add DNS Record** page appears. From that page, you can continue adding the custom email domain.
- If the custom email domain has an **In Use** or **Success** status, the **Add Custom Domain** page appears. You can only edit the **Originating Email Address** field. Edit the **Originating Email Address** field and then click **Update**. The **Next** button becomes available. When you click the **Next **button, the **Verify Custom Domain Setup** page appears. From that page, you can send a test email again to verify that the custom email domain is working correctly.
To delete a custom email domain, in the **Action** column, click the **Delete** icon next to a domain name. You cannot delete a custom email domain with a status of **In Use**. You can select another domain and make it the default, and then you can delete the previous domain that was the default.
[][]To regenerate DNS records for an expired custom email domain:
- Go to **Setup** > **Custom Email Domain**. The **Custom Email Domain** page appears, listing all the custom email domains for your organization.
-
On the **Custom Email Domain** page, in the **Action** column, click the **Regenerate** icon next to a domain name that has a status of **Expired**.
[See image.](#image-custom-email-domain-regenerate-icon)
Workflow Automation regenerates the DNS records for the domain, and the **Add DNS Record** page appears, displaying those new DNS records.
- Continue with adding the custom email domain. To learn more, see [Adding a Custom Email Domain](#add-custom-email-domain).
[]To revert to the Zscaler domain:
- Go to **Setup** > **Custom Email Domain**. The **Custom Email Domain** page appears, listing all the custom email domains for your organization.
-
On the **Custom Email Domain** page, click **Revert to Zscaler Domain**. A message appears asking whether you are sure that you want to revert to zsworkflow.net as the originating email domain.
[See image.](#custom-email-domain-revert-to-zscaler-domain)
-
Click **Yes**.
The** Revert to Zscaler Domain **button changes to **Zscaler Domain in use**, and you cannot click it.
[See image.](#custom-email-domain-Zscaler-Domain-In-Use)
To use your custom email domain again as the default, in the **Action** column, click the **Make Default** icon next to the domain name that you want to set as the default. After you select the default, **Revert to Zscaler Domain** becomes available again.
[]To view custom email domains, go to **Setup** > **Custom Email Domain**. The **Custom Email Domain** page appears, listing all the custom email domains for your organization. The custom email domain you specified as the default appears in bold. For custom email domains, you can view the following information:
- **Domain Name**: The name of the custom email domain.
- **Envelope Sender Domain Name**: The name of the envelope sender domain configured for your custom email domain. This field improves email deliverability, helps with SPF alignment, and ensures a consistent sending identity for your notifications.
- **Originating Email Address**: The email address from the custom email domain that shows as the sender of notifications.
- **Last Updated**: The date and time when the custom email domain was last updated.
- **Status**: The status of the custom email domain. Statuses are:
- **DNS verification pending**:** **The custom email domain is pending verification of the DNS records. Only the **Add Custom Domain** page (first step) is complete for this domain.
- **Expired**: The custom email domain is expired. You did not publish the DNS records to your DNS provider within the 72-hour deadline. If the custom domain has expired, you can regenerate the DNS records and publish them to your DNS provider. To learn more, see [Regenerate DNS Records for Expired Custom Email Domains](#link-regenerate-dns-record-section).
- **Failed**: The custom email domain failed the verification of DNS records by AWS. To use this domain, you must delete it and then add it again so that the system can regenerate the DNS records.
- **In Use**: The custom email domain that is set as the default for the email notifications. You can only set one custom email domain to this status.
- **Success**: The custom email domain is verified. All the pages required for adding a custom email domain are complete. Only custom email domains with a **Success **status can be set as the default.
[See image.](#view-custom-email-domains)
To view the details for a custom email domain:
- Go to **Setup** > **Custom Email Domain**. The **Custom Email Domain** page appears, listing all the custom email domains for your organization.
-
On the **Custom Email Domain** page, in the **Action** column, click the **View Domain** icon next to a domain name. The overview page for the **Custom Email Domain Setup** wizard appears. Depending on the status of the domain, a **View **button appears under the pages that you previously completed and you can view.
[See image.](#view-details-custom-email-domain)
- Under the page that you want to view, click **View**. That page appears, displaying the information that you added on that page.
-
(Optional) To view the information on the other pages, click **Next** or **Back** to navigate through the other pages.
[See image.](#viewing-custom-email-domain-back-next-buttons)
[]![The Custom Email Domain page displaying the existing custom email domains for your organization. The page contains the Add Domain button and Revert to Zscaler Domain button above a table with columns for Domain Name, Envelope Sender Domain, Originating Email Address, Last Updated, Status, and Action.](/downloads/workflow-automation/setup/managing-custom-email-domains/WA-Cust-Email-Domain-Page-Initial_1.png)
[]![Viewing the Custom Email Domain Setup wizard on the Custom Email Domain page](/downloads/workflow-automation/setup/managing-custom-email-domains/WA-Cust-Email-Domain-Setup-Wizard_0.png)
[]![Viewing the Add Custom Domain page in the Custom Email Domain Setup wizard](/downloads/workflow-automation/setup/managing-custom-email-domains/WA-Add-Custom-Domain-Page_2.png)
[]![Viewing the DNS records generated by Workflow Automation on the Add DNS Record page. This page has a table with columns for Type, Name, Value, and TTL.](/downloads/workflow-automation/setup/managing-custom-email-domains/WA-Add-DNS-Record-PG-System-Verification-Inprogress_0.png)
[]![Viewing the copy icons on the Add DNS Record page](/downloads/workflow-automation/setup/managing-custom-email-domains/WA-Add-DNS-Record-PG-System-Verification-Inprogress-Copy-Icons_0.png)
[]![Viewing the Add DNS Record page after the verification process is successful. A message is displayed on the page stating that the domain was successfully verified and that you can proceed to the next step. ](/downloads/workflow-automation/setup/managing-custom-email-domains/WA-Add-DNS-Record-PG-Domain-Successfully-Verified_0.png)
[]![Viewing the Add DNS Record page after the verification process failed. A message is displayed on the page stating that the domain verification failed and instructing you to ensure DNS records were accurately entered in your DNS provider.](/downloads/workflow-automation/setup/managing-custom-email-domains/WA-Add-DNS-Record-PG-Domain-Verification-Failed_0.png)
[]![Viewing the Verify Custom Domain Setup page in the Custom Email Domain Setup wizard](/downloads/workflow-automation/setup/managing-custom-email-domains/WA-Verify-Custom-Domain-Setup-Page.png)
[]![Viewing a custom email domain that was successfully added on the Custom Email Domain page. This page contains the Add Domain button and the Revert to Zscaler button above a table with columns for Domain Name, Envelope Sender Domain, Originating Email Address, Last Updated, Status, and Action.](/downloads/workflow-automation/setup/managing-custom-email-domains/WA-Cust-Email-Domain-Page-After-Add_1.png)
[]![Viewing the Make Default icons on the Custom Email Domain page](/downloads/workflow-automation/setup/managing-custom-email-domains/WA-Cust-Email-Domain-Page-Make-Default-Icon_1.png)
[]![Custom Email Domain page displaying an expired custom email domain with the Regenerate icon highlighted.](/downloads/workflow-automation/setup/managing-custom-email-domains/WA-Cust-Email-Domain-Page-Expired-Status_0.png)
[]![Custom Email Domain page displaying the following message after you click Revert to Zscaler Domain on the Custom Email Domain page: Are you sure you want to revert back to zsworkflow.net as the originating email domain? This action will override your current settings.](/downloads/workflow-automation/setup/managing-custom-email-domains/WA-Cust-Email-Domain-Page-Revert-Zscaler-Domain_1.png)
[]![Custom Email Domain page displaying the Zscaler Domain in use button after you click Revert to Zscaler Domain.](/downloads/workflow-automation/setup/managing-custom-email-domains/WA-Cust-Email-Domain-Page-Zscaler-Domain-In-Use_1.png)
[]![Viewing all custom email domains on the Custom Email Domain page. This page contains the Add Domain button and Revert to Zscaler Domain button above a table with columns for Domain Name, Envelope Sender Domain, Originating Email Address, Last Updated, Status, and Action.](/downloads/workflow-automation/setup/managing-custom-email-domains/WA-Cust-Email-Domain-Page-View-All_2.png)
[]![Viewing the View buttons on the overview page in the Custom Email Domain Setup wizard](/downloads/workflow-automation/setup/managing-custom-email-domains/WA-Cust-Email-Domain-Setup-Wizard-View-Buttons_0.png)
[]![Viewing the Back button and the Next button on the Add DNS Record page in the Custom Email Domain Setup wizard](/downloads/workflow-automation/setup/managing-custom-email-domains/WA-Cust-Email-Domain-Setup-Wizard-Back-Next-Buttons_0.png)