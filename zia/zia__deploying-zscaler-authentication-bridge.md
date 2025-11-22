# Deploying a Zscaler Authentication Bridge
Source: https://help.zscaler.com/zia/deploying-zscaler-authentication-bridge
PDF: https://help.zscaler.com/pdf/com/en/1399636.pdf

The Zscaler Authentication Bridge (ZAB) is a virtual machine (VM) that you can use to [provision and authenticate users](/zia/about-provisioning-authenticating-users). To learn more, see [About the Zscaler Authentication Bridge](/zia/about-zscaler-authentication-bridge).
If you're subscribed to multiple ZABs, only one ZAB can synchronize your users. For example, you can deploy two ZABs, and the Zscaler service automatically uses the healthy one to sync users. If you also want to use the ZAB for authentication, ensure the configured ZAB URL can address both ZABs. During deployment, you can create a DNS entry for the ZAB. The user is redirected to the URL during the password authentication phase. You can implement a round-robin DNS or put the ZABs behind a load balancer to achieve an active deployment.
New or clean deployment of ZAB requires VM image running on Zscaler OS version 24.
Requirements
Ensure you have the following to deploy the ZAB:
- Hypervisor VMware ESX/ESXi version 6.0 and later.
- A VM with:
- 2 GB of RAM minimum. This increases with the number of users.
- 64-bit Xeon CPU. Two cores assigned to the VM.
- 1 network interface with a static IP address. This IP address is used for control and data connections to the Zscaler cloud and to connect to the directory server. Your administrator can also use it to make an SSH connection to the VM.
- A ZAB subscription.
- [Super admin](/zia/adding-super-admin-role) access for the ZIA Admin Portal.
- Log in information for your directory server.
Prerequisites
Ensure your outbound firewall is configured to allow the necessary connections. The ZAB requires outbound connections to the Zscaler service. To view the firewall requirements, go to:
https://config.zscaler.com/<Zscaler Cloud Name>/zab
The <Zscaler Cloud> depends on the URL you use to log in to the Zscaler service. For example, if you log in to admin.zscalerbeta.net, then go to https://config.zscaler.com/zscalerbeta.net/zab. To learn more, see [What is my cloud name for ZIA?](/zia/what-my-cloud-name-zia)
Deploying a ZAB
Only [super admins](/zia/adding-super-admin-role) can deploy a ZAB.
To deploy a ZAB:
- [1. Verify the ZAB subscription.](#verifyzab)
- [2. Add the ZAB using the ZIA Admin Portal.](/zia/adding-zscaler-authentication-bridge)
- [3. Download the ZAB virtual machine (VM).](/zia/downloading-zscaler-authentication-bridge-vm)
- [4. Download the ZAB SSL certificate.](#downloadzabssl)
- [5. Configure the ZAB network settings.](#confignetworksettings)
- [6. Install the ZAB client SSL certificate.](#clientcert)
- [7. Install the server SSL certificate.](#servercert)
- [8. Install and start the ZAB software.](#zabsoftware)
- [9. (Optional) Configure nested groups on the ZAB.](#configure-nested-groups)
- [10. Configure the user synchronization settings.](#syncsettings)
- [11. (Optional) Configure the local NTP server to synchronize time with the ZAB.](#ntpserver)
Troubleshooting
You can use the following commands to troubleshoot your ZAB configuration:
- Enter the following command to view a ​​list of the ZAB commands:
zab -h
- Enter the following command to run a script to test access to the outbound firewall:
zab test-firewall
- Enter the following command to collect all the relevant ZAB log files and configuration files. You can then compress the files into a ZIP file and send it to Zscaler Support for troubleshooting.
zab collect-diagnostics
- Enter the following command to allow Zscaler Support remote access to examine and diagnose configuration errors. This feature is disabled by default.
zab enable-remote-debugging
- Enter the following command to allow Zscaler Support remote access to log in to your ZAB via SSH. An interactive shell is useful when additional troubleshooting assistance is required. This feature is disabled by default.
zab support-access-start
[]To verify your organization's ZAB subscription:
- Go to **Administration**** **>** Company Profile**.
- Click the **Subscriptions** tab.
- Verify that your organization is subscribed to **Zscaler Auth Bridge**.
[See image.](#seeimage1c)
[]![Screenshot of the Zscaler Authentication Bridge subscription on the Subscriptions page](/downloads/zia/authentication-administration/user-management-authentication-settings/zscaler-authentication-bridge/how-do-i-deploy-zscaler-authentication-bridge/02_zscaler_authentication_bridge_subscription_on_the_subscriptions_page.png)
[]The ZAB uses an SSL certificate to authenticate itself to the Zscaler service.
To download the ZAB SSL certificate:
- Go to **Administration** >** Authentication Settings**.
- Click the **Authentication ****Bridges **tab.
- In the **SSL Certificate** column of the ZAB, click **Download**.
[See image.](#seeimage4c)
[]![Screenshot of the Download button for the authentication bridge](/downloads/zia/authentication-administration/user-management-authentication-settings/zscaler-authentication-bridge/how-do-i-deploy-zscaler-authentication-bridge/03_download_button.png)
[]To configure the network settings of the ZAB:
- On the ZAB, log in with the following default credentials:
- **Username**: zsroot
- **Password**: zsroot
[See image.](#seeimg1)
- Switch to a superuser, by entering the following command:
sudo su -
- Enter the password. In this example, it's `zsroot`.
[See image.](#seeimg3)
- Enter the following command to configure the ZAB network settings:
zab configure
- Enter the the following information for the network settings:
- Name server IP address
- ZAB IP address and netmask
[See image.](#seeimg4)
- Enter the following command to verify your configuration:
zab dump-config
[See image.](#seeimg5)
Zscaler strongly recommends that you change the default password by entering the following command
passwd <Username>
For example, if you're using the default username, enter "passwd zsroot".
[See image.](#seeimg2)
[]![Screenshot logging in to the ZAB VM console](/downloads/zia/documentation-knowledgebase/authenticating-and-managing-users/zscaler-authentication-bridge/configuring-zscaler-authentication-bridge/how-do-i-deploy-zscaler-authentication-bridge/zab_vm_console_login.png)
[]![Screenshot changing the password in the ZAB VM console](/downloads/zia/documentation-knowledgebase/authenticating-and-managing-users/zscaler-authentication-bridge/configuring-zscaler-authentication-bridge/how-do-i-deploy-zscaler-authentication-bridge/new_password_in_the_zab_vm_console.png)
[]![Screenshot switching to a superuser in the ZAB VM console](/downloads/zia/documentation-knowledgebase/authenticating-and-managing-users/zscaler-authentication-bridge/configuring-zscaler-authentication-bridge/how-do-i-deploy-zscaler-authentication-bridge/superuser_command_in_the_zab_vm_console.png)
[]![Screenshot of the ZAB configuration in the ZAB VM console](/downloads/zia/documentation-knowledgebase/authenticating-and-managing-users/zscaler-authentication-bridge/configuring-zscaler-authentication-bridge/how-do-i-deploy-zscaler-authentication-bridge/zab_configuration_in_the_zab_vm_console.png)
[]![Screenshot of the zab dump-config command in the ZAB VM console](/downloads/zia/documentation-knowledgebase/authenticating-and-managing-users/zscaler-authentication-bridge/configuring-zscaler-authentication-bridge/how-do-i-deploy-zscaler-authentication-bridge/zab_dump-config_command_in_the_zab_vm_console.png)
[]Install the ZAB SSL certificate you downloaded from the ZIA Admin Portal in [4. Download the ZAB SSL Certificate](/zia/how-do-i-deploy-zscaler-authentication-bridge#downloadzabssl). The certificate authenticates the ZAB to the Zscaler service.
To install the ZAB SSL certificate:
- Copy the client certificate securely to the ZAB VM. Zscaler recommends that you use SCP or SFTP instead of FTP.
- On the ZAB, enter the following command to install the ZAB:
zab install-client-cert ZabCert.zip
[See image.](#seeimg6)
- Enter the following command to verify that the ZAB is associated with the Zscaler cloud and your organization:
zab dump-config
[See image.](#seeimg7)
[]![Screenshot of the zab install-client-cert ZabCert.zip command in the ZAB VM console](/downloads/zia/documentation-knowledgebase/authenticating-and-managing-users/zscaler-authentication-bridge/configuring-zscaler-authentication-bridge/how-do-i-deploy-zscaler-authentication-bridge/zab_install-client-cert_zabcert.zip_command_in_the_zab_vm_console.png)
[]![Screenshot of the zab dump-config command in the ZAB VM console](/downloads/zia/documentation-knowledgebase/authenticating-and-managing-users/zscaler-authentication-bridge/configuring-zscaler-authentication-bridge/how-do-i-deploy-zscaler-authentication-bridge/zab_dump-config_command_in_the_zab_vm_console.png)
[]In order for the ZAB to authenticate a user against the AD, it needs to present the user with an authentication form, where the user enters their credentials to be validated against the AD. To be able to serve the form over a webpage, the ZAB has an HTTPS server component running on it.
You can either install your own certificate signed by a trusted Certificate Authority or install a self-signed certificate. A server certificate from an issuing authority must be used if you're using the ZAB for user authentication. This prevents the user from seeing a server certificate warning in the browser. However, if you're using ZAB only to provision users but not to authenticate them, you can allow the system to generate a self-signed certificate.
Configure one of the following options:
- [Install A Certificate Signed by a Trusted Certificate Authority](#cert-signed-trusted-cert-auth)
- [Install a Self-Signed Certificate](#self-signed-cert)
[]To install a certificate signed by a trusted Certificate Authority:
- Copy the server certificate and the private key on to the ZAB.
- Copy the full path of the certificate and the private key.
- Enter the following command:
zab install-server-cert
- Enter the full path of the server certificate in PEM format.
- Enter the full path of the server private key.
- (Optional) Enter a passphrase to decrypt the private key. There are no restrictions for the passphrase.
- Enter `y` when it asks if you have a separate host CA certificate file.
- Enter the full path of the host CA certificate in PEM format.
root@ZAB:/usr/home/zsroot/servercerts # zab install-server-cert
Please enter full path of the server certificate in PEM format (Empty to generate self-signed cert): /var/test_servercert.pem
Please enter full path of the server key in PEM format: /usr/home/zsroot/servercerts/zscaler.encrypted.key
Please enter passphrase for decrypting the server key:
REPEAT: Please enter passphrase for decrypting the server key:
Validating pass_phrase with /usr/home/zsroot/servercerts/zscaler.encrypted.key...
Pass phrase works!
Do you have a separate host CA certificate file? <y/n> : [y]: y
Please enter complete path of the host CA certificate file:/usr/home/zsroot/servercerts/chain.pem
Copying files to /sc/conf...
Finished server certificate installation.
[]To install a self-signed certificate:
- Enter the command:
zab install-server-cert
[See image.](#seeimage20)
- Click **Enter** on your keyboard.
- Under **Self signed certificate generation**, enter your domain name.
- Enter a passphrase for generating the certificate. There are no restrictions for the passphrase.
[See image.](#seeimage21)
**[]**![Screenshot of the command to generate server certificate](/downloads/zia/documentation-knowledgebase/authenticating-and-managing-users/zscaler-authentication-bridge/configuring-zscaler-authentication-bridge/how-do-i-deploy-zscaler-authentication-bridge/zia-zab-server-cert-cmd.png)
****[]****![Screenshot of the commands issued to generate a self signed certificate](/downloads/zia/documentation-knowledgebase/authenticating-and-managing-users/zscaler-authentication-bridge/configuring-zscaler-authentication-bridge/how-do-i-deploy-zscaler-authentication-bridge/zia-zab-self-signed.png)
[]To install and start the ZAB software:
- Enter the following command to install and update the ZAB software:
zab update-now
[See image.](#seeimg8)
- Enter the following command to start the ZAB:
zab start
[See image.](#seeimg9)
- Enter the following command to enable ZAB automatic startup:
zab enable-autostart
[See image.](#seeimg10)
- Enter the following command to display the process running:
zab status
[See image.](#seeimg11)
- Enter the following command to verify the ZAB is making outbound connections:
sockstat -4
[See image.](#seeimg12)
[]![Screenshot of the zab update-now command in the ZAB VM console](/downloads/zia/documentation-knowledgebase/authenticating-and-managing-users/zscaler-authentication-bridge/configuring-zscaler-authentication-bridge/how-do-i-deploy-zscaler-authentication-bridge/zab_update-now_command_in_the_zab_vm_console.png)
[]![Screenshot of the zab start command in the ZAB VM console](/downloads/zia/documentation-knowledgebase/authenticating-and-managing-users/zscaler-authentication-bridge/configuring-zscaler-authentication-bridge/how-do-i-deploy-zscaler-authentication-bridge/zab_start_command_in_the_zab_vm_console.png)
[]![Screenshot of the zab enable-autostart command in the ZAB VM console](/downloads/zia/documentation-knowledgebase/authenticating-and-managing-users/zscaler-authentication-bridge/configuring-zscaler-authentication-bridge/how-do-i-deploy-zscaler-authentication-bridge/zab_enable-autostart_command_in_the_zab_vm_console.png)
[]![Screenshot of the zab status command in the ZAB VM console](/downloads/zia/documentation-knowledgebase/authenticating-and-managing-users/zscaler-authentication-bridge/configuring-zscaler-authentication-bridge/how-do-i-deploy-zscaler-authentication-bridge/zab_status_command_in_the_zab_vm_console.png)
[]![Screenshot of the sockstat -4 command in the ZAB VM console](/downloads/zia/documentation-knowledgebase/authenticating-and-managing-users/zscaler-authentication-bridge/configuring-zscaler-authentication-bridge/how-do-i-deploy-zscaler-authentication-bridge/sockstat_-4_command_in_the_zab_vm_console.png)
[]Nesting groups is adding a group as a member of another group in order to consolidate member accounts and reduce replicated traffic. Enabling nested groups on the ZAB allows the Zscaler service to flatten and sync user group membership for nested groups.
To enable nested groups on the ZAB:
- Enter the following command to enable nested groups:
zab enable-nested-groups
[See image.](#seeimage9a)
- Restart the ZAB
To disable nested groups on the ZAB:
- Enter the following command to disable nested groups:
zab disable-nested-groups
[See image.](#seeimage9a2)
- Restarts the ZAB
[]![Screenshot of the ZAB CLI commands for enabling nested groups.](/downloads/zia/documentation-knowledgebase/authenticating-and-managing-users/zscaler-authentication-bridge/configuring-zscaler-authentication-bridge/how-do-i-deploy-zscaler-authentication-bridge/zia-zab-enable-nested-groups.png)
[]![Screenshot of the ZAB CLI commands for disabling nested groups.](/downloads/zia/documentation-knowledgebase/authenticating-and-managing-users/zscaler-authentication-bridge/configuring-zscaler-authentication-bridge/how-do-i-deploy-zscaler-authentication-bridge/zia-zab-disable-nested-group.png)
[]After you configure the ZAB, you must use the Zscaler Authentication Wizard to synchronize users with the ZAB. You optionally can configure the service to use the ZAB for authentication as well. To learn more about the steps in the Authentication Wizard, see [Synchronizing User Data with an Active Directory or OpenLDAP](/zia/synchronizing-user-data-active-directory-openldap#setupwizard).
To configure the Zscaler service to synchronize users with the ZAB:
- In the ZIA Admin Portal, go to **Administration **>** Authentication Settings**.
- In the **Authentication Profile** tab, under **Directory Type**, choose **Active Directory**.
[See image.](#seeimage-zab)
- Click **Authentication Wizard**.
[See image.](#seeimg13)
- In **Directory Server**:
- **Authentication Agent Hosting**: Choose **Enterprise**.
- **Directory Server IP Address**: Enter the IP address of the directory server that the ZAB connects to.
- **Authentication Agent Address**: Enter the ZAB URL if your organization is using the ZAB for user authentication. If your organization is using another authentication mechanism (e.g., SAML or OpenLDAP), then you can enter any IP address.
- Click **Next**.
[See image.](#seeimg14)
- In **Authentication**:
- **Use Anonymous Authentication**: Enable if the directory server allows anonymous access. Ensure that this option is also enabled on your directory server.
- **Bind DN**: Enter the DN of any user account to query the directory server. The user doesn't have to be an administrator.
- **Bind Password**: Enter the password of the entered user account.
- Click **Next**.
[See image.](#seeimg15)
- In **Detected Settings**:
- **Base DN**: The Zscaler service connects to the directory server and automatically populates this field.
- **Pagination**: Choose **Auto**** (Recommended)**.
- Click **Next**.
[See image.](#seeimg16)
- In **Lookup & Attributes**:
- **Lookup Parameters**: Choose **Auto**.
- **Lookup User Entry**: Enter an email address, login name, DN, or LDAP attribute., and click **Look Up User**. The Zscaler service queries the directory server for the user entry and attributes.
- **Lookup Results**: Displays the user's attributes that were retrieved from the directory server. The Zscaler service uses this information to populate the **Attributes Field** section below.
- Click **Next**.
[See image.](#seeimg17)
- In **Synchronization**, click **Start Synchronization** to start synchronizing the Zscaler service with the directory server. The wizard displays the synchronization status and results. Click **Next**.
[See image.](#seeimg18)
- In **Authentication Parameters**:
- **Test User Login**: Enter a test user's login ID.
- **Test User Password**: Enter a test user's password.
- **Check Authentication**: Click to verify the user's credentials, and ensure the information was synchronized correctly.
- Click **Next**.
[See image.](#seeimg19)
- In **Review**, click **Finish**.
[]![Screenshot highlighting the Active Directory option under the Directory Type.](/downloads/zia/authentication-administration/user-management-authentication-settings/zscaler-authentication-bridge/deploying-zscaler-authentication-bridge/ZIA-Authentication-Profile-Directory-Type.png)
[]![Screenshot highlighting the Authentication Wizard option for Active Directory.](/downloads/zia/authentication-administration/user-management-authentication-settings/zscaler-authentication-bridge/deploying-zscaler-authentication-bridge/ZIA-Authentication-Profile-Active-Directory-Authentication-Wizard.png)
[]![Screenshot of the configured Directory Server step in the Authentication Wizard.](/downloads/zia/authentication-administration/user-management-authentication-settings/zscaler-authentication-bridge/deploying-zscaler-authentication-bridge/ZIA-Authentication-Wizard-Primary-Directory-Server.png)
[]![Screenshot of the configured Authentication step in the Authentication Wizard.](/downloads/zia/authentication-administration/user-management-authentication-settings/zscaler-authentication-bridge/deploying-zscaler-authentication-bridge/zia-authentication-wizard-authentication.png)
[]![Screenshot of the configured Detected Settings step in the Authentication Wizard.](/downloads/zia/authentication-administration/user-management-authentication-settings/zscaler-authentication-bridge/deploying-zscaler-authentication-bridge/zia-authentication-wizard-detected-settings.png)
[]![Screenshot of the configured Lookup & Attributes step in the Authentication Wizard.](/downloads/zia/authentication-administration/user-management-authentication-settings/zscaler-authentication-bridge/deploying-zscaler-authentication-bridge/zia-authentication-wizard-lookup-attributes-active-directory.png)
[]![Screenshot of the configured Synchronization step in the Authentication Wizard.](/downloads/zia/authentication-administration/user-management-authentication-settings/zscaler-authentication-bridge/deploying-zscaler-authentication-bridge/zia-authentication-wizard-synchronization.png)
[]![Screenshot of the configured Authentication Parameters step in the Authentication Wizard.](/downloads/zia/authentication-administration/user-management-authentication-settings/zscaler-authentication-bridge/deploying-zscaler-authentication-bridge/zia-authentication-wizard-authentication-parameters.png)
[]Optionally, if you have a local NTP server, you can configure the ZAB to synchronize time with the server.
To configure the ZAB to synchronize time with the NTP server:
- On the ZAB, enter the following command:
crontab -e
- Add the following line with your local NTP server name:
*/10 * * * * ntpdate <NTP Server Name>
- Save and exit.
The time synchronization command runs every 10 minutes.