# Sharing Defined Application Segments
Source: https://help.zscaler.com/unified/sharing-defined-application-segments
PDF: https://help.zscaler.com/pdf/com/en/1492116.pdf

Applications can be shared explicitly between Microtenants. The **Share** icon only appears if you are in a [Microtenant](/unified/about-microtenants).
To share a defined application segment to another Microtenant:
- Go to the **Defined Application Segments **page (Policies > Access Control > Private Applications > App Segments).
- In the table, locate the application segment you want to share and click the **Share** icon. The **Share with Microtenant** window appears.
- In the **Share with Microtenant** window:
- Review the application segment name to confirm it is the one you want to share.
- Select the Microtenant(s) from the drop-down menu that the application segment will be shared to. The Default tenant is not an option, as the Share option is also not shown in the Default tenant.
A hop in the transaction might occur in the following scenario when a user is connected to a Private Service Edge from a Microtenant and accesses the shared application from another Microtenant. For example:
- An application is served by an App Connector and is defined in Microtenant A.
- The same application is shared from Microtenant A to Microtenant B, which is assigned to a user.
- The user connects to the Private Service Edge from Microtenant B.
- The same user from Microtenant B accesses the application.
[See Image.](#share-with-microtenant)
- Click **Save**.
[]![The Share with Microtenant window on the Defined Application Segment page within the ZPA Admin Portal](/downloads/zpa/documentation-knowledgebase/policies/access-policy/configuring-access-policies/Share%20window%20updated_.png)