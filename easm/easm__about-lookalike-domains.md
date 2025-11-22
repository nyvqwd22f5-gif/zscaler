# About Lookalike Domains
Source: https://help.zscaler.com/easm/about-lookalike-domains
PDF: https://help.zscaler.com/pdf/com/en/1508141.pdf

As part of the asset discovery process that maps out your organization's digital attack surface, EASM identifies and tracks lookalike domains that are fraudulent or fake domains intentionally created by threat actors to mimic your legitimate domains. These domains, often used in phishing and other malicious activities, leverage domain spoofing techniques to deceive users into downloading malware or revealing sensitive information by acting under the guise of a trusted source. EASM detects lookalike domains for the seed domains configured via a [discovery profile](/easm/about-discovery-profiles).
Lookalike domains provide the following benefits and enable you to:
- Identify lookalike or phishing domains associated with your organization's legitimate domains and implement threat mitigation controls.
- Safeguard your customers and employees from phishing domains and other forms of cyberattacks, protect your brand identity, and prevent financial loss from cyberattacks.
About the Lookalike Domains Page
On the Lookalike Domains page (Insights > Lookalike Domains), you can do the following:
- View the list of lookalike domains that are detected for your seed domains configured for the selected organization. For each lookalike domain, you can view:
- **Lookalike Domain**: The lookalike domain name.
- **Original Domain**: The legitimate domain impersonated by the lookalike domain.
- **Risk Category**: The risk categorization of the lookalike domain into Verified Phishing, Registered Lookalike, and Preventative Lookalike.
- **Exposure Score**: A risk score computed for the lookalike domain.
- **Deception Method**: The deception tactic used in the lookalike domain name to impersonate a legitimate domain. Examples of deception techniques include the use of homograph (i.e., by exploiting similar-looking characters or homoglyphs), substituting letters with numbers, hyphenation, intentional typos, adding, removing, or transposing letters, etc.
- **Status**: The status assigned to the lookalike domain entry from Not Verified, Verified, Risk Accepted, Resolved, and Disputed.
- **First Seen**: The timestamp when the lookalike domain was first identified in a scan.
- **Last Seen**: The timestamp when the lookalike domain was last observed in a scan.
- **Registered**: The registration status of the lookalike domain through a domain name registrar.
- **Registered By**: An individual or entity responsible for registering the lookalike domain, if available.
- [Click a lookalike domain record to view comprehensive details about the entity.](/easm/understanding-lookalike-domain-details)
- [Filter the lookalike domain data based on specific parameters such as Status, Exposure Score, Risk Category, and Deception Method.](/easm/filtering-customizing-lookalike-domains-page)
- [Modify the table and its columns.](/easm/filtering-customizing-lookalike-domains-page)
- [Download the list of all lookalike domains tracked for your seed domains associated with the selected organization into a CSV file.](/easm/downloading-lookalike-domains)
- Search for a lookalike domain by name.
- Select a different organization for which you want to view the lookalike domains. The default organization is automatically selected when the Lookalike Domains page is accessed.
- View the timestamp when the lookalike domain data was last updated.
![The Lookalike Domains page in EASM Admin Portal displaying a list of phishing domains discovered for the legitimate seed domains](/downloads/easm/insights/lookalike-domains/about-lookalike-domains/about-lookalike-domain-page.png)