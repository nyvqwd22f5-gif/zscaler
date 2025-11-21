# Configuring Bypass Settings
Source: https://help.zscaler.com/zpa/configuring-bypass-settings
PDF: https://help.zscaler.com/pdf/com/en/1483516.pdf

There might be times when you want users to bypass ZPA and connect directly to specific applications. For example, you might want users to bypass ZPA for a specific application if they are connected directly to your trusted corporate network.
You can use the Bypass setting within an application segment for the following scenarios:
- [To bypass ZPA on the corporate network](#BypassZPACorpNet)
- [To bypass ZPA for certain applications](#BypassZPAApps)
The Bypass setting is applied at the domain level. When a user requests access to an application, ZPA evaluates the forwarding profile. If the forwarding profile specifies that the user must use ZPA, then ZPA checks the application's Bypass setting and allows the user to connect to the application accordingly.
To configure bypass settings for ZPA:
- In the Zscaler Client Connector Portal, [configure forwarding profiles](/z-app/configuring-forwarding-profiles-zscaler-app) for the Zscaler Client Connector so that it can recognize when users are on and off trusted corporate networks.
- In the ZPA Admin Portal, when [configuring the application segment](/zpa/about-application/onboard), select the appropriate option for the **Bypass **setting. You can select one of the following options:
- **Use Client Forwarding Policy**: This option is selected by default. If selected, the decision to forward a user’s application request to ZPA is defined by the [client forwarding policy](/zpa/about-client-forwarding-policy). If none of the policy rules apply, then access to the application is implicitly set to **Forward to ZPA**. To learn more, see [Configuring Client Forwarding Policies](/zpa/configuring-client-forwarding-policies). This is also the case if you do not define any client forwarding policy rules at all within the ZPA Admin Portal.
- **Always**: If selected, users can always bypass ZPA when accessing an application. Only choose this option if you've enabled [dynamic application discovery](/zpa/about-application-discovery) and you want users to access the defined application without ZPA.
- **On Corporate Network**: If selected, users can bypass ZPA when accessing an application from a trusted network. ZPA checks if the user is on a trusted network defined in the [Zscaler Client Connector forwarding profile](/z-app/configuring-forwarding-profiles-zscaler-app).
You can click **Clear Selection** to remove any selections.
- [Complete the application segment configuration.](/zpa/about-application/onboard)
[]In this scenario, your users are connected to your corporate network and you want them to bypass ZPA and connect directly to internal applications. In this case, for those applications, you would select** On Corporate Network **as your **Bypass** setting. If you want to allow users to bypass ZPA only on trusted networks, you must first have [configured forwarding profiles](/z-app/configuring-forwarding-profiles-zscaler-app) for the Zscaler Client Connector so that it can recognize when users are on and off those networks.
[]Perhaps you want to leverage ZPA's [application discovery](/zpa/about-application-discovery) feature and allow the service to discover web applications as users request them, for whatever network the users are on. However, there are is one application you never want to make accessible via ZPA.
In this scenario, you would define the following two application segments:
- General Web Apps
![Application segment window with Bypass field](/downloads/zpa/documentation-knowledgebase/applications/application-segments/configuring-bypass-settings/zpa-bypassexampleapp1_0.png)
ZPA can always discover these applications and connect users to them, for whatever network they're on.
- HR Web App
![zpa-bypassexampleapp2.png](/downloads/zpa/documentation-knowledgebase/applications/application-segments/configuring-bypass-settings/zpa-bypassexampleapp2.png)
Although users can access all applications that end in mockcompany.com with ZPA because of the General Web Apps configuration, because of the bypass configured here, they can never access the HR Web App with ZPA.