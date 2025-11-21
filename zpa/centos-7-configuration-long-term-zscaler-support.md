# CentOS 7 Configuration for Long-Term Zscaler Support
Source: https://help.zscaler.com/zpa/centos-7-configuration-long-term-zscaler-support
PDF: https://help.zscaler.com/pdf/com/en/1488081.pdf

The Zscaler-hosted repository provides Long-Term Support (LTS) for CentOS 7 and includes security patches for critical CVEs affecting the operating system.
Zscaler will end support of the CentOS 7 LTS repository after the posted End-of-Support (EOS) of ZPA for CentOS 7. To learn more, see [End-of-Support for CentOS 7.x, RHEL 7.x, and Oracle Linux 7.x](/eos-eol/end-support-centos-7.x-rhel-7.x-and-oracle-linux-7.x).
To configure CentOS 7 for LTS:
- (Optional) If it doesn't already exist, enter the following content under `/etc/yum.repos.d/zscaler.repo`:
`[zscaler]
name=Zscaler Private Access Repository
baseurl=https://yum.private.zscaler.com/yum/el7
enabled=1
gpgcheck=1
gpgkey=https://yum.private.zscaler.com/gpg`
- Enter the following content under `/etc/yum.repos.d/centos-longterm.repo`:
`[centos-7-for-x86_64-baseos-eus-rpms]
name=CentOS 7 for x86_64 EUS RPMS
gpgkey=https://os-updates-eus.private.zscaler.com/centos-mirror/RPM-GPG-KEY-CENTOS-7-BASE-EUS
gpgcheck=1
enabled=0
baseurl=https://os-updates-eus.private.zscaler.com/centos-mirror/centos-7-for-x86_64-baseos-eus-rpms`
- Disable all other repositories using the following command:
`$ yum-config-manager --disable \*`
- Enable the Zscaler repository using the following command:
`$ yum-config-manager --enable zscaler`
- Enable the CentOS 7 LTS repository using the following command:
`$ yum-config-manager --enable centos-7-for-x86_64-baseos-eus-rpms`
- Verify that only the Zscaler repository and the CentOS 7 LTS repository exist using the following command:
`$ yum repolist`
- Perform a yum update using the following command:
`$ yum update`
The steps to configure CentOS7 for LTS apply to both App Connectors and ZPA Private Service Edges.