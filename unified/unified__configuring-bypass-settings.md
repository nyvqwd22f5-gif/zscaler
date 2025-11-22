# Configuring Bypass Settings
Source: https://help.zscaler.com/unified/configuring-bypass-settings
PDF: https://help.zscaler.com/pdf/com/en/1492206.pdf

There might be times when you want users to bypass Private Applications and connect directly to specific applications. For example, you might want users to bypass Private Applications for a specific application if they are connected directly to your trusted corporate network.
You can use the Bypass setting within an application segment for the following scenarios:
- [To bypass Private Applications on the corporate network](#BypassZPACorpNet)
- [To bypass Private Applications for certain applications](#BypassZPAApps)
The Bypass setting is applied at the domain level. When a user requests access to an application, Private Applications evaluates the forwarding profile. If the forwarding profile specifies that the user must use Private Applications, then Private Applications check the application's Bypass setting and allows the user to connect to the application accordingly.
To configure bypass settings for Private Applications:
- [Configure forwarding profiles](/unified/configuring-forwarding-profiles-zscaler-client-connector) for the Zscaler Client Connector so that it can recognize when users are on and off trusted corporate networks.
- When [configuring the application segment](/unified/configuring-defined-application-segments), select the appropriate option for the **Bypass **setting. You can select one of the following options:
- **Use Client Forwarding Policy**: This option is selected by default. If selected, the decision to forward a user’s application request to Private Applications is defined by the [client forwarding policy](/unified/about-client-forwarding-policy). If none of the policy rules apply, then access to the application is implicitly set to **Forward to Private Applications**. To learn more, see [Configuring Client Forwarding Policies](/unified/configuring-client-forwarding-policies). This is also the case if you do not define any client forwarding policy rules at all within the Admin Portal.
- **Always**: If selected, users can always bypass Private Applications when accessing an application. Only choose this option if you've enabled [dynamic application discovery](/unified/about-application-discovery) and you want users to access the defined application without Private Applications.
- **On Corporate Network**: If selected, users can bypass Private Applications when accessing an application from a trusted network. Private Applications checks if the user is on a trusted network defined in the [Zscaler Client Connector forwarding profile](/unified/configuring-forwarding-profiles-zscaler-client-connector).
You can click **Clear Selection** to remove any selections.
- [Complete the application segment configuration.](/unified/configuring-defined-application-segments)
[]In this scenario, your users are connected to your corporate network and you want them to bypass Private Applications and connect directly to internal applications. In this case, for those applications, you would select** On Corporate Network **as your **Bypass** setting. If you want to allow users to bypass Private Applications only on trusted networks, you must first have [configured forwarding profiles](/unified/configuring-forwarding-profiles-zscaler-client-connector) for the Zscaler Client Connector so that it can recognize when users are on and off those networks.
[]Perhaps you want to leverage Private Applications's [application discovery](/unified/about-application-discovery) feature and allow the service to discover web applications as users request them, for whatever network the users are on. However, there is one application you never want to make accessible via Private Applications.
In this scenario, you would define the following two application segments on the Application Segments page (Policies > Private Applications > App Segments):
- General Web Apps
![Application segment window with Bypass field](/downloads/zpa/documentation-knowledgebase/applications/application-segments/configuring-bypass-settings/zpa-bypassexampleapp1_0.png)
Private Applications can always discover these applications and connect users to them, for whatever network they're on.
- HR Web App
![zpa-bypassexampleapp2.png](/downloads/zpa/documentation-knowledgebase/applications/application-segments/configuring-bypass-settings/zpa-bypassexampleapp2.png)
Although users can access all applications that end in mockcompany.com with Private Applications because of the General Web Apps configuration, because of the bypass configured here, they can never access the HR Web App with Private Applications.