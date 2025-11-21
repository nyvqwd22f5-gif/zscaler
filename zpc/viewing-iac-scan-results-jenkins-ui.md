# Viewing IaC Scan Results on the Jenkins UI
Source: https://help.zscaler.com/zpc/viewing-iac-scan-results-jenkins-ui
PDF: https://help.zscaler.com/pdf/com/en/1394331.pdf

ZPC generates a graphical report that contains details of the IaC scan results and policy violations detected in a Jenkins job. You can see the report for both single and multibranch pipeline jobs in the Jenkins UI and also download the report as a CSV or PDF file.
To view the IaC scan results in Jenkins:
- On the Jenkins dashboard, click the build number that you submitted for deployment.
- In the left-side navigation, select **Zscaler IaC Scan Results** to view the report.
[See image.](#buildnumber)
If you see an error message in the report, it can be due to one of the following reasons:
- IaC resources are not available
- Parsing error
- IaC scan is not initiated
- IaC scan failed to complete
[See image.](#failedscan)
Resolve the issue and run the IaC scan again.
Report Details
The Jenkins report displays the following information:
- **Project Details**: The project name, build number, build status, and the date and time when the build was scanned.
- **Scan Status**: The total number of scans and status (Passed, Failed, Skipped).
- **Severity**: The overall severity level of the policy violations (Critical, High, Medium, or Low).
- **Export CSV**: Download the report as a CSV file.
- **Export PDF**: Download the report as a PDF file.
- **F****ailed**, **Skipped**, and **Passed** tabs: The number of policies that were failed, skipped, and passed during the IaC scan. For each policy, you can see:
- **Policy Name**: The policy title.
- **Scan Status**: The status of the scan (Failed, Skipped, or Passed).
- **Policy ID**: The unique identification number for the security policy.
- **Severity**: The severity level of the policy violation (Critical, High, Medium, or Low).
- **Resource Details**: Click the arrow next to the **Policy Name** to view:
- **Resource**: The name of the resource.
- **Resource Type**: The type of resource (e.g. AWS S3 bucket).
- **File**: The name of the file that was scanned.
- **Line**: The line within the code that has misconfigurations.
[See image.](#resourcedetails)
[See image.](#jenkinsresults)
[![Select the build number to view the report](/downloads/zpc/iac-integrations/cicd-tools/viewing-iac-scan-results-jenkins-ui/zpc-jenkinsreport-buildnumber.png)
]
[![View the Jenkins scan results](/downloads/zpc/iac-integrations/cicd-tools/viewing-iac-scan-results-jenkins-ui/zpc-jenkinsreport.png?1677159401)
]
[![View the resource details](/downloads/zpc/iac-integrations/cicd-tools/viewing-iac-scan-results-jenkins-ui/zpc-jenkinsreport-resource.png)
]
[![View the error message for failed scan](/downloads/zpc/iac-integrations/cicd-tools/viewing-iac-scan-results-jenkins-ui/zpc-jenkinsreport-scanfailed.png)
]