# Entering and Exiting Business Continuity
Source: https://help.zscaler.com/zpa/entering-and-exiting-business-continuity
PDF: https://help.zscaler.com/pdf/com/en/1507936.pdf

You can enter and exit Business Continuity after the [prerequisites](/zpa/understanding-business-continuity) are met.
The following workflows assume that the [Business Continuity Settings](/zpa/configuring-business-continuity-settings#controlChannelRecovery) are configured in the ZPA Admin Portal.
Entering Business Continuity
The following workflow for entering Business Continuity applies to App Connectors and ZPA Private Service Edges:
- [App Connectors and ZPA Private Service Edges](#ConnectorsPses)
- []When connectivity to the Zero Trust Exchange (ZTE) is lost, a timer is triggered based on the Max Time to Wait to Enter Business Continuity specified in the [Business Continuity Settings](/zpa/configuring-business-continuity-settings#controlChannelRecovery).
- App Connectors and ZPA Private Service Edges attempt to retry connections to the ZTE until the Max Time to Wait to Enter Business Continuity expires.
- After the timer expires, the App Connectors and ZPA Private Service Edges connect to the [Private Cloud Controller](/zpa/about-private-cloud-controllers) using the Business Continuity FQDNs. After successful connection to the Private Cloud Controller, App Connectors and ZPA Private Service Edges continue to reestablish the control channel to the ZPA cloud.
The workflow for Zscaler Client Connector to enter Business Continuity differs depending on if you are a new user enrolling in Business Continuity, or if you are an enrolled user that is already registered to the ZPA cloud.
- [New Users](#NewUsers)
- [Enrolled Users](#EnrolledUsers)
[]The following workflow applies to new users enrolling in Business Continuity after launching Zscaler Client Connector:
- Zscaler Client Connector attempts to reach the cloud authentication endpoint (samlsp.private.zscaler.com).
- If the authentication endpoint is not reachable, then Zscaler Client Connector contacts the local authentication endpoint and, after successful authentication, enters Business Continuity.
[]The following workflow applies for enrolled users who need to authenticate:
- Zscaler Client Connector attempts to reach the cloud authentication endpoint (samlsp.private.zscaler.com).
- If this is not reachable, then Zscaler Client Connector attempts to reach the local authentication endpoint hosted on the Private Cloud Controller.
- If the local authentication endpoint is reachable, then the user is redirected to the IdP and authenticates with the Business Continuity IdP.
- Zscaler Client Connector contacts the ZTE to get a list of ZPA Public Service Edges or ZPA Private Service Edges to connect to.
- Zscaler Client Connector establishes the control and data channel to the ZPA Public Service Edge or ZPA Private Service Edge.
- If the initial connection to the ZTE fails or the Zscaler Client Connector is not able to establish control and data channel with any ZPA Public Service Edge or ZPA Private Service Edge, then Zscaler Client Connector contacts the Business Continuity FQDN and gets redirected to the Business Continuity ZPA Private Service Edges.
The following workflow applies for users who are authenticated and actively connected to the ZPA Public Service Edge:
- If the connection is idle for 60 seconds, Zscaler Client Connector attempts to reconnect to the current ZPA Public Service Edge that the ZTE redirected the user to establish control and data channel.
- If the ZPA Public Service Edge is not reachable, then Zscaler Client Connector attempts to establish control and data channel with the next ZPA Public Service Edge or ZPA Private Service Edge in the redirect list. After two retries to each of the ZPA Public Service Edge or ZPA Private Service Edge, if Zscaler Client Connector cannot reach any of the ZPA Public Service Edges or ZPA Private Service Edge, then Zscaler Client Connector contacts the Private Cloud Controller using the Business Continuity FQDN.
- The Private Cloud Controller redirects users to the Business Continuity ZPA Private Service Edges.
Exiting Business Continuity
App Connectors and ZPA Private Service Edges exit Business Continuity and switch their control channels to the ZPA cloud immediately after connectivity to the ZPA cloud recovers.
A Remote Procedure Call (RPC) is sent by the ZPA Private Service Edge to move the users back to the ZTE. After the initial connection, the ZPA Private Service Edge waits for 10 minutes and starts to probe every minute to check if Zscaler Client Connector has active Microtunnels (M-Tunnels). The RPC is sent to Zscaler Client Connector to ask if it can move back to the ZTE in one of the following scenarios:
- There are no active M-Tunnels for a given user with the ZPA Private Service Edge.
-
The duration specified by the Max Time to Exit Business Continuity Mode expires. To learn more, see [Configuring Business Continuity Settings](/zpa/configuring-business-continuity-settings#controlChannelRecovery).
The timers for the duration specified in the Business Continuity Settings are unique to each user connection.
After receiving the RPC, Zscaler Client Connector checks the connectivity to the ZTE. If the ZTE is reachable, then Zscaler Client Connector ends the connection with the ZPA Private Service Edge and connects to the ZTE. If the ZTE is not reachable, Zscaler Client Connector continues to stay connected to the ZPA Private Service Edges and waits for the next RPC.