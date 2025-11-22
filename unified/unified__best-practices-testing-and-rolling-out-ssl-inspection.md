# Best Practices for Testing and Rolling Out SSL Inspection
Source: https://help.zscaler.com/unified/best-practices-testing-and-rolling-out-ssl-inspection
PDF: https://help.zscaler.com/pdf/com/en/1493816.pdf

As a best practice, Zscaler recommends that you enable SSL inspection on a small location or test lab before enabling it on all locations in your organization. This allows you to test your deployment of SSL inspection with a select number of users.
To enable SSL inspection, first deploy the[ Zscaler](/unified/choosing-ca-certificate-ssl-inspection#Zscaler-Intermediate-Certificate) or [custom](/unified/choosing-ca-certificate-ssl-inspection#Custom-Intermediate-Root-Certificate) intermediate root certificate. Then, enable SSL inspection for the [location](/unified/about-locations) or [sub-location](/unified/understanding-sub-locations) you are using for testing.
Testing SSL Inspection
Before testing SSL inspection, define the set of users you want to use for testing. For example, you can choose users from the IT department, such as application authors and owners, support staff members, proxy team members, or security team members. You can also choose managers and end users from non-IT departments.
To test SSL inspection:
- Compile a list of the websites and applications that your organization uses for everyday operations. Remember to include vendor sites and applications.
- Enable SSL inspection for the websites and applications from the list by configuring the SSL Inspection policy, and then have the users test them.
When you are configuring the SSL Inspection policy, you are specifying the URL categories or applications that you do not want the service to inspect. For example, if you want to enable SSL inspection for the Legal Liability categories only, then select the **Do Not Inspect** action for all of the URL categories except the Legal Liability categories in your [SSL inspection rule](/unified/configuring-ssl-inspection-policy). The Zscaler service does not perform SSL inspection on the specified URL categories, but does perform SSL inspection on the Legal Liability categories.
- You might need to exempt some sites for SSL inspection permanently, or you might need to report sites to Zscaler Support to identify the cause of failure.
Zscaler recommends not to exempt the **Miscellaneous or Unknown** category for SSL inspection if the traffic forwarded to Zscaler uses transparent proxy mode. In transparent mode, policies on both SNI as well as IP addresses are evaluated for exemption from SSL inspection. Exempting SSL inspection for the **Miscellaneous or Unknown** category exempts almost all traffic from SSL inspection as most IP addresses are categorized as miscellaneous or unknown. However, in the case of explicit traffic forwarding, Zscaler evaluates the policies only based on SNI and does not exempt traffic from SSL inspection based on IP address categories. To learn more, see [Choosing Traffic Forwarding Methods](/unified/choosing-traffic-forwarding-methods).
- After testing the list of websites and applications, test SSL inspection for the [URL categories](/unified/about-url-categories). As a best practice, Zscaler recommends that you enable SSL inspection for only certain URL categories at a time, and include the rest of the categories in the list of URL categories for which SSL transactions are not to be decrypted. Then, when your organization is ready, enable SSL inspection for all URL categories.
Some organizations choose to bypass SSL inspection for Finance and Health URL categories due to privacy concerns. Zscaler recommends that you enable SSL inspection for all URL categories.
Enable and test SSL inspection for the URL categories in the following order of phases.
- [Click to see the URL categories in phase 1.](#phase1)
[]
| **Phase 1** |
| ----------- |
| Adult Themes |
| Alcohol and Tobacco |
| Anonymizer |
| Computer Hacking |
| Copyright Infringement |
| Drugs |
| Gambling |
| Mature Humor |
| Militancy, Hate and Extremism |
| Newly Registered and Observed Domains |
| Non Categorizable |
| Nudity |
| Other Adult Material |
| Other Illegal or Questionable |
| Other Security |
| Peer-to-Peer Site |
| Pornography |
| Profanity |
| Questionable |
| Social Networking Adult |
| Spyware/Adware |
| Tasteless |
| Violence |
| Weapons/Bombs |
Before testing the URL categories in phase 2, remember to keep SSL inspection enabled for the URL categories in phase 1.
- [Click to see the URL categories in phase 2.](#phase2)
[]
| **Phase 2** |
| ----------- |
| Adult Sex Education |
| Alt or New Age |
| Alternate Lifestyle |
| Art and Culture |
| Continuing Education/Colleges |
| Corporate Marketing |
| Cult |
| Dining and Restaurant |
| Entertainment |
| Family Issues |
| Government |
| History |
| Hobbies and Leisure |
| Job/Employment Search |
| K-12 |
| K-12 Sex Education |
| Lingerie/Bikini |
| Music |
| Online Auctions |
| Online Shopping |
| Other Education |
| Other Entertainment/Recreation |
| Other Games |
| Other Government and Politics |
| Other Information Technology |
| Other Internet Communication |
| Other Religion |
| Other Shopping and Auctions |
| Other Social and Family Issues |
| Other Society and Lifestyle |
| Politics |
| Radio Stations |
| Real Estate |
| Reference Sites |
| Science/Tech |
| Body Art |
| Social Issues |
| Social Networking |
| Social Networking Games |
| Special Interests/Social Organizations |
| Sports |
| Television/Movies |
| Traditional Religion |
| Translators |
| Travel |
| Vehicle |
Before testing the URL categories in phase 3, remember to keep SSL inspection enabled for the URL categories in phases 1 and 2.
- [Click to see the URL categories in phase 3.](#phase3)
[]
| **Phase 3** |
| ----------- |
| Blogs |
| Classifieds |
| Content Delivery Networks |
| Discussion Forums |
| File Host |
| Image Host |
| Internet Services |
| Miscellaneous or Unknown |
| News and Media |
| Online Chat |
| Other Business and Economy |
| Portals |
| Professional Services |
| Remote Access |
| Safe Search Engine |
| Shareware Download |
| Streaming Media |
| Advertising |
| Web Host |
| Web Search |
| Webmail |