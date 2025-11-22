# Entering and Exiting Business Continuity
Source: https://help.zscaler.com/unified/entering-and-exiting-business-continuity
PDF: https://help.zscaler.com/pdf/com/en/1528651.pdf

You can enter and exit Business Continuity after the [prerequisites](/unified/understanding-business-continuity) are met.
The following workflows assume that the [Business Continuity Settings](/unified/configuring-business-continuity-settings#controlChannelRecovery) are configured in the Admin Portal.
Entering Business Continuity
The following workflow for entering Business Continuity applies to App Connectors and Private Service Edges for Private Applications:
- [App Connectors and Private Service Edges for Private Applications](#ConnectorsPses)
- []When connectivity to the Zero Trust Exchange (ZTE) is lost, a timer is triggered based on the Max Time to Wait to Enter Business Continuity specified in the [Business Continuity Settings](/unified/configuring-business-continuity-settings#controlChannelRecovery).
- App Connectors and Private Service Edges for Private Applications: attempt to retry connections to the ZTE until the Max Time to Wait to Enter Business Continuity expires.
- After the timer expires, the App Connectors and Private Service Edges for Private Applications: connect to the [Private Cloud Controller](/unified/about-private-cloud-controllers) using the Business Continuity FQDNs. After successful connection to the Private Cloud Controller, App Connectors and Private Service Edges for Private Applications: continue to reestablish the control channel to the cloud.
The workflow for Zscaler Client Connector to enter Business Continuity differs depending on if you are a new user enrolling in Business Continuity, or if you are an enrolled user that is already registered to the cloud.
- [New Users](#NewUsers)
- [Enrolled Users](#EnrolledUsers)
[]The following workflow applies to new users enrolling in Business Continuity after launching Zscaler Client Connector:
- Zscaler Client Connector attempts to reach the cloud authentication endpoint (samlsp.private.zscaler.com).
- If the authentication endpoint is not reachable, then Zscaler Client Connector contacts the local authentication endpoint and, after successful authentication, enters Business Continuity.
[]The following workflow applies for enrolled users who need to authenticate:
- Zscaler Client Connector attempts to reach the cloud authentication endpoint (samlsp.private.zscaler.com).
- If this is not reachable, then Zscaler Client Connector attempts to reach the local authentication endpoint hosted on the Private Cloud Controller.
- If the local authentication endpoint is reachable, then the user is redirected to the IdP and authenticates with the Business Continuity IdP.
- Zscaler Client Connector contacts the ZTE to get a list of Public Service Edges or Private Service Edges for Private Applications to connect to.
- Zscaler Client Connector establishes the control and data channel to the Public Service Edge or Private Service Edge for Private Applications.
- If the initial connection to the ZTE fails or the Zscaler Client Connector is not able to establish control and data channel with any Public Service Edge or Private Service Edge for Private Applications, then Zscaler Client Connector contacts the Business Continuity FQDN and gets redirected to the Business Continuity Private Service Edges for Private Applications.
The following workflow applies for users who are authenticated and actively connected to the Public Service Edge for Private Applications:
- If the connection is idle for 60 seconds, Zscaler Client Connector attempts to reconnect to the current Public Service Edge for Private Applications that the ZTE redirected the user to establish control and data channel.
- If the Public Service Edge for Private Applications is not reachable, then Zscaler Client Connector attempts to establish control and data channel with the next Public Service Edge or Private Service Edge for Private Applications in the redirect list. After two retries to each of the Public Service Edge or Private Service Edge for Private Applications, if Zscaler Client Connector cannot reach any of the Public Service Edges or Private Service Edge for Private Applications, then Zscaler Client Connector contacts the Private Cloud Controller using the Business Continuity FQDN.
- The Private Cloud Controller redirects users to the Business Continuity Private Service Edges for Private Applications.
Exiting Business Continuity
App Connectors and Private Service Edges for Private Applications exit Business Continuity and switch their control channels to the cloud immediately after connectivity to the cloud recovers.
A Remote Procedure Call (RPC) is sent by the Private Service Edge for Private Applications to move the users back to the ZTE. After the initial connection, the Private Service Edge for Private Applications waits for 10 minutes and starts to probe every minute to check if Zscaler Client Connector has active Microtunnels (M-Tunnels). The RPC is sent to Zscaler Client Connector to ask if it can move back to the ZTE in one of the following scenarios:
- There are no active M-Tunnels for a given user with the Private Service Edge for Private Applications.
-
The duration specified by the Max Time to Exit Business Continuity Mode expires. To learn more, see [Configuring Business Continuity Settings](/unified/configuring-business-continuity-settings#controlChannelRecovery).
The timers for the duration specified in the Business Continuity Settings are unique to each user connection.
After receiving the RPC, Zscaler Client Connector checks the connectivity to the ZTE. If the ZTE is reachable, then Zscaler Client Connector ends the connection with the Private Service Edge for Private Applications and connects to the ZTE. If the ZTE is not reachable, Zscaler Client Connector continues to stay connected to the Private Service Edges for Private Applications and waits for the next RPC.