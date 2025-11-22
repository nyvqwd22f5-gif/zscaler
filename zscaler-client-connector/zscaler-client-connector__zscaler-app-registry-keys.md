# Zscaler Client Connector: Windows Registry Keys
Source: https://help.zscaler.com/zscaler-client-connector/zscaler-app-registry-keys
PDF: https://help.zscaler.com/pdf/com/en/1358826.pdf

You can navigate to Zscaler Client Connector registry keys by using the following path: `\HKEY_CURRENT_USER\Software\Zscaler\App`.
This table provides a list of possible values and their explanation for the registry key, `ZNW_State`**, **which represents Zscaler Client Connector's network state.
| Registry Key Values | Explanation |
| ------------------- | ----------- |
| TRUSTED_VPN | The machine is connected to a trusted full tunnel VPN. |
| NON_TRUSTED | The machine is connected to a non-trusted network. |
| TRUSTED | The machine is connected to a trusted network. |
This table provides a list of possible values and their explanation for the registry keys, `ZPA_State`** **and** **`ZWS_State`** **which represents ZPA service state and ZIA service state, respectively.
| Registry Key Values | Explanation |
| ------------------- | ----------- |
| OFF | Service is turned off. |
| ON | Service is turned on. |
| CONNECTING | Service is connecting. |
| NONE_FORWARDING | Service is in None Forwarding state. The traffic Interception is turned off. |
| TUNNEL_FORWARDING | Service is in Tunnel Forwarding state. Network drivers are being used to intercept traffic. |
| LOCAL_PROXY_FORWARDING | Service is in Local Proxy Forwarding state. PAC files are being used to intercept traffic. |
| ENFORCE_PROXY_FORWARDING | Service is in Enforce Proxy Forwarding state. A PAC file is being enforced on the system. |
| ADAPTER_DOWN_ERROR | Service is in Adapter Down Error state. Zscaler Client Connector is not able to find an adapter with a default route.This error may appear due to DHCP renewal. Run the "ipconfig /all" command and check for the lease obtained timestamp. Verify if the lease obtained timestamp coincides with the problem time.For example: Lease Obtained. . . . . . . . . . : Wednesday, 9 February 2022 2:59:42 |
| SERVICE_DOWN_ERROR | Service is in Service Down Error state. One of the microservices is not operational. |
| CAPTIVE_PORTAL_ERROR | Service is in Captive Down Error state. Captive portal has been detected on the system and the open timeout has expired. |
| SERVER_DOWN_ERROR | Service is in Server Down Error state. Zscaler Client Connector is not able to reach the ZIA Public Service Edge or ZPA Public Service Edge. |
| INTERNET_UNREACHABLE_ERROR | Service is in Internet Unreachable Error state. Network appears to be connected but ZPA is not able to resolve the broker name.This registry key value is applicable only for ZPA. |
| FIREWALL_BLOCK_ERROR | Service is in Firewall Block Error state. Zscaler Client Connector's attempt to create an outbound and/or inbound connection to itself failed. |
| SYSTEM_SOCKETS_EXHAUSTED_ERROR | Service is in Sockets Exhausted Error state. System's limit for maximum sockets has reached. |
| DRIVER_ERROR | Service is in Driver Error state. Zscaler Client Connector is not able to load the network driver (TAP/TUN/LWF). |
| CAPTIVE_PORTAL_FAILOPEN | Service is in Captive Portal FailOpen state. Zscaler Client Connector has detected a captive portal on the network and it has stopped traffic interception for some time to allow captive authentication. |
| PRE_ENROLMENT_PROXY_ENFORCEMENT | Service is in Local Captive Mode state. Strict enforcement has been configured and Zscaler Client Connector has blocked network access till the user logs in to Zscaler Client Connector. |
| SERVER_AUTH_ERROR | Service is in Server Auth Error state. ZIA Public Service Edge or ZPA Public Service Edge is not accepting the auth credentials sent by the client. |
| SERVER_AUTH_TERMINATED_AT_UNKNOWN | Service is in Chaining Authentication Error state. The realm of ZIA Public Service Edge or ZPA Public Service Edge and the logged-in user do not match. |
| ZPA_UNTRUSTED_SERVER_CERT_ERROR | Service is in ZPA Untrusted Server Error state. ZPA connection got an SSL exception while connecting.This registry key value is applicable only for ZPA. |
| ZPAAuth_STATE | Service is in disabled state. ZPA entitlement is removed. |