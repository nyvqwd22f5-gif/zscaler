# Managing Credentials Using API
Source: https://help.zscaler.com/cloud-branch-connector/managing-credentials-using-api
PDF: https://help.zscaler.com/pdf/com/en/1447466.pdf

The Zscaler Cloud & Branch Connector API lets you programmatically manage admin user passwords and API keys. Using the Cloud & Branch Connector API for programmatic management reduces overhead and eliminates misconfigurations.
Programmatically managing credentials typically involves these tasks:
- Obtaining the current API key.
- Regenerating the API key.
- Updating an admin user or service account password.
- Updating Cloud & Branch Connector appliances and client applications.
The following examples illustrate these tasks. For an example that combines all four steps into a single programmatic operation (that can be scheduled), see our GitHub [samples repository](https://github.com/zscaler/zscaler-script-samples).
Getting a List of Current API Keys
To get a list of current API keys, send a GET request to `/apiKeys`. You can then use the API key ID in the response Body to [regenerate the API key](#headerRegeneratingAPIKey) it corresponds to.
For example, in Python:
- [Getting a List of Current API Keys (Python 3.x)](#pythonGettingaListofCurrentAPIKeys)
[]Regenerating an API Key
To regenerate an API key:
- Send a POST request to `/apiKeys/{keyId}/regenerate`, specifying the API key ID (`keyId`) of the API key you want to regenerate.
After an API key is regenerated, any session connections using the previous API key remain valid until session logout or expiry. Any subsequent authentications require the new regenerated API key.
- [Activate the changes to your configuration](/cloud-branch-connector/getting-started-api#activatingconfigurationchanges) by sending a PUT request to `/ecAdminActivateStatus/activate`.
For example, in Python:
- [Regenerating an API Key (Python 3.x)](#pythonRegeneratinganAPIKey)
Updating the API Key Value for Client Applications and Appliances
When you regenerate an API key, you must update deployed Cloud & Branch Connector appliances and any clients to use the new API key. With Cloud Connector appliances, you can update the `api_key` value in AWS Secrets Manager or the `api-key` value in Azure Key Vault. With Branch Connector appliances, you can modify the `api_key` line in the `/etc/cloud/cloud.cfg/userdata.cfg` file of the appliance. If you’re using the Postman REST API Client, you can update your environment variables or the request Body for the POST `/auth` endpoint with the new API key value.
For example, to update the AWS Secrets Manager in Python:
- [Updating the AWS Secrets Manager (Python 3.x)](#pythonUpdatingtheAWSSecretsManager)
Updating an Admin User Password
To update information for a specific admin user:
- Send a POST request to `/passwordChange`, including the following key-value pairs in the request Body:
- `userName`: A string (e.g., `"admin@antest.com"`).
- `oldPassword`: A string (e.g., `"CloudConnector2022!"`).
- `newPassword`: A string (e.g., `"CloudConnector2023!"`).
- [Activate the changes to your configuration](/cloud-branch-connector/getting-started-api#activatingconfigurationchanges) by sending a PUT request to `/ecAdminActivateStatus/activate`.
You can only change the password for the currently logged-in user. You cannot change the password of another user on the system.
For example, in Python:
- [Updating an Admin User Password (Python 3.x)](#pythonUpdatingAdminUserPassword)
[]
# Import Required Modules
import time, requests, json, urllib3, getpass
# Variables
cloudName = input("Cloud Name (e.g., zscloud.net): ")
username = input("Username: ")
password = getpass.getpass("Password: ")
apiKey = input("Current APIKey: ")
# Construct base URL
base_url = "https://connector." + cloudName + "/api/v1/"
# Obfuscate API Key
def obfuscateApiKey (apiKey):
seed = apiKey
now = int(time.time() * 1000)
n = str(now)[-6:]
r = str(int(n) >> 1).zfill(6)
key = ""
for i in range(0, len(str(n)), 1):
key += seed[int(str(n)[i])]
for j in range(0, len(str(r)), 1):
key += seed[int(str(r)[j])+2]
return key
headers = {'Content-Type':'application/json'}
urllib3.disable_warnings(urllib3.exceptions.InsecureRequestWarning)
# Create Session
def createSession(username, password, apiKey):
auth_url = base_url + 'auth'
now = int(time.time() * 1000)
payload = {'apiKey': obfuscateApiKey(apiKey), 'username': username, 'password':password, 'timestamp': now  }
s = requests.Session()
# Added verify=False to bypass ZCC certificate otherwise call may fail with unable to verify SSL cert for certain cloud
r = s.post(auth_url,data=json.dumps(payload),headers=headers, verify=False)
return s
# Get Current API Key ID
def getAPI(s):
api_url = base_url + 'apiKeys'
list_of_apikeys = s.get(api_url, headers=headers)
return list_of_apikeys.json()
f = createSession(username, password, apiKey)
# Print API Key Information
print(getAPI(f))
[]
# Import Required Modules
import time, requests, json, urllib3, getpass
# Variables
cloudName = input("Cloud Name (e.g., zscloud.net): ")
username = input("Username: ")
password = getpass.getpass("Password: ")
apiKey = input("Current APIKey: ")
keyID = input("Current APIKey ID: ")
# Construct base URL
base_url = "https://connector." + cloudName + "/api/v1/"
# Obfuscate API Key
def obfuscateApiKey (apiKey):
seed = apiKey
now = int(time.time() * 1000)
n = str(now)[-6:]
r = str(int(n) >> 1).zfill(6)
key = ""
for i in range(0, len(str(n)), 1):
key += seed[int(str(n)[i])]
for j in range(0, len(str(r)), 1):
key += seed[int(str(r)[j])+2]
return key
headers = {'Content-Type':'application/json'}
urllib3.disable_warnings(urllib3.exceptions.InsecureRequestWarning)
# Create Session
def createSession(username, password, apiKey):
auth_url = base_url + 'auth'
now = int(time.time() * 1000)
payload = {'apiKey': obfuscateApiKey(apiKey), 'username': username, 'password':password, 'timestamp': now  }
s = requests.Session()
# Added verify=False to bypass ZCC certificate otherwise call may fail with unable to verify SSL cert for certain cloud
r = s.post(auth_url,data=json.dumps(payload),headers=headers, verify=False)
return s
# Regenerate API Key
def regenAPI(s):
regen_api_url = base_url + 'apiKeys/' + keyID + '/regenerate'
regen_status = s.post(regen_api_url, headers=headers)
return regen_status
# Activate Changes
def activateChanges(s):
activation_url = base_url + 'ecAdminActivateStatus/activate'
activation_status = s.put(activation_url, headers=headers)
return activation_status
f = createSession(username, password, apiKey)
# Print API Key Information
print("\nRegeneration Status")
print(regenAPI(f).text)
# Display activation status
print("\nActivation Status:")
print(activateChanges(f).text)
[]
# Import Required Modules
import json
from boto3 import Session
# Variables
aws_region_name = input("Enter the AWS Region where Secrets Manager exists (e.g., us-west-2): ")
aws_access_id = input("Enter your AWS Access Key: ")
aws_secret_key = input("Enter your AWS Secret Key: ")
aws_secret_name = input("Enter your AWS Secrets Manager Object Name (e.g., ZS/CC/credentials/yourSecretName): ")
keyValue = input("Enter the updated API Key value: ")
# Initialize session client
session = Session(
aws_access_key_id=aws_access_id,
aws_secret_access_key=aws_secret_key,
region_name=aws_region_name
)
client = session.client(service_name="secretsmanager")
# Get original Secrets Object
original_secret = client.get_secret_value(SecretId=aws_secret_name)
# Convert SecretString to dictionary
updated_secret = json.loads(original_secret['SecretString'])
# Update the dictionary with new value
updated_secret.update({"api_key": keyValue})
# Update the secret key
client.update_secret(SecretId=aws_secret_name, SecretString=str(json.dumps(updated_secret)))
print("Update Complete")
[]
# Import Required Modules
import time, requests, json, urllib3, secrets, string, getpass
# Variables
cloudName = input("Cloud Name (e.g., zscloud.net): ")
username = input("Username: ")
password = getpass.getpass("Current Password: ")
updPassword = getpass.getpass("NEW Password: ")
apiKey = input("Current APIKey: ")
# Construct base URL
base_url = "https://connector." + cloudName + "/api/v1/"
# Obfuscate API Key
def obfuscateApiKey (apiKey):
seed = apiKey
now = int(time.time() * 1000)
n = str(now)[-6:]
r = str(int(n) >> 1).zfill(6)
key = ""
for i in range(0, len(str(n)), 1):
key += seed[int(str(n)[i])]
for j in range(0, len(str(r)), 1):
key += seed[int(str(r)[j])+2]
return key
headers = {'Content-Type':'application/json'}
urllib3.disable_warnings(urllib3.exceptions.InsecureRequestWarning)
# Create Session
def createSession(username, password, apiKey):
auth_url = base_url + 'auth'
now = int(time.time() * 1000)
payload = {'apiKey':obfuscateApiKey(apiKey), 'username':username, 'password':password, 'timestamp':now  }
s = requests.Session()
# Added verify=False to bypass ZCC certificate otherwise call may fail with unable to verify SSL cert for certain cloud
r = s.post(auth_url,data=json.dumps(payload),headers=headers, verify=False)
return s
# Update Password
def updatePassword(s):
pass_url = base_url + 'passwordChange'
payload = {'userName':username,'oldPassword':password,'newPassword':updPassword}
r = s.post(pass_url,data=json.dumps(payload, separators=(',', ':')),headers=headers, verify=False)
# If successful, returns HTTP status code 204 with no payload
return r
# Activate Changes
def activateChanges(s):
activation_url = base_url + 'ecAdminActivateStatus/activate'
activation_status = s.put(activation_url, headers=headers)
return activation_status
f = createSession(username, password, apiKey)
# Print update status
print("\nPassword Update Status")
print(updatePassword(f))
# Display activation status
print("\nActivation Status:")
print(activateChanges(f).text)

## Contents
- **API Developer & Reference Guide**
  - [Getting Started](/cloud-branch-connector/getting-started-cloud-branch-connector-api)
  - [Configuring the Postman REST API Client](/cloud-branch-connector/configuring-postman-rest-api-client)
  - [API Response Codes and Error Messages](/cloud-branch-connector/api-response-codes-and-error-messages)
  - [Understanding Rate Limits](/cloud-branch-connector/understanding-rate-limits)
  - **Reference Guide**
    - [Activation](/cloud-branch-connector/activation)
    - [Admin and Role Management](/cloud-branch-connector/admin-and-role-management)
    - [Authentication](/cloud-branch-connector/authentication)
    - [Cloud & Branch Connector Groups](/cloud-branch-connector/cloud-branch-connector-groups)
    - [Forwarding Gateways](/cloud-branch-connector/forwarding-gateways)
    - [Location Management](/cloud-branch-connector/location-management)
    - [Partner Integrations](/cloud-branch-connector/partner-integrations)
    - [Policy Management](/cloud-branch-connector/policy-management)
    - [Policy Resources](/cloud-branch-connector/policy-resources)
    - [Provisioning](/cloud-branch-connector/provisioning)
    - [API Rate Limit Summary](/cloud-branch-connector/api-rate-limit-summary)
  - **Working with APIs**
    - [Deleting Cloud & Branch Connectors Using API](/cloud-branch-connector/deleting-cloud-branch-connectors-using-api)
    - [Managing Admin Users and Roles Using API](/cloud-branch-connector/managing-admin-users-and-roles-using-api)
    - [Managing Credentials Using API](/cloud-branch-connector/managing-credentials-using-api)