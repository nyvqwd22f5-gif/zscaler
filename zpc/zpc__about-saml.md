# About SAML
Source: https://help.zscaler.com/zpc/about-saml
PDF: https://help.zscaler.com/pdf/com/en/1392511.pdf

Zscaler Posture Control (ZPC) supports Security Assertion Markup Language (SAML) 2.0 for provisioning and authenticating users. SAML is an XML-based structure that is used to organize users’ security and identity information and to distribute this information across the organization’s tenants. It enables the following entities to exchange identity, authentication, attribute, and authorization information:
- A principal, which is a user who is trying to access a service or application online.
- A SAML authority, also referred to as the identity provider (IdP), authenticates the user.
- A relying party, which is the service provider (SP) that relies on the IdP to authenticate the user before it allows access to the service or application.
SAML provides for a federated identity wherein partner services use the same identifier to refer to a user. It also enables Single Sign-On (SSO), so users can authenticate only once to an IdP and then access various services. To learn how to configure SAML for your organization, see [Configuring SAML for SSO](/zpc/configuring-saml-sso).
SAML achieves this through a collection of assertions, protocols, bindings, and profiles:
- **Assertions**: A SAML authority creates statements regarding any of the following information:
- The authentication of a subject
- A subject’s attribute information
- Data of a subject in regard to a specific resource
- **Protocols**: Request/response protocols allow the SPs to:
- Request one or more assertions from a SAML authority
- Request an IdP’s authentication for a principal and return the corresponding assertion
- Request the registration of a name identifier
- Request the termination of an identifier’s use
- Receive a protocol message requested by means of an artifact
- Request a single logout for a collection of related sessions
- Request mapping of a name identifier
- **Bindings**: A binding defines how the SAML protocol messages are sent over transport and messaging protocols. ZPC supports the HTTP Post Binding, which defines how SAML protocol messages can be transported within the base 64-encoded content of an HTML form control.
- **Profiles**: A profile defines the assertions, protocols, and bindings used for specific use cases.
To learn more about SAML, see [OASIS Security Services (SAML) TC](https://www.oasis-open.org/committees/tc_home.php?wg_abbrev=security).
Service Provider-Initiated SAML
The most common deployment is the SP-initiated SAML deployment where the user tries to access ZPC, which then sends a SAML request to the IdP. The IdP validates the user's credentials, gets the user attributes like role name, and returns the SAML response assertion to ZPC through the user's browser.
- A user opens a browser and tries to access ZPC.
- ZPC generates a SAML authentication request, which is encoded and embedded into the URL for the IdP. The request is sent to the IdP by the user's browser redirection.
- The IdP does the following:
- Decodes the SAML request.
- Extracts the URL from ZPC's Assertion Customer Service (ACS).
- Authenticates the user with login credentials or by checking for an active session.
The IdP generates a SAML response with digitally signed public/private DSA/RSA keys, encodes it and sends it to ZPC's ACS URL.
- ZPC's ACS uses the IdP's public key to verify the response.
- After ZPC successfully verifies the response, it logs in the user and redirects the user's browser to the ZPC Admin Portal.
Identity Provider-Initiated SAML
In IdP-initiated SAML, a user can log in directly from an Identity Provider's portal by clicking on the ZPC application icon. When the user clicks the ZPC application icon, the IdP generates a SAML response and sends it to ZPC's ACS URL.
SAML JIT Provisioning
You can enable SAML just-in-time (JIT) provisioning to allow ZPC to automatically retrieve information related to users such as first name, or role name from the SAML response. If the user doesn't exist in the database, then the user is added to the database along with the role information. This new user is activated, and can access the ZPC Admin Portal. To learn how to configure SAML JIT provisioning, see [Configuring SAML for SSO](/zpc/configuring-saml-sso).