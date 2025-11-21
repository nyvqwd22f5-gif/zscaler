# Disabling Password Expiration for STIG-Hardened Private Service Edge Images
Source: https://help.zscaler.com/unified/disabling-password-expiration-stig-hardened-private-service-edge-images
PDF: https://help.zscaler.com/pdf/com/en/1520896.pdf

This information applies to Security Technical Implementation Guide (STIG) images that were released on November 24, 2024 and December 12, 2024. STIG images released after these dates are not affected.
If you're using an image that supports STIG compliance, passwords automatically expire every 60 days for Amazon Web Services (AWS), Google Cloud Platform (GCP), and Microsoft Azure, or 95 days (60 days + a 35-day grace period) for VMware.
If the password expires without changing it or disabling expiration, admin access to a Private Service Edge for Private Applications is no longer available. When admin access expires, the only recovery method is to deploy a new Private Service Edge.
The STIG-hardened prebuilt Private Service Edge image release dates are:
- AWS and GCP: November 24, 2024
- Azure and VMware: December 12, 2024
To verify if an image is STIG-hardened:
- Go to the Private Service Edges page in the Admin Portal.
- Expand the row for a Private Service Edge in the table.
- Under **Private Service Edge Host Platform**, if you see `ZSIVersion: 2024.11` or `ZSIVersion: 2024.12` for the ZSIVersion, the image is STIG-hardened.
[See image.](#StigImage)
Zscaler recommends using one of these methods for passwords:
- [Disable or set a password for AWS, GCP, and Azure.](#StigMarketplace)
- [Disable or set a password for VMware.](#StigOVAs)
- []Disable the password expiration:
-
Enter the following command (replacing `admin` with your admin username):
``[admin@zpa-service-edge ~]$ sudo chage -M -1 adm`in`
-
Verify that the password is set to never expire.
``[admin@zpa-service-edge ~]$ sudo chage -l adm`in
`Last password change                               : Feb 18, 20`25
`Password expires                                   : never`
`Password inactive                                  : never`
`Account expires                                    : never`
Minimum number of days between password change     : 1
Maximum number of days between password change     : -1
Number of days of warning before password expires  : 7`
- Set a password when creating a new instance using `passwd admin` (replacing `admin` with your admin username) and renew it every 60 days.
-
[]Disable the password expiration by entering the following command (replacing `admin` with your admin username):
`$ sudo chage -M -1 admin`
- Set a password when creating a new instance using `passwd admin` (replacing `admin` with your admin username) and renew it every 60 or 95 days.
[]
Example STIG-hardened image with `ZSIVersion: 2024.11.`
![Verify STIG-hardened image on a ZPA Private Service Edge](/downloads/tech-pubs-drafts/zpa-draft-articles/app-connector-deployment-guide-amazon-web-services-draft-doc-56293/zpa-pse-stig-image-verification-nov2024.png)