# Supporting Reauthentication into ZPA via Microsoft IWA with Kerberos
Source: https://help.zscaler.com/zpa/supporting-reauthentication-zpa-microsoft-iwa-kerberos
PDF: https://help.zscaler.com/pdf/com/en/1484206.pdf

In order to support reauthentication for application access into ZPA when single sign-on (SSO) is set up using Microsoft Integrated Windows Authentication (IWA) with Kerberos, you must complete the following procedure:
If you do not set up an application segment with an associated timeout access policy rule as detailed in the steps below, an error message will display in Zscaler Client Connector whenever your users attempt to reauthenticate. [See image.](#ZApp_Error)
If you need to use fully qualified domain names (FQDNs) you must create an application segment for each domain.
- Go to **Resource Management** > **Application Management** > **Application Segments **> **Defined Application Segments**.
- Click **Add Application Segment**.
The **Add Application Segment** window appears.
- In the **Add Application Segment** window, under **1. Define Applications, **enter the FQDN for ADFS and TCP port 443.
- For **Bypass**, select **On Corporate Network**.
[See image](#ReauthBypass_adfs_appseg)
- Click **Next**.
- Under **2. Segment Group**, select the proper segment group to add this application segment to or create a new segment group. To learn more, see [Configuring Application Segments](/zpa/about-application/onboard#tab2).
- Complete the configuration as detailed in [Configuring Application Segments](/zpa/about-application/onboard).
- After saving the previous application segment, click **Add Application Segment** again.
- Under **1. Define ****Applications**, enter the FQDN for LDAP/Active Directory (AD) using TCP and UDP ports 389, 636, and 3268-3269.
- For **Bypass**, select **On Corporate Network**.
[See image](#ReauthBypass_AppSeg)
- Click **Next**.
- Under **2. Segment Group**, select the proper segment group to add this application segment to or create a new segment group. To learn more, see [Configuring Application Segments](/zpa/about-application/onboard).
- Complete the configuration as detailed in [Configuring Application Segments](/zpa/about-application/onboard).
- After saving the previous application segment, click **Add Application Segment** again.
- Under **1. Define ****Applications**, enter the FQDN for KDC using TCP and UDP port 88.
- For **Bypass**, select **On Corporate Network**.
[See image.](#ReauthBypass_kdc_appseg)
- Click **Next**.
- Under **2. Segment Group**, select the proper segment group to add this application segment to or create a new segment group. To learn more, see [Configuring Application Segments](/zpa/about-application/onboard).
- Go to **Policy **> **Timeout Policy**
- Click **Add Rule**.
The **Add Timeout Policy** window appears.
- In the **Add Timeout Policy** window,
- For **Authentication Timeout**, select **Never**.
- For **Segment Groups**, select the groups you chose previously.
[See image.](#TimeoutPolicy_Never)
- Complete the configuration as detailed in [Configuring Timeout Policies](/zpa/about-reauthPolicy/new).
[]![zpa-zapperror-iwareauthfail.png](/downloads/zpa/documentation-knowledgebase/knowledge-base/supporting-reauthentication-zpa-microsoft-iwa-kerberos/zpa-zapperror-iwareauthfail.png)
[]![Example for how to enter the FQDN for LDAP/Active Directory using TCP and UDP ports 389, 636, and 3268-3269](/downloads/zpa/documentation-knowledgebase/application-management/enterprise-application-configurations/supporting-reauthentication-zpa-microsoft-iwa-kerberos/zpa-kerberos-ldap_0.png)
[]![Add Timeout Policy window within the ZPA Admin Portal](/downloads/zpa/documentation-knowledgebase/knowledge-base/supporting-reauthentication-zpa-microsoft-iwa-kerberos/zpa-timeoutpolicy-iwa_0.png)
[![Example for entering the FQDN for ADFS and TCP port 443](/downloads/zpa/documentation-knowledgebase/application-management/enterprise-application-configurations/supporting-reauthentication-zpa-microsoft-iwa-kerberos/zpa-kerberos-adfs.png)
]
[ ]
![Example of how to enter the FQDN for KDC using TCP and UDP ports 88](/downloads/zpa/documentation-knowledgebase/application-management/enterprise-application-configurations/supporting-reauthentication-zpa-microsoft-iwa-kerberos/zpa-kerberos-kdc.png)
[ ]
[ ]