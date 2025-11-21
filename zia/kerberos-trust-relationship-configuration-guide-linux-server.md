# Kerberos Trust Relationship Configuration Guide for Linux Server
Source: https://help.zscaler.com/zia/kerberos-trust-relationship-configuration-guide-linux-server
PDF: https://help.zscaler.com/pdf/com/en/1399581.pdf

Kerberos support in Linux is provided by both the MIT Kerberos package or Heimdal package. Use the appropriate version available with your distribution. The Kerberos configuration file is in /etc/krb5.conf. A sample configuration file is provided below. Only the text in blue is the Zscaler-specific configuration. It is assumed that Kerberos authentication has been configured and is operational.
![Screenshot of the Kerberos configuration on the Linux server](/downloads/zia/documentation-knowledgebase/authenticating-and-managing-users/kerberos/kerberos-deployment-guide/kerberos-configuration-example-trust-relationship-linux-server/kerberos_configuration_on_the_linux_server.png)
Ensure that you are already logged in by running the klist command:
![Screenshot of the klist command on the Linux server](/downloads/zia/documentation-knowledgebase/authenticating-and-managing-users/kerberos/kerberos-deployment-guide/kerberos-configuration-example-trust-relationship-linux-server/klist_command_on_the_linux_server.png)
If no tickets are found, run the kinit command:
![Screenshot of the kinit command on the Linux server](/downloads/zia/documentation-knowledgebase/authenticating-and-managing-users/kerberos/kerberos-deployment-guide/kerberos-configuration-example-trust-relationship-linux-server/kinit_command_on_the_linux_server.png)
Validate the Configuration
![Screenshot verifying the Kerberos configuration on the Linux server](/downloads/zia/documentation-knowledgebase/authenticating-and-managing-users/kerberos/kerberos-deployment-guide/kerberos-configuration-example-trust-relationship-linux-server/kerberos_configuration_validation_on_the_linux_server.png)
Configure Firefox
To configure Firefox, do the following:
- In the address bar of Firefox, enter** about:config** to display the advanced configuration options.
- In the Filter field, type negotiate to narrow down the list.
- Set the following field to the respective values:
**network.negotiate-auth.trusted-uris**: gateway.zscalerbeta.net, .gateway.zscalerbeta.net
If authentication fails, open a terminal and execute the following commands:
user@linux~$ export NSPR_LOG_MODULES=negotiateauth:5
user@linux~$ export NSPR_LOG_FILE=/tmp/firefox-dbug.log
user@linux~$ firefox
The file /tmp/firefox-dbug.log contains the trace of events that might be useful when investigating issues.
Troubleshooting
To troubleshoot your Kerberos configuration, see [Troubleshooting Kerberos](/zia/troubleshooting-kerberos) and [ZIA Public Service Edge Error Codes for Kerberos](/zia/zen-error-codes-kerberos).