# Configuring the Zscaler SecOps Platform Gateway
Source: https://help.zscaler.com/uvm/configuring-zscaler-secops-platform-gateway
PDF: https://help.zscaler.com/pdf/com/en/1528011.pdf

The Zscaler Security Operations (SecOps) platform supports connecting on-premises outegrations and data sources through the Zscaler gateway at the account level, allowing for seamless onboarding of customers with on-premises installations for their vendors. In this guide, the resource you intend to connect is referred to as the on-premises service. This objective is to make the on-premises service accessible through the SecOps platform. The guide outlines a recommended setup using a virtual machine (VM).
The SecOps gateway setup process begins with creating a VM and generating a public SSH key. You then share the public key along with the VM's public IP address and gateway IP addresses with Zscaler. Using this information, Zscaler creates a representative VM instance and notifies you when the setup is complete. You then establish a reverse SSH tunnel and inform Zscaler. Upon confirmation, Zscaler completes the gateway configuration and notifies you. At this point, the Zscaler gateway is fully operational and ready for use.
![architecture of the zscaler gateway configuration](/downloads/uvm/account-management/account-settings/avalor-gateway-internal/zscaler%20gateway%20architecture.png)
You should receive this guide and the zscaler-gateway.sh script file after communication with Zscaler Support. If you have not received the script, contact your Zscaler Account team for assistance with setting up a gateway for your account.
Using the Zscaler Gateway
The Zscaler gateway is used in one of the following configuration processes:
- When [creating a data source](/uvm/creating-data-sources), select the relevant gateway in the Retrieval section of the source setup page.
- When [configuring the Jira outegration](/uvm/configuring-jira-outegration), select the relevant gateway in the Details section.
Prerequisites
For this setup, you must create or use a VM dedicated to running a reverse SSH tunnel. Do not use your local computer.
Ensure that you have the following requirements for the VM:
-
Connectivity:** **Deploy the instance in a private subnet with a dedicated virtual network interface (vNIC) for secure communication within the private network.
Ensure that the on-premises service is accessible from the VM you intend to use. It is crucial to test this connectivity before proceeding.
- Operating System:** **Your VM should be set up with one of the supported Linux** **distributions:
- Ubuntu
- Red Hat Enterprise Linux (RHEL)
- Centos
- Amazon-Linux
- Instance Specification:
- Use small instance types with at least 2 vCPUs and 4 GB of RAM.
- The instance size should be flexible and might vary based on traffic patterns. Ensure the chosen instance type supports scalability (both vertical and horizontal scaling) to handle workload fluctuations.
- Select instance resources based on expected traffic volume, with the ability to adjust instance sizing dynamically depending on actual usage.
- Network Configuration: The VM must be configured to listen on port 22 for incoming SSH connections.
Configuring the Zscaler Gateway
This guide accompanies the zscaler-gateway.sh script. The script first checks for an existing SSH key pair. If none are found, it creates one and displays the public key for you to send to Zscaler. Next, it verifies whether autossh is installed and attempts to install it if necessary. Finally, the script configures a service to establish the reverse SSH tunnel.
- [Step 1: Generate SSH Key Pair](#step1)
- [Step 2: Request the VM Instance Creation](#step2)
- [Step 3: Zscaler Creates a Representative Instance for the Gateway](#step3)
- [Step 4: Rerun the Script to Establish the Reverse SSH Tunnel](#step4)
- [Step 5: Zscaler Sets Up the Gateway in the Platform](#step5)
[]The first step in configuring the gateway involves running the script, which installs autossh and generates the public key to send to Zscaler.
Prerequisite
Before running the script, make sure your user account has root privileges, but is not logged in as the root user. You can verify this by running the `sudo -v` command. If you encounter an error such as `Sorry, user <username> may not run sudo on <hostname>`, switch to a different user with root access.
Copying the Script
To copy the script to your server, you can either use the Secure Copy Protocol (`scp`) command or copy the script manually.
- [Copy the Script Using the scp Command (Recommended)](#copy-with-scp)
- [Copy the Script Manually](#copy-manually)
Running the Script
After transferring the script content either via scp or manual copy, run the script using the following command, as a user with root privileges (but not as the root user):
bash zscaler-gateway.sh
After running the script:
- Select **No** if prompted to create an SSH tunnel to the Zscaler gateway; the tunnel is established later.
- Copy and save the newly generated public key displayed in yellow between the `Start copy` and `End copy` prompts to send to Zscaler in the next step.
- Ensure that the autossh package was installed, as this is essential for establishing the tunnel. If the installation fails, manually install autossh using the link provided in the script output, and then rerun the script.
The tunnel is not active at this stage.
[]Copy the script to the server on which you want to configure the tunnel, using the `scp` command:
scp /<Path>/zscaler-gateway.sh <User>@<Server IP>:/<Destination Path>/
Replace the following variables:
- Replace `<Path>` with the local path to the script.
- Replace `<User>` with your username.
- Replace `<Server IP>` with your server IP address.
- Replace `<Destination Path>` with the destination directory on the server.
[]If `scp` is unavailable, you can manually create a new file on the server and paste the script contents. Manual copying can be prone to errors, so use this method with caution and only when necessary.
To copy the script manually:
- Connect to the server where you want to configure the tunnel.
-
Create a new file using the following command:
`touch zscaler-gateway.sh`
- Open the file in your text editor. The following instructions are for Vim:
-
Run the following command:
vim zscaler-gateway.sh
- Press `i` to enter edit mode.
- Copy and paste the content of the downloaded script into the new file.
- Verify that the file starts with `#!/bin/bash` and ends with `# End of file`.
- To save and exit edit mode, press `Esc`, then enter `:wq` and press `Enter`.
[]After you create the SSH key pair, submit a request to Zscaler to provision a VM. To submit the request, email [support@avalor.io](https://support@avalor.io) and [z-avalor-devops@zscaler.com](https://z-avalor-devops@zscaler.com) with the following details:
- The Public SSH key that was [previously generated](#step1).
- Gateway IP address(es):** **The public IP address that the VM will use to access the external network.
- If your VM is configured with a public IP address, include that IP address.
- If your VM only has a private IP address, provide the full list of possible gateway IP addresses.
This information is essential for allowlisting access to the Zscaler instance, ensuring that only your VM can connect.
[]In this step, the Zscaler team provisions the representative instance based on the information you provided in Step 2. When the setup is complete, you receive an email reply from Zscaler confirming that the tunnel is ready to be established.
If the Zscaler team encounters issues in this step, you might be asked to provide logs from your server to assist with troubleshooting. You can do this by running the following command:
journalctl -u avalor-tunnel | tail -n30
The number `30` indicates the number of lines to return. You can increase or decrease this number to adjust the number of log lines returned.
[]Rerun the script from step 1 (provided again below). Select **Yes **when prompted to create the tunnel (you can skip displaying the existing key).
bash zscaler-gateway.sh
When complete, notify the Zscaler team by replying to the original email thread.
[]After you inform Zscaler that the tunnel was successfully established, Zscaler will proceed with configuring the gateway on the platform. You will receive a confirmation via the original email thread when the setup is complete.
Troubleshooting
During the Zscaler gateway setup process, you might encounter an error message such as `May 06 08:53:28 xxxxxxxx autossh[392026]: Host key verification failed`. This typically means that the remote server (Zscaler gateway) has not yet been authorized for its initial SSH connection.
To resolve the authorization issue:
-
Determine which user created the service under `/etc/systemd/system/`. In the example below, the user is `root`.
`ls -la /etc/systemd/system/zscaler-gateway
-rw-r--r-- 1 root root 0 May 7 14:41 zscaler-gateway`
-
Authorize the server from the appropriate user (e.g., `root`) by running the command below. The variables needed for this command are defined in the script provided by Zscaler Support.
`ssh -i $<Key Path> -o StrictHostKeyChecking=no $<Gateway User>@$<Gateway Public DNS Name> "exit"`