# Modifying Lookalike Domain Status
Source: https://help.zscaler.com/easm/modifying-lookalike-domain-status
PDF: https://help.zscaler.com/pdf/com/en/1508151.pdf

EASM supports various statuses for [lookalike domains](/easm/about-lookalike-domains) to help you effectively track and manage these domains and gain visibility into the threats posed by phishing domains detected for your legitimate domains. The following statuses are supported for lookalike domains:
- **Not Verified**: All lookalike domains initially detected by EASM for your legitimate seed domains are automatically tagged with the label "Not Verified".
- **Verified**: Lookalike domains are manually investigated and verified for risks. An example could be a high-risk domain that is verified to be a phishing site.
- **Risk Accepted**: Represents that the risk is deemed acceptable. An example could be a domain that is not registered yet and can be put on the watchlist.
- **Resolved**: Lookalike domains for which remediation steps are taken or are planned can be marked as resolved. For example, if a fake domain is taken offline or suspended by the registrar after reporting and the threat is eliminated, it can be marked as resolved. However, if the lookalike domain is discovered again in a subsequent scan, then it is marked as "Not Verified".
- **Disputed**: If the manual verification of a lookalike domain turns out differently from the original detection, the lookalike domain can be moved to the Disputed status, indicating that it might be a false positive.
To modify the status of a lookalike domain:
The data on the Lookalike Domains page is specific to the organization selected on the top-right corner. Before you begin, ensure that the desired organization is selected.
- Go to the Lookalike Domains page.
-
Click the lookalike domain record for which you want to modify the status.
The **Lookalike Domain Details** drawer opens on the right side.
-
In the **Lookalike Domain Details** drawer, you can modify the domain's status by using the **Status** drop-down menu.
[See image.](#lookalike-domain-status)
A **Status Update Confirmation** window appears.
- In the **Status Update Confirmation** window, enter the reason for modifying the lookalike domain's status which can be useful for auditing trails and general tracking purposes.
- Click **Accept**.
[]![Changing lookalike domain status in the EASM Admin Portal](/downloads/easm/insights/lookalike-domains/changing-lookalike-domain-status/changing-lookalike-domain-status.png)