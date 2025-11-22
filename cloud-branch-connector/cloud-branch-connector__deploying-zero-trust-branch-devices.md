# Deploying Zero Trust SD-WAN Devices
Source: https://help.zscaler.com/cloud-branch-connector/deploying-zero-trust-branch-devices
PDF: https://help.zscaler.com/pdf/com/en/1468301.pdf

Enabled by the Zscaler Zero Trust Exchange (ZTE), Zero Trust Software-Defined Wide Area Network (SD-WAN) Devices are [Zscaler Branch Connector](/cloud-branch-connector/what-zscaler-branch-connector) hardware devices that use Zero Trust Branch Connectivity to simplify traffic forwarding to Zscaler services. To learn more, see [Understanding Zero Trust SD-WAN Devices](/cloud-branch-connector/understanding-zero-trust-branch-devices).
To deploy a Zero Trust SD-WAN Device:
- Upon receipt of the Zero Trust SD-WAN Device,[ install your hardware ](/cloud-branch-connector/installing-zero-trust-branch-devices)according to the instructions provided.
- After installing your device, log in to the [Zscaler Cloud & Branch Connector Admin Portal](/cloud-branch-connector/accessing-navigating-zscaler-cloud-branch-connector-admin-portal).
- Go to** Administration **> **ZT Devices**.
- On the [ZT Devices](/cloud-branch-connector/about-zt-devices) page, view your Zero Trust SD-WAN Device and copy the **Serial Number** to a secure location.
- Go to **Administration** > **Provisioning & Configuration **> **Branch Configuration**.
- On the [Branch Configuration Template ](/cloud-branch-connector/about-branch-configuration-templates)page, click **Add Branch Connector Configuration Template**.
- [Configure a Branch Configuration Template](/cloud-branch-connector/configuring-branch-provisioning-template) with the serial number of the Zero Trust SD-WAN Device.
- On the **Branch Configuration Template** page, under the **Status **column of the configuration template, change the status from** Staged **to** Ready to Deploy**.
-
In the **Status Update Confirmation** window, click **Update **to complete deployment. This process might take a few minutes.
The LED indicator light on the front of the Zero Trust SD-WAN Device shows the Zero Touch Provisioning (ZTP) status, as well as the status of the Zero Trust SD-WAN Device after it is deployed.
| Indicator State | Zero Trust Provisioning Status | Zero Trust SD-WAN Device Status |
| --------------- | ------------------------------ | ------------------------------- |
| Solid red | Initializing | Not operational (control and data tunnels are down) |
| Blinking red | ZTP is pending | N/A |
| Blinking green | ZTP is in progress | N/A |
| Solid green | All services are running | Normal operation (control and data tunnels are up) |
After deployment is complete, the status of the configuration template is **Deployed**.
After Zero Trust SD-WAN Devices are deployed, you can:
- View the deployment, location, and status of your deployment from the [Cloud & Branch Connector Monitoring ](/cloud-branch-connector/accessing-cloud-branch-connector-monitoring)page.
- Modify the Zero Trust SD-WAN Devices from the [Physical Branch Devices ](/cloud-branch-connector/about-physical-branch-devices)page.
- [Configure Traffic Forwarding Rules](/cloud-branch-connector/configuring-traffic-forwarding-rule).
- [Configure DNS Gateways](/cloud-branch-connector/configuring-dns-gateway).
If your Zero Trust SD-WAN Device is deployed in gateway mode, you can edit its configuration after deployment by clicking the edit icon on the [Branch Configuration Template](/cloud-branch-connector/about-branch-configuration-templates) page.
Zscaler Zero Trust SD-WAN devices contain a Zscaler Service Account called `zsroot`. This account is a privileged user that enables secure administrative access and management of the Zero Trust SD-WAN Device. In order to safeguard your organization, Zscaler strongly recommends implementing routine password rotation as a best practice.
- Log in to the device through the console/management interface as user `zsroot`.
- Change the password:
- Enter the following command:
passwd zsroot
- Follow the prompts to enter the current password and then enter a new password.