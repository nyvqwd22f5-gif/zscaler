# Enforcing User-Based URL Policies on HTTPS Traffic
Source: https://help.zscaler.com/unified/enforcing-user-based-url-policies-https-traffic
PDF: https://help.zscaler.com/pdf/com/en/1493981.pdf

The Zscaler service can enforce user-based URL policies on HTTPS traffic in different ways.
Enable SSL Inspection
When SSL inspection is enabled, the Zscaler service decrypts SSL transactions and has full visibility of the HTTP traffic in the SSL tunnel (with URI and the Zscaler cookie representing the user), so it can enforce user policies. To learn more, see [About SSL Inspection](/unified/about-ssl-inspection).
If you use this option:
- The location must have authentication enabled.
- You should enable SSL inspection or the location or forward the location's traffic to Zscaler on port 9443.
Enable IP Surrogate
If enabling SSL interception is not a feasible option for your organization, you can use the [IP surrogate](/unified/about-surrogate-ip) feature, which enables the Zscaler service to map a user to a device IP address so it can apply the user's policies.