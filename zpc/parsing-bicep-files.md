# Parsing Bicep Files
Source: https://help.zscaler.com/zpc/parsing-bicep-files
PDF: https://help.zscaler.com/pdf/com/en/1420196.pdf

ZPC realizes that organizations use various types of IaC templates (e.g., JSON, YAML, ARM, Cloud Formation Template, Bicep, etc.) in their infrastructure. To support the scanning of all types of templates for security configuration violations, ZPC provides support for parsing Bicep files into Azure Resource Manager (ARM) templates.
Bicep is a declarative domain specific language (DSL) that is used to provision Azure resources. To learn more, see the [Microsoft documentation](https://learn.microsoft.com/en-us/azure/azure-resource-manager/bicep/overview?tabs=bicep).
Known Limitations
Although ZPC supports the parsing of Bicep files, there are a few limitations:
- ZPC supports the parsing of Bicep files only in GitHub Actions and Azure Pipelines.
- While converting a Bicep file, you must provide the folder path where the Bicep file resides and not the directory path because the Bicep CLI does not recognize the directory path.
- After the Bicep file is converted to an ARM template (JSON), the policy violations are shown based on the line numbers within the ARM template and not the line numbers within the Bicep file.
- To scan and deploy a parameter file along with the Bicep file, see the [Microsoft documentation](https://learn.microsoft.com/en-us/azure/azure-resource-manager/bicep/parameter-files#deploy-bicep-file-with-parameter-file).
Installing Azure Bicep CLI
You need to install and use the Azure Bicep command-line interface (CLI) for compiling the Bicep files into ARM templates. You can also install and use the Azure command-line interface (CLI) which automatically installs the Bicep CLI.
To parse a Bicep file with Azure Bicep CLI:
- [Install the Azure Bicep CLI](https://learn.microsoft.com/en-us/azure/azure-resource-manager/bicep/install).
- Open the command prompt, and go to the folder that contains the Bicep file.
- Run the following command to convert the Bicep file to JSON:
`bicep build main.bicep`
The converted JSON file can be deployed and scanned for misconfigurations.
Scanning Bicep Files with CLI Scanner
After you've converted the Bicep file to an ARM template (JSON), you can use the Zscaler CLI scanner to scan the file for misconfigurations.
To scan the JSON file:
- Open the command prompt.
- Run the following command to scan the folder that contains the JSON file.
zscanner scan -d /<folder name>/<folder path>
- Run the following command to scan the specific JSON file.
zscanner scan -f file <filename>
The scan results are displayed as output.
Parsing Bicep Files
You can use either GitHub Actions or Azure DevOps to parse your Bicep files.
- [Parse Bicep Files Using GitHub Actions](#githubactions)
- [Parse Bicep Files Using Azure DevOps](#azuredevops)
[]Prerequisites
Before parsing the Bicep files, you must have:
- An Azure account with an active subscription.
- A GitHub account.
- A GitHub repository to store your Bicep files and your workflow files.
To parse the Bicep file in GitHub Actions:
- Log in to your GitHub account.
- Select **Actions** from the top menu, then click on **set up a workflow yourself**.
[See image.](#workflow)
GitHub Actions uses YAML syntax to define the workflow. Each workflow is stored as a separate YAML file in your code repository, in a directory named `.github/workflows`.
- Rename the `main.yml` file, if required.
- Edit the YAML file:
name: Bicep Build and Scan
on: push
jobs:
build_and_scan:
name: Build and Scan
runs-on: ubuntu-latest
steps:
- name : Code Checkout
uses: actions/checkout@v2
- name : Azure Login
uses: azure/login@v1
with:
creds: ${{ secrets.AZURE_CREDENTIALS }}
- name: Bicep Build
uses: Azure/bicep-build-action@v1.0.0
with:
bicepFilePath: ./main.bicep
outputFilePath: ./azuredeploy.json
- name : Zscaler IAC Scan
uses : ZscalerCWP/Zscaler-IaC-Action@main
id : zscaler-iac-scan
with:
client_id : ${{ secrets.ZSCANNER_CLIENT_ID }}
client_secret : ${{ secrets.ZSCANNER_CLIENT_SECRET }}
fail_build : 'true'
output_format : 'human+github-sarif'
region : 'CUSTOM'
log_level : 'debug'
iac_file : 'azuredeploy.json'
Replace the `ZSCANNER_CLIENT_ID` and `ZSCANNER_CLIENT_SECRET` values with the values you copied and saved while onboarding the GitHub account on the ZPC Admin Portal. To learn more, see [Configuring IaC Scan for GitHub Actions](/zpc/configuring-iac-scan-github-actions).
- Click **Save**.
- Click **Start commit**
This action starts the workflow and the Bicep file is converted to a JSON file and scanned for any misconfigurations.
[]Prerequisites
Before parsing the Bicep files, you must have:
- An Azure subscription.
- An Azure DevOps organization.
- A Bicep file in a repository.
To parse the Bicep file in Azure DevOps:
- Sign in to your Azure DevOps organization.
- Select **New project**. To learn more, see the [Microsoft documentation](https://learn.microsoft.com/en-us/azure/devops/organizations/projects/create-project?view=azure-devops&tabs=browser).
- Enter the **Project name**.
- Select **Private Project**.
- Under **Advanced**, select the required version control system (Git or Azure Repos) and the process.
- Click **Create**.
[See image.](#project)
- Open your project and select the repository that has the workflow.
- Install and configure the Zscaler IaC Scan in this repository. To learn more, see [Configuring IaC Scan for Azure Repos](/zpc/configuring-iac-scan-azure-repos).
- Create an Azure Pipeline job. To learn more, see the [Microsoft documentation](https://learn.microsoft.com/en-us/azure/devops/pipelines/create-first-pipeline?view=azure-devops&tabs=java%2Ctfs-2018-2%2Cbrowser).
- Edit the YAML file.
trigger:
- main
pool:
vmImage: ubuntu-latest
steps:
- script: az bicep build --file src/main.bicep --outfile src/azuredeploy.json
displayName: 'Compile Bicep file'
- task: ZscalerIaCScan@1
inputs:
region: 'CUSTOM'
clientId: ZSCANNER_CLIENT_ID
clientSecret: ZSCANNER_CLIENT_SECRET
iacfile: 'src/azuredeploy.json'
failBuild: true
Replace the `ZSCANNER_CLIENT_ID` and `ZSCANNER_CLIENT_SECRET` values with the values you copied and saved while onboarding the Azure account on the ZPC Admin Portal. To learn more, see [Configuring IaC Scan for Azure Pipelines](/zpc/configuring-iac-scan-azure-pipelines).
- Click **Save**.
When you run the Pipeline job, the Bicep file is converted to a JSON file and scanned for misconfigurations and policy violations.
You can compile multiple Bicep files in a single workflow and scan the entire directory.
[![Create a new GitHub workflow](/downloads/zpc/version-control-cicd-systems/managing-iac-scannng/parsing-bicep-files/zpc-github-new-wrkflow.png)
]
[![Create a new project in Azure DevOps](/downloads/zpc/version-control-cicd-systems/managing-iac-scannng/parsing-bicep-files/zpc-azure-createproject.png)
]