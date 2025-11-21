# Source IP Anchoring Configuration Guide for Office 365 Conditional Access
Source: https://help.zscaler.com/unified/source-ip-anchoring-configuration-guide-office-365-conditional-access
PDF: https://help.zscaler.com/pdf/com/en/1497711.pdf

[Source IP Anchoring](/unified/understanding-source-ip-anchoring) addresses one of the most common Office 365 use cases where users of an organization need to be given conditional access to the Office 365 applications. An admin can configure users to access Office365 applications only if their traffic originates from a trusted location, such as a corporate network. In such cases, users have to provide multi-factor authentication. The admin can also block user traffic originating from a non-corporate location, such as a coffee shop. You can use Source IP Anchoring to associate the traffic from a trusted location.
To enable conditional access, it is sufficient to configure Source IP Anchoring only for the initial user login/authentication traffic that is redirected to Azure AD domain (login.microsoftonline.com, login.windows.net, login.microsoft.com). After successful authentication, the subsequent application traffic uses an authenticated token to access the actual application and hence does not require to be redirected through Source IP Anchoring.
Configuring Source IP Anchoring for Office 365 Conditional Access
To enable and configure Source IP Anchoring for Office 365 Conditional Access:
- Complete the following steps to do the initial setup in the Admin Portal if you are using Private Applications solely for Source IP Anchoring. You can skip this step if you have already done the initial setup in the Admin Portal.
- []Update your [company](/unified/configuring-company-profile) and [administrator](/unified/about-administrators) information.
-
[]Configure the [enrollment certificates](/unified/about-enrollment-ca-certificates) for the App Connectors.
For Source IP Anchoring, it is sufficient if you configure the enrollment certificates only for the App Connectors.
- []Configure your [App Connectors](/unified/configuring-app-connectors).
- Configure the following items in the Admin Portal:
- Create an application segment for Office 365 and enable the **Source IP Anchor** option while configuring the application segment. To learn more, see [Configuring Application Segments.](/unified/configuring-defined-application-segments)
- Under the **Applications** section, enter **login.microsoftonline.com**. Alternatively, you can use **login.windows.net **or **login.microsoft.com**.
- In the **TCP Port Ranges** field, add 80 and 443 to allow the ports.
[See image.](#app-segment)
- Configure a segment group and a server group for the Office 365 application segment. Ensure that your server group is associated to the connector group that you configured earlier.
[See image](#segment-server-group)
- Configure a client forwarding policy for the Office 365 application segment. To learn more, see [Configuring Client Forwarding Policies.](/unified/configuring-client-forwarding-policies)
Ensure that you select the **Rule Action** as **Only Forward Allowed Applications** in the client forwarding policy for the Office 365 application segment.
[See image.](#client-forwarding-policy)
- Create and configure an access policy for the Office 365 application segment. To learn more, see [Configuring Access Policies.](/unified/configuring-access-policies)
Ensure that you allow access only to the client type, **ZIA Service Edge** in the access policy for the application segment.
[See image.](#access-policy)
- Configure the following items in the Admin Portal:
- Configure the ZPA gateway for the Office 365 application segment. To learn more, see [Configuring ZPA Gateway.](/unified/configuring-zpa-gateway)
Ensure that you select the Server Group that you created for the Office365 application segment in the Admin Portal.
[See image.](#zpa-gw)
- Configure the forwarding policies to forward the Office 365 application traffic to Private Applications. To learn more, see [Configuring Forwarding Policies for ZPA.](/unified/configuring-forwarding-policy#source-ip-anchoring)
- Under the **Forwarding Rule** section, select **ZPA** as the **Forwarding Method**.
[See image.](#fwd-method)
- Under the **General** tab, select the required trust criteria, such as location, users etc.
- Under the **Destination** tab, select the Office 365 application segment that you created in the Admin Portal from the **Application Segment** drop-down menu.
[See image.](#fwd-gw)
- Select the ZPA gateway that you created in the previous step from the **Forward to ZPA Gateway** drop-down menu.
[]![Screenshot of Add ZPA Application Segment for Office 365](/downloads/zia/documentation-knowledgebase/policies/configuring-source-ip-anchoring/zpa-app-segment-sipa.png)
[]![Screenshot of ZPA Segment group and Server Group Configuration](/downloads/zia/policies/forwarding-control/source-ip-anchoring/configuring-source-ip-anchoring-office-365/zpa-segment-group-server-group-sipa.png)
[]![Screenshot of ZPA Client Forwarding Policy Configuration](/downloads/zia/policies/forwarding-control/source-ip-anchoring/configuring-source-ip-anchoring-office-365/zpa-o365-client-forwarding-policy-sipa.png)
[]![Screenshot of ZPA Access Policy Configuration](/downloads/zia/policies/forwarding-control/source-ip-anchoring/configuring-source-ip-anchoring-office-365/zpa-access-policy-sipa.png?1620637078)
[]![Screenshot of Add ZPA Gateway](/downloads/zia/policies/forwarding-control/source-ip-anchoring/source-ip-anchoring-config-guide-office-365/zia-zpa-gateway.png)
[]![Screenshot of Add Forwarding Rule with ZPA Forwarding Method](/downloads/zia/policies/forwarding-control/source-ip-anchoring/source-ip-anchoring-config-guide-office-365/zia-add-fwding-rule-fwding-method.png)
[]![Screenshot of Add Forwarding Rule to Select Forwarding Gateway ](/downloads/zia/policies/forwarding-control/source-ip-anchoring/source-ip-anchoring-config-guide-office-365/zia-add-fwding-rule-fwding-gateway.png)