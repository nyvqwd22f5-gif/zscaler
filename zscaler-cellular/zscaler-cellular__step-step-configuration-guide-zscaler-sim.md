# Step-by-Step Configuration Guide for Zscaler SIMs
Source: https://help.zscaler.com/zscaler-cellular/step-step-configuration-guide-zscaler-sim
PDF: https://help.zscaler.com/pdf/com/en/1519076.pdf

This guide takes you through the configuration steps you need to complete to begin using Zscaler SIMs for your organization. Each step guides you through essential tasks, ensuring that you are fully equipped to secure and monitor your IoT and mobile devices. Before you begin configuring Zscaler SIMs, Zscaler recommends reading the following articles to learn more about Zscaler Cellular:
- [What Is Zscaler Cellular?](/zscaler-cellular/what-zscaler-cellular)
- [Understanding the Zscaler Cellular Architecture](/zscaler-cellular/understanding-zscaler-cellular-architecture)
- [Accessing and Navigating the Zscaler Cellular Edge Admin Portal](/zscaler-cellular/accessing-and-navigating-zscaler-cellular-admin-portal)
Configuring Zscaler SIMs
- [Step 1: Set Up Your Account](#set-up-account)
- [Step 2: Configure Credentials for Cellular Edge Deployment](#configure-crendentials)
- [Step 3: Deploy Cellular Edges](#deploy-cell-edges)
- [Step 4: Configure Polices](#configure-policies)
- [Step 5: Deploy Zscaler SIMs](#deploy-sims)
- [Step 6: Monitor SIM Usage](#monitor-sim-usage)
[]After Zscaler SIM service is enabled for your organization, a tenant is provisioned in Zscaler Internet Access (ZIA), Zscaler Private Access (ZPA), Cloud & Branch Connector, Zscaler Cellular, and ZIdentity. You can access the Zscaler Cellular Admin Portal via ZIdentity. Zscaler sends you an email with details such as the URL to access and set up ZIdentity. To learn more, see [Step-by-Step Configuration Guide for ZIdentity](/zidentity/setting-your-zscaler-account).
After completing the setup, log in to the Zscaler Cellular Admin Portal.
[]Before you can set up Zscaler SIMs, you must go to the Zscaler Cellular Admin Portal and enter the credentials for the Cloud & Branch Connector Admin Portal. To learn how to obtain and configure credentials, see [Configuring and Updating Credentials for Cellular Edge Deployment](/zscaler-cellular/configuring-and-updating-credentials-cell-edge-deployment).
[]Based on your subscriptions, deploy Cellular Edges in your preferred regions. To learn how to request Cellular Edge deployment, see [Deploying New Cellular Edges](/zscaler-cellular/deploying-new-cell-edges).
After this request, Zscaler starts deploying and setting up the necessary hardware and software systems to enable egress points for your IoT and mobile devices.
[]After successful deployment of Cellular Edges, configure necessary policies in the ZIA Admin Portal, the ZPA Admin Portal, or the Cloud & Branch Connector Admin Portal as required using parameters relating to mobile and IoT devices. The Cellular Edge appears as a location in ZIA. If you have different types of locations or devices, you can configure it with sublocations.
[]Insert the Zscaler SIMs supplied to you into your mobile or IoT devices. The Zscaler SIMs automatically connect with the Zscaler cloud.
[]In the Zscaler Cellular Admin Portal, monitor the devices and data usage to gather insights into the cellular traffic.
To learn more, see:
- [Understanding the Zscaler Cellular Dashboard](/zscaler-cellular/understanding-zscaler-cellular-dashboard)
- [About SIMs](/zscaler-cellular/about-sims)
- [About Network Events](/zscaler-cellular/about-network-events)