# Domains to Add to SSL Bypass List
Source: https://help.zscaler.com/zscaler-client-connector/domains-add-ssl-bypass-list
PDF: https://help.zscaler.com/pdf/com/en/1285526.pdf

To ensure Zscaler Client Connector properly processes traffic for Zscaler Private Access (ZPA), all domains for Zscaler Client Connector enrollment and authentication that are listed on [config.zscaler.com/private.zscaler.com/zpa](http://config.zscaler.com/private.zscaler.com/zpa) must be in your SSL bypass list. Also, be sure to include any domains used by your organization's identity provider (IdP).
If you are using Okta as your organization's IdP, you must also include Okta-specific domains in your SSL bypass list. To learn more, see the [Okta documentation](https://help.okta.com/en-us/content/topics/security/ip-address-allow-listing.htm%20).