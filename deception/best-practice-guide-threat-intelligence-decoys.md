# Best Practice Guide for Threat Intelligence Decoys
Source: https://help.zscaler.com/deception/best-practice-guide-threat-intelligence-decoys
PDF: https://help.zscaler.com/pdf/com/en/1531583.pdf

This best practice guide provides use cases and deployment recommendations for Threat Intelligence (TI) decoys.
Public-facing web applications encounter various security threats and might become initial attack vectors, leading to data breaches. To secure your applications, you can deploy TI decoys.
TI decoys are internet-facing decoys that engage with targeted threats against a named organization. These decoys detect various MITRE ATT&CK techniques and give predictive analytics of attacker activity early in the reconnaissance phase of the kill chain. To learn more, see [About Threat Intelligence Decoys](/deception/about-threat-intelligence-decoys).
Deploy a minimum of 10 TI decoys for all your public-facing infrastructure, which includes a minimum of one content management system (CMS), development, email, VPN, and file share server TI decoys. Configure [application datasets](/deception/adding-dynamic-application-dataset) and subdomain names practically to create realistic TI decoys. It is recommended that you use domain names that resemble backup servers or deprecated services. If adversaries access these decoys, it indicates that they scrapped the DNS A record showing more intent and recon activity.
The following are some of the use cases for TI decoys:
- [Use Case: Deploy TI Decoys That Mimic Content Management Systems](#deception-best-practice-ti-usecase-cms)
- [Use Case: Deploy TI Decoys That Mimic Development Servers](#deception-best-practice-ti-usecase-dev-server)
- [Use Case: Deploy TI Decoys That Mimic Email Servers](#deception-best-practice-ti-usecase-mail-server)
- [Use Case: Deploy TI Decoys That Mimic VPN Servers](#deception-best-practice-ti-usecase-vpn-server)
- [Use Case: Deploy TI Decoys That Mimic File Share Servers](#deception-best-practice-ti-usecase-fileshare-server)
- [Use Case: Deploy TI Decoys with Subdomain Names Not Commonly Found in Dictionaries](#deception-best-practice-ti-usecase-adv-subdomain-server)
- [Use Case: Deploy TI Decoys That Mimic Custom Business-Critical Applications](#deception-best-practice-ti-usecase-adv-critical-app-server)
[]Adversaries exploit vulnerabilities in CMS servers, such as Drupal, WordPress, Jmoola, etc. to gain access to your website. Attackers inject malicious code and steal sensitive information. Deploying TI decoys that mimic CMS servers helps you to detect attacks targeted towards CMS servers.
**Recommendations:**
[Create a TI decoy](/deception/creating-threat-intelligence-decoy) with the following configurations:
- **Subdomain FQDN**: Enter an available subdomain name (e.g., `wordpress1.acme.com`, `drupal2.acme.com`, etc.).
- Select a static, dynamic, or high-interaction decoy [application dataset](/deception/understanding-application-datasets) from the drop-down menu (e.g., **Wordpress Login**, **Drupal Admin Panel**, **Joomla Admin Panel**, **EMC Documentum**, etc.).
-
**Web Server Banner**: Select a server banner from the drop-down menu (e.g., **Apache/2.4.x**).
[See image.](#deception-bp-ti-cms-image)
[]A development server is an environment used by developers to build, test, and debug software before it is pushed to the production server. These servers might be misconfigured to expose internal services. These misconfigurations are an easy-to-target vulnerability and can pose a threat to the entire application stack. Deploying TI decoys that mimic development servers helps you to detect attacks targeted towards development servers.
**Recommendations:**
[Create a TI decoy](/deception/creating-threat-intelligence-decoy) with the following configurations:
- **Subdomain FQDN**: Enter an available subdomain name (e.g., `development1.acme.com`, `uatbackup.acme.com`, etc.).
- Select a static, dynamic, or high-interaction decoy [application dataset](/deception/understanding-application-datasets) from the drop-down menu (e.g., **Jenkins CI/CD Login Portal**, **GitLab, PHP MyAdmin**, **cPanel**, etc.).
-
**Web Server Banner**: Select a server banner from the drop-down menu (e.g., **Jetty 9.4.z-SNAPSHOT**).
[See image.](#deception-bp-ti-dev-image)
[]Adversaries use attack methods such as brute force, credential stuffing, spear phishing, email spoofing, man-in-the-middle attack, etc. to discover vulnerabilities in an email server. If the email server is compromised, it can lead to loss of confidential information. Deploying TI decoys that mimic email servers helps you to detect attacks targeted towards email servers.
**Recommendations:**
[Create a TI decoy](/deception/creating-threat-intelligence-decoy) with the following configurations:
- **Subdomain FQDN**: Enter an available subdomain name (e.g., `owa1.acme.com`, `outlook2.acme.com`, etc.).
- Select a static, dynamic, or high-interaction decoy [application dataset](/deception/understanding-application-datasets) from the drop-down menu (e.g., **OWA**, **IBM Lotus iNotes**, **Mailenable**, etc.).
-
**Web Server Banner**: Select a server banner from the drop-down menu (e.g., **Microsoft-IIS/x**, **Lotus Notes**, etc.)
[See image.](#deception-bp-ti-email-image)
[]VPNs have facilitated remote enterprise access to networks, yet the growing scale and complexity of cyber threats targeting these networks remain a significant concern for security teams. Critical VPN vulnerabilities serve as entry points for attacks. The top threats exploiting VPN vulnerabilities are ransomware, malware, DDoS attacks, spear phishing, etc. Adversaries perform authentication bypass and remote command injection exploits to sign in to external remote services. Deploying TI decoys that mimic VPN servers help you to detect attacks targeted towards VPN servers.
**Recommendations:**
[Create a TI decoy](/deception/creating-threat-intelligence-decoy) with the following configurations:
- **Subdomain FQDN**: Enter an available subdomain name (e.g., `vpn2.acme.com`, `citrix3.acme.com`, etc.).
- Select a static, dynamic, or high-interaction decoy [application dataset](/deception/understanding-application-datasets) from the drop-down menu (e.g., **Citrix NetScaler ADC**, **F5 VPN**, **Checkpoint SSL VPN**, **Cisco SSL VPN**, etc.).
-
**Web Server Banner**: Select a server banner from the drop-down menu (e.g., **Apache**).
[See image.](#deception-bp-ti-vpn-image)
[]A file share server is a physical or virtual server where files are stored. Organizations use file share servers to share documents privately or publicly. Weak permissions or exposed sensitive information (admin passwords and security keys) in file share servers allow adversaries to access internal documents and replace the files with malicious executables. Deploying TI decoys that mimic file share servers helps you to detect attacks targeted towards file share servers.
**Recommendations:**
[Create a TI decoy](/deception/creating-threat-intelligence-decoy) with the following configurations:
- **Subdomain FQDN**: Enter an available subdomain name (e.g., `uploadfileserver1.acme.com`, `downloadfileserver2.acme.com`, `backupfileserver3.acme.com`, etc.).
- Select a static, dynamic, or high-interaction decoy [application dataset](/deception/understanding-application-datasets) from the drop-down menu (e.g., **OwnCloud**, **Synology NAS**, etc.).
-
**Web Server Banner**: Select a server banner from the drop-down menu (**Apache/2.4.x**).
[See image.](#deception-bp-ti-fileshare-image)
[]Adversaries perform reconnaissance by enumerating subdomains using well-known [subdomain dictionaries](https://github.com/danielmiessler/SecLists/blob/master/Discovery/DNS/subdomains-top1million-5000.txt). To increase the chances of discovering the subdomains, adversaries use target-related keywords to create their own subdomains wordlist. Deploying TI decoys with subdomain names not commonly found in dictionaries helps you to prevent adversaries performing reconnaissance on your web applications.
**Recommendations:**
[Create a TI decoy](/deception/creating-threat-intelligence-decoy) with the following configurations:
- **Subdomain FQDN**: Enter a subdomain name which is a combination of the company name and use case (e.g., `xyzbanknb.acme.com`).
- Select a static, dynamic, or high-interaction decoy [application dataset](/deception/understanding-application-datasets) from the drop-down menu per the use case.
[]Creating a TI decoy that looks and behaves like an original application helps you to detect attacks against any business-critical web applications.
**Recommendations:**
Before creating the decoy, clone the business-critical web application’s login page and create a static, dynamic, or high-interaction [application dataset](/deception/understanding-application-datasets).
[Create a TI decoy](/deception/creating-threat-intelligence-decoy) with the following configurations:
- **Subdomain FQDN**: Enter a subdomain name that matches the web application.
- Select the static, dynamic, or high-interaction decoy application** **that you created by cloning the web application.
[]![Configure a TI decoy CMS server](/downloads/deception/getting-started/best-practices/best-practice-guide-threat-intelligence-decoys/zscaler-deception-best-practice-ti-drupal-cms-server-1.png)
[]![Configure a TI development server](/downloads/deception/getting-started/best-practices/best-practice-guide-threat-intelligence-decoys/zscaler-deception-best-pratice-ti-dev-server-1.png)
[]![Configure a TI email server](/downloads/deception/getting-started/best-practices/best-practice-guide-threat-intelligence-decoys/zscaler-deception-best-practice-ti-email-server-1.png)
[]![Configure a TI decoy VPN server](/downloads/deception/getting-started/best-practices/best-practice-guide-threat-intelligence-decoys/zscaler-deception-best-practice-ti-vpn-server-1.png)
[]![Configure a TI decoy file share server](/downloads/deception/getting-started/best-practices/best-practice-guide-threat-intelligence-decoys/zscaler-deception-best-practice-ti-fileshare-server-1.png)