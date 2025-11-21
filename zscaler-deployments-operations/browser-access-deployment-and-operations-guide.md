# Browser Access Deployment and Operations Guide
Source: https://help.zscaler.com/zscaler-deployments-operations/browser-access-deployment-and-operations-guide
PDF: https://help.zscaler.com/pdf/com/en/1420976.pdf

This guide describes the benefits of using Browser Access and the steps necessary for configuring Zscaler Private Access (ZPA) to add Browser Access to your security posture. Browser Access leverages a web browser for user authentication and application access over ZPA without Zscaler Client Connector.
To learn more, see [About Browser Access](/zpa/about-browser-access).
Value of Deploying Browser Access
Enabling Browser Access for ZPA provides the following benefits:
- Allows you to include devices without Zscaler Client Connector installed. For example, you might want to:
- Control user access to applications on devices with operating systems currently unsupported by Zscaler Client Connector.
- Provide third-party access to applications on devices that aren’t owned or managed by your company (e.g., a contractor or partner).
- Makes applications accessible for users from any web browser without Zscaler Client Connector or browser plugins and configurations.
- Uses your existing identity provider (IdP) to provide access to your current users, contractors, and other third-party users without managing an internet footprint.
Deployment Phase
The deployment phase includes initially setting up and integrating Zscaler solutions into an existing network infrastructure. During the deployment phase, you configure Browser Control to meet the needs of your infrastructure. The following sections discuss steps to deploy Browser Control.
Prerequisites
For Browser Access deployment, observe the following prerequisites:
- Browser Access might require an additional license for your organization. Check with your Zscaler Account team to verify the necessary licensing requirements.
- Ensure that application servers support Transport Layer Security (TLS) 1.2 encryption.
- Any user, contractor, or third party using Browser Access must be [provisioned in the ZPA IdP](/zpa/configuring-idp-single-sign).
Deployment Steps
The following steps explain how to deploy Browser Access:
- ZPA uses web server certificates to provide access to Browser Access. You get a certificate by:
- Uploading an [existing web server certificate](/zpa/about-uploadingBrowserAccessCertificate#UploadNotPending).
- [Creating a certificate signing request (CSR)](/zpa/about-creatingBrowserAccessCsr) for a web server certificate and [uploading the signed certificate](/zpa/uploading-web-server-certificates#UploadPending).
- Define a Browser Access application by creating an application segment or [editing an existing application segment](/zpa/defining-browser-access-application-within-existing-application-segment).
- (Optional) Define a Browser Access application with [multiple ports on the same domain](/zpa/defining-browser-access-application-multiple-ports-same-domain).
- (Optional) Define a Browser Access application with [different external and internal domains](/zpa/defining-browser-access-application-different-external-vs-internal-domains).
- (Optional) Enable [cross-origin resource sharing (CORS) requests](/zpa/configuring-authentication-settings).
- (Optional) Enable [SameSite Cookie Attribution](/zpa/configuring-authentication-settings).
Considerations
Review the following considerations:
- If you intend to use a different external and internal hostname for an application that has browser access enabled within an application segment:
- Internal hostnames are not exposed, so there is no record of internal hostnames on the public DNS.
- Backend Secure Sockets Layer (SSL) cannot be verified, so a web server certificate error is displayed to your end users because the hostname of the application doesn't match the certificate's hostname.
- If you intend to use the same external and internal hostname for an application that has browser access enabled within an application segment:
- Internal hostnames are exposed on the public DNS.
- Backend SSL can be verified, so end users don’t receive a web server certificate error.
- Browser Access cookies are session-based and are cleared when a web browser's session terminates. Users must authenticate before accessing applications via Browser Access. In addition, users are asked to reauthenticate periodically based on the Authentication Timeout setting of the ZPA timeout policy rule. To learn more, see [Configuring Timeout Policies](/zpa/about-reauthPolicy/new).
- To learn if specific browsers support CORS requests, see [About Browser Access](/zpa/about-browser-access).
- Browser Access only accesses web-based applications. You can leverage [Privileged Remote Access](/zpa/about-privileged-portals) to reach applications on protocols other than HTTP/HTTPS.
Operations Phase
This section describes standard practices used to operate Zscaler solutions when integrated with your environment. You can monitor and tune Browser Access during operations to meet your infrastructure needs.
Prerequisites
Document which applications correlate to which application segments for Browser Access operations.
Common Troubleshooting Items
You might receive a `403 Forbidden` error if the application fails to load a domain with CORS headers enabled. To support CORS and same-site requests from the applications configured for Browser Access, follow the instructions in [Configuring Authentication Settings](/zpa/configuring-authentication-settings).
To learn more, see [Understanding Browser Access Error Codes](/zpa/understanding-browser-access-error-codes).
Deployment Checklist
Zscaler recommends downloading the [Browser Access Deployment and Operations Checklist](/downloads/zscaler-deployments-operations/zpa-deployments-operations/browser-access-deployment-and-operations-guide/Browser-Access-Deployment-Operations-Checklist.pdf) to help plan and implement Browser Access on ZPA: [Download PDF](/downloads/zscaler-deployments-operations/zpa-deployments-operations/browser-access-deployment-and-operations-guide/Browser-Access-Deployment-Operations-Checklist.pdf)
Additional Information
For more information and troubleshooting instructions regarding Browser Access, see the [Zscaler Support Portal](https://zscaler.my.site.com/customers/s/) and the [Zscaler Zenith Community](http://community.zscaler.com).