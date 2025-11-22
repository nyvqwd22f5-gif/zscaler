# Understanding Lookalike Domain Details
Source: https://help.zscaler.com/easm/understanding-lookalike-domain-details
PDF: https://help.zscaler.com/pdf/com/en/1508146.pdf

The lookalike domains that are detected for your seed domains are investigated and cataloged on the [Lookalike Domains page](/easm/about-lookalike-domains) (Insights > Lookalike Domains). This page provides a customizable, tabulated list where you can click each domain entry to access more detailed information and take specific actions. The lookalike domain details consist of contextual information, helping you understand key aspects, such as the original domain forged by the lookalike domain, domain registration details, risk category and risk score, deception tactics used in the domain name, domain detection timeline, and status.
To view comprehensive information about a lookalike domain, click on an entry in the table. A right-side drawer referred to as the Lookalike Domain Details drawer opens. In this drawer, you can access the following information about the lookalike domain:
- **Original Domain**: The legitimate domain mimicked by the lookalike domain.
- **Lookalike Domain Annotation**: A label for the lookalike domain.
-
**Risk Category**: The risk categorization of the lookalike domain.
[Available Risk Categories](#risk-categories)
- **Risk Score**: A risk score assigned for the lookalike domain.
- **Deception Method**: The deception tactic used in the lookalike domain name to impersonate a legitimate domain. Examples of deception techniques include the use of homograph (i.e., by exploiting similar-looking characters or homoglyphs), substituting letters with numbers, hyphenation, intentional typos, adding, removing, or transposing letters, etc.
- **Lookalike Domain Registrar**: The internet company that was used to register the domain, if available. Popular registrars include GoDaddy, Namecheap, Bluehost, Domain.com, etc.
- **Lookalike Domain Registered**: Indicates whether the domain is registered with a registrar or not.
- **Lookalike Registrant Organization**: An individual or entity that owns the registered domain, if available.
- **Lookalike Registration Expiration**: The domain registration expiration date, if available.
- **First Seen**: The timestamp when the lookalike domain was first identified in a scan.
- **Last Seen**: The timestamp when the lookalike domain was last observed in a scan.
-
**Status**: The status assigned to the lookalike domain entry from Not Verified, Verified, Risk Accepted, Resolved, and Disputed. You can modify the status using the drop-down menu as needed.
[Available Statuses](#statuses)
- **Description**: A description of the lookalike domain, why it is suspicious, and the deception tactics used.
[See image.](#lookalike-domain-details-image)
- []**Verified Phishing**: Indicates that the domain is verified to be a phishing site by Zscaler's web risk analyzer service.
- **Registered Lookalike**: Indicates that the domain is registered through an internet company that provides domain registration services (i.e., registrar).
- **Preventative Lookalike**: Indicates that the domain is not registered with a registrar.
- []**Not Verified**: All lookalike domains initially detected by EASM for your legitimate seed domains are automatically tagged with the label "Not Verified".
- **Verified**: Lookalike domains are manually investigated and verified for risks. An example could be a high-risk domain that is verified to be a phishing site.
- **Risk Accepted**: Represents that the risk is deemed acceptable. An example could be a domain that is not registered yet and can be put on the watch list.
- **Resolved**: Lookalike domains for which remediation steps are taken or are planned can be marked as resolved. For example, if a fake domain is taken offline or suspended by the registrar after reporting and the threat is eliminated, it can be marked as resolved. However, if the lookalike domain is discovered again in a subsequent scan, then it is marked as "Not Verified".
- **Disputed**: If the manual verification of a lookalike domain turns out differently from the original detection, the lookalike domain can be moved to the Disputed status, indicating that it might be a false positive.
[See image.](#lookalike-domain-status-change-image)
[]![Lookalike domain details page showing key information in the EASM Admin Portal](/downloads/easm/insights/lookalike-domains/understanding-lookalike-domain-details/Lookalikedomain-details.png)
[]![Lookalike domain status change in the EASM Admin Portal](/downloads/easm/insights/lookalike-domains/understanding-lookalike-domain-details/lookalike-domain-statuses.gif)