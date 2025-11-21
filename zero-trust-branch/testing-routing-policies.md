# Testing Routing Policies
Source: https://help.zscaler.com/zero-trust-branch/testing-routing-policies
PDF: https://help.zscaler.com/pdf/com/en/1532643.pdf

You can test [routing policies](/tech-pubs-drafts/understanding-routing-policies) to verify that network traffic is correctly routed through the intended interfaces in your Zero Trust Branch configuration. This helps ensure that the routing logic you defined is functioning as expected.
To test a routing policy:
- Log in to the branch appliance over SSH using the corresponding management IP address and credentials.
- Choose a source device (e.g., a virtual machine) to which the policy applies and ping an IP address (e.g., 8.8.8.8).
-
While the ping test is in progress, run the following command to capture packets on both primary and secondary interfaces:
`sudo tcpdump -i <interface_link_name> icmp `
- Verify the output, which should reflect the [policy configuration](/tech-pubs-drafts/configuring-routing-policies).