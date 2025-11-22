# About the Index Tool
Source: https://help.zscaler.com/unified/about-index-tool
PDF: https://help.zscaler.com/pdf/com/en/1492946.pdf

The Index Tool allows you to configure index templates that can be applied when creating custom Data Loss Prevention (DLP) dictionaries and engines for the Zscaler service.
After an [Index Tool Configuration](/unified/adding-index-tool-configuration) is created and the virtual machine (VM) for the tool is installed and running, you can then log in to the tool to create and modify [Exact Data Match (EDM)](/unified/creating-exact-data-match-template) or [Indexed Document Match (IDM)](/unified/creating-indexed-document-match-template) index templates for DLP. The Index Tool also provides a dashboard view of your EDM and IDM index templates, including template details, the date and time when the template was last modified, and the template's status. You can configure single sign-on (SSO) for the Index Tool. To learn more, see [Configuring Single Sign-On for the Index Tool](/unified/configuring-single-sign-index-tool).
The Zscaler Index Tool provides the following benefits and allows you to:
- Create and modify EDM and IDM index templates.
- See a dashboard view of your EDM and IDM index templates.
- Host the Index Tool VM on an AWS EC2 instance, on an Azure VM, or on-premises.
To ensure you have access to the latest features, the Zscaler service automatically updates the Index Tool. You are notified in the Index Tool when an upgrade takes place and you can't change the upgrade time. However, the upgrade process waits for all system operations to complete before it begins. During the upgrade, which takes approximately one hour, the tool is not available for use.
To learn more, see [About Exact Data Match](/unified/about-exact-data-match) and [About Indexed Document Match](/unified/about-indexed-document-match).
About the Index Tool Page
On the Index Tool page (Policies > Data Protection > Common Resources > Index Tool), you can do the following:
- [Add an Index Tool Configuration](/unified/adding-index-tool-configuration).
- Download the VM (.ova) for the Index Tool.
- Search for an Index Tool configuration.
- View a list of all Index Tool configurations for your organization. For each Index Tool, you can see the following:
- **VM Name**: The name of the VM.
- **Status**: Displays whether the configuration is enabled or disabled.
- **SSL Certificate**: Displays a link that allows you to download the SSL client certificate used by the VM.
- [Edit an Index Tool Configuration](/unified/modifying-index-tool-configuration), including the ability to delete a configuration.
- [Modify the table and its columns](/unified/using-tables).
![Viewing and managing Zscaler Index Tool Configurations, including tool virtual machine (VM) and SSL certificate download links, within the Zscaler Internet Access (ZIA) Admin Portal](/downloads/zia/policies/data-loss-prevention/about-index-tool/ZIA-About-Index-Tool.png)