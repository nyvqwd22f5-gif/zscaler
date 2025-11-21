# Secure SaaS Access from Unmanaged Devices via User Portal
Source: https://help.zscaler.com/unified/secure-saas-access-unmanaged-devices-user-portal
PDF: https://help.zscaler.com/pdf/com/en/1500371.pdf

Organizations can provide access to sanctioned SaaS applications from unmanaged devices to enforce policies using the [isolation policies](/unified/about-isolation-policy) defined on Private Applications. The isolation containers that are created as a result of a Private Applications Isolation Policy can forward non-Private Applications defined application traffic and internet traffic generated to Internet & SaaS for further processing and enforcement of necessary policies.
[See image.](#diagram-flow)
Define a SaaS Application as a Private Applications Browser Access Application:
SaaS applications are typically accessed using an URL that has a domain that is not owned by your organization, such as zscaler70-dev-ed.lightning.force.com. Considering the admin does not own this domain, they need to define an application segment with an application using a placeholder domain as shown below.
In the above example, they have created an application segment by the name of “Isolated SaaS Application” and an application using an FQDN in a DNS namespace that they own, which is salesforce.safemarch.com. They are transforming the domain to zscaler70-dev-ed.lightning.force.com, which is the true FQDN used by the SaaS application that they intend to provide isolated access to. They have ensured that the application defined is configured for browser access. To learn more, see [About Browser Access](/unified/about-browser-access) and [Configuring Defined Application Segments](/unified/configuring-defined-application-segments).
[See image.](#Add-App-Segment)
Create an Isolation Policy
Once the application is defined with the necessary configurations, admins can define an isolation policy that isolates the application segment they just created. To learn more, see [About Isolation Policy](/unified/about-isolation-policy).
[See image.](#Add-Iso-Policy)
Ensure that the isolation profile selected while defining the isolation policy has the **Forward Internet Traffic via ZIA** option enabled under the **Company Settings** tab. If the option is not enabled, the SaaS application traffic generated from the isolated browser is not forwarded via Internet & SaaS and the traffic is not inspected, logged, and enforced with the policies defined on Internet & SaaS. To learn more, see [Creating Isolation Profiles for Private Applications](/unified/creating-isolation-profiles-private-applications).
[See image.](#FWD-Traffic-via-ZIA)
Test SaaS Application in Isolation
Try accessing the placeholder domain that was used to create the application segment from an unmanaged device using a browser, such as a device that does not have Zscaler Client Connector running. If the application is configured for browser access correctly, you are prompted to authenticate with your IDP, which is configured with Private Applications. Upon successful authentication, you are redirected to an isolation session and prompted to authenticate to Internet & SaaS. Upon successful authentication to Internet & SaaS, the isolated browser accesses the original SaaS application URL configured in the application segment that was created, and you can access the SaaS application from the isolated browser.
[See image.](#Test-SaaS-Apps)
Publish the SaaS Application on the User Portal
Zscaler provides you with the ability to create a portal called the [User Portal](/unified/about-user-portals) to be used as a catalog of applications published via the Private Applications Browser Access for users to access. Users can access the user portal URL and see the list of all published private and SaaS applications, via app tiles. To learn more, see [About User Portals](/unified/about-user-portals).
[See image.](#User-Portal)
[]![ZIA Over ZPA Diagram Flow](/downloads/isolation/profiles/zpa-profiles/secure-saas-access-unmanaged-devices-user-portal/ZIA-Over-ZPA-digram-flow.png)
[]![Add a new Application Segment in ZPA for Isolation SaaS Applications ](/downloads/isolation/profiles/zpa-profiles/secure-saas-access-unmanaged-devices-user-portal/Add-Application-Segment-Isolation-SaaS-Apps.png)
[]![Add an Isolation Policy.](/downloads/isolation/profiles/zpa-profiles/secure-saas-access-unmanaged-devices-user-portal/Add-Isolation-Policy.png)
[]![Enable to forward traffic via ZIA instead ZPA.](/downloads/isolation/profiles/zpa-profiles/secure-saas-access-unmanaged-devices-user-portal/Add-Isolation-Profile_traffic-forwarding.png)
[]![Test the SaaS applications in Isolation.](/downloads/isolation/profiles/zpa-profiles/secure-saas-access-unmanaged-devices-user-portal/test-saas-apps.png)
[]![Access the User Portal. ](/downloads/isolation/profiles/zpa-profiles/secure-saas-access-unmanaged-devices-user-portal/User-Portal.png)