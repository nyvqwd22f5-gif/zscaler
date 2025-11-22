# Managing Admin Users and Roles Using API
Source: https://help.zscaler.com/cloud-branch-connector/managing-admin-users-and-roles-using-api
PDF: https://help.zscaler.com/pdf/com/en/1447456.pdf

[Admin and Role Management API](/cloud-branch-connector/admin-and-role-management) resources allow you to retrieve admin user and role information to configure the level of access admins have in the Zscaler Cloud & Branch Connector Admin Portal and API. These resources also allow you to add, update, or delete admin users and roles within your organization. To learn more about admins and roles, see [Adding Admins](/cloud-branch-connector/adding-admins) and [Adding Admin Roles](/cloud-branch-connector/adding-admin-roles).
Getting a List of Admin Users
To get a list of admin users, send a GET request to `/adminUsers`. You can use the following optional parameters:
- `page`: Specify a page offset.
- `pageSize`: Specify the page length, up to a limit of 1000.
For example, in Python:
- [Getting a List of Admin Users (Python 3.x):](#pythonGettingaListofAdminUsers)
Adding an Admin User
To add an admin user:
- Send a POST request to `/adminUsers` and use the following key-value pairs in the Body:
- `userName`: A string (e.g., `"Admin User"`).
- `email`: A string (e.g., `"admin@antest.com"`).
- `loginName`: A string (e.g., `"admin@antest.com"`).
- `password`: A string (e.g., "`CloudConnector2023!"`).
- `role`: An object, the role ID (`id`) and name (`name`) to assign to this user: (e.g., "`{"id”:"12345", "name":"Super Admin"}"`).
- [Activate the changes to your configuration](/cloud-branch-connector/getting-started-api#activatingconfigurationchanges) by sending a PUT request to `/ecAdminActivateStatus/activate`.
For example, in Python:
- [Adding an Admin User (Python 3.x)](#pythonAddinganAdminUser)
Updating Information for a Specific Admin User
To update information for a specific admin user:
- Get information about a specific admin user by sending a GET request to `/adminUsers/{userId}`, specifying the user ID (`userId`).
- Modify the user's information by sending a PUT request to `/adminUsers/{userId}`, specifying the user ID (`userId`) and updating the following key-value pairs in the Body:
The following key-value pairs are required, even if not updated.
- `userName`: A string (e.g., `"Admin User"`).
- `email`: A string (e.g., `"admin@antest.com"`).
- `loginName`: A string (e.g., `"admin@antest.com"`).
- `password`: A string (e.g., "`CloudConnector2023!"`).
- `role`: An object, the role ID (`id`) and name (`name`) to assign to this user: (e.g., "`{"id":"12345", "name":"Super Admin"}"`).
- [Activate the changes to your configuration](/cloud-branch-connector/getting-started-api#activatingconfigurationchanges) by sending a PUT request to `/ecAdminActivateStatus/activate`.
For example, in Python:
- [Updating Information for a Specific Admin User (Python 3.x)](#pythonUpdatingInfoForaSpecificAdminUser)
Deleting an Admin User
To delete a specific admin user:
- Send a DELETE request to `/adminUsers/{userId}`, specifying the user ID (`userId`).
- [Activate the changes to your configuration](/cloud-branch-connector/getting-started-api#activatingconfigurationchanges) by sending a PUT request to `/ecAdminActivateStatus/activate`.
For example, in Python:
- [Deleting an Admin User (Python 3.x)](#pythonDeletingaSpecificAdminUser)
Getting a List of Admin Roles
To get a list of admin roles, send a GET request to `/adminRoles`.
For example, in Python:
- [Getting a List of Admin Roles (Python 3.x)](#pythonGettingaListofAdminRoles)
Getting an Admin Role by Role ID
To get information for a specific admin role, send a GET request to `/adminRoles`, specifying the admin role ID (`roleId`) in the `id` query parameter: `/adminRoles?id={roleId}`.
For example, in Python:
- [Getting an Admin Role by Role ID (Python 3.x)](#pythonGettinganAdminRoleByRoleID)
Adding an Admin Role
To add an admin role:
- Send a POST request to `/adminRoles`, including the following required key-value pairs in the Body with appropriate values for the role:
- `name`: A string (e.g., `"Admin Role"`).
- `rank`: An integer. This value must be set to `"7"`
- `policyAccess`: A string. This value must be set to `"NONE"`
- `alertingAccess`: A string. This value must be set to `"READ_ONLY"`
- `dashboardAccess`: A string. This value must be set to `"NONE"`
- `reportAccess`: A string. This value must be set to `"NONE"`
- `analysisAccess`: A string. This value must be set to `"NONE"`
- `usernameAccess`: A string. This value must be set to `"NONE"`
- `deviceInfoAccess`: A string. This value must be set to `"NONE"`
- `adminAcctAccess`: A string. This value must be set to `"READ_WRITE"`
- `roleType`: A string. This value must be set to `"EDGE_CONNECTOR_ADMIN"`
- `featurePermissions`: An object containing name-value pairs for the feature (`APIKEY_MANAGEMENT`, `EDGE_CONNECTOR_CLOUD_PROVISIONING`, `EDGE_CONNECTOR_LOCATION_MANAGEMENT`, `EDGE_CONNECTOR_DASHBOARD`, `EDGE_CONNECTOR_FORWARDING`, `EDGE_CONNECTOR_TEMPLATE`, `REMOTE_ASSISTANCE_MANAGEMENT`, `EDGE_CONNECTOR_ADMIN_MANAGEMENT`, `EDGE_CONNECTOR_NSS_CONFIGURATION`) and its permission (`READ_ONLY`, `READ_WRITE`, `NONE`) to assign to this role (e.g., "`{"EDGE_CONNECTOR_CLOUD_PROVISIONING":"READ_WRITE", "EDGE_CONNECTOR_LOCATION_MANAGEMENT":"READ_WRITE"}"`)
- [Activate the changes to your configuration](/cloud-branch-connector/getting-started-api#activatingconfigurationchanges) by sending a PUT request to `/ecAdminActivateStatus/activate`.
For example, in Python:
- [Adding an Admin Role (Python 3.x)](#pythonAddinganAdminRole)
Updating Information for a Specific Admin Role
To update information for a specific admin role:
- Get information about a specific admin role by sending a GET request to `/adminRoles`, specifying the admin role ID (`roleId`) in the `id` query parameter: `/adminRoles?id={roleId}`
- Modify the admin role by sending a PUT request to `/adminRoles/{roleId}`, specifying the admin role ID (`roleId`) and including the following required key-value pairs in the Body with appropriate values for the role:
- `name`: A string (e.g., `"Admin Role"`).
- `rank`: An integer. This value must be set to `"7"`
- `policyAccess`: A string. This value must be set to `"NONE"`
- `alertingAccess`: A string. This value must be set to `"READ_ONLY"`
- `dashboardAccess`: A string. This value must be set to `"NONE"`
- `reportAccess`: A string. This value must be set to `"NONE"`
- `analysisAccess`: A string. This value must be set to `"NONE"`
- `usernameAccess`: A string. This value must be set to `"NONE"`
- `deviceInfoAccess`: A string. This value must be set to `"NONE"`
- `adminAcctAccess`: A string. This value must be set to `"READ_WRITE"`
- `roleType`: A string. This value must be set to `"EDGE_CONNECTOR_ADMIN"`
- `featurePermissions`: An object containing name-value pairs for the feature (`APIKEY_MANAGEMENT`, `EDGE_CONNECTOR_CLOUD_PROVISIONING`, `EDGE_CONNECTOR_LOCATION_MANAGEMENT`, `EDGE_CONNECTOR_DASHBOARD`, `EDGE_CONNECTOR_FORWARDING`, `EDGE_CONNECTOR_TEMPLATE`, `REMOTE_ASSISTANCE_MANAGEMENT`, `EDGE_CONNECTOR_ADMIN_MANAGEMENT`, `EDGE_CONNECTOR_NSS_CONFIGURATION`) and its permissions (`READ_ONLY`, `READ_WRITE`, `NONE`) to assign to this role (e.g., "`{"EDGE_CONNECTOR_CLOUD_PROVISIONING":"READ_WRITE", "EDGE_CONNECTOR_LOCATION_MANAGEMENT":"READ_WRITE"}"`)
- [Activate the changes to your configuration](/cloud-branch-connector/getting-started-api#activatingconfigurationchanges) by sending a PUT request to `/ecAdminActivateStatus/activate`.
For example, in Python:
- [Updating Information for a Specific Admin Role (Python 3.x)](#pythonUpdatingInfoForaSpecificAdminRole)
Deleting an Admin Role
To delete a specific role:
- Send a DELETE request to` /adminRoles/{roleId}`, specifying the role ID (`roleId`).
- [Activate the changes to your configuration](/cloud-branch-connector/getting-started-api#activatingconfigurationchanges) by sending a PUT request to `/ecAdminActivateStatus/activate`.
For example, in Python:
- [Deleting an Admin Role (Python 3.x)](#pythonDeletinganAdminRole)
[]
# Import Required Modules
import time, requests, json, urllib3, getpass
# Variables
cloudName = input("Cloud Name (e.g., zscloud.net): ")
username = input("Username: ")
password = getpass.getpass("Password: ")
apiKey = input("APIKey: ")
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
def createSessionCC(username, password, apiKey):
auth_url = base_url + 'auth'
now = int(time.time() * 1000)
payload = {'apiKey':obfuscateApiKey(apiKey), 'username':username, 'password':password, 'timestamp':now  }
s = requests.Session()
# Added verify=False to bypass ZCC certificate otherwise call may fail with unable to verify SSL cert for certain cloud
r = s.post(auth_url,data=json.dumps(payload),headers=headers, verify=False)
return s
# Get Users
def getAdminUsers(s):
user_url = base_url + 'adminUsers'
list_of_users = s.get(user_url, headers=headers)
return list_of_users.json()
f = createSessionCC(username, password, apiKey)
# Print retrieved Admin Users
print(str(getAdminUsers(f)))
[]
# Import Required Modules
import time, requests, json, urllib3, getpass
# Variables
cloudName = input("Cloud Name (e.g., zscloud.net): ")
username = input("Username: ")
password = getpass.getpass("Password: ")
apiKey = input("APIKey: ")
newUsername = input("Enter the new user's name (e.g. Admin User): ")
newLoginName = input("Enter the new user's login ID (e.g. admin@zscaler.com): ")
newPassword = getpass.getpass("Enter the new user's password: ")
newEmail = input("Enter the new user's email address (e.g. admin@zscaler.com): ")
newRole = input("Enter the new user's role assignment (e.g. Super Admin): ")
newRoleID = input("Enter the role ID associated with the role assigned to this user: ")
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
def createSessionCC(username, password, apiKey):
auth_url = base_url + 'auth'
now = int(time.time() * 1000)
payload = {'apiKey':obfuscateApiKey(apiKey), 'username':username, 'password':password, 'timestamp':now  }
s = requests.Session()
# Added verify=False to bypass ZCC certificate otherwise call may fail with unable to verify SSL cert for certain cloud
r = s.post(auth_url,data=json.dumps(payload),headers=headers, verify=False)
return s
# Create Admin User
def createAdmin(s):
add_url = base_url + 'adminUsers'
payload = {'userName':newUsername, 'loginName':newLoginName, 'password':newPassword, 'email':newEmail, 'role':{'id': newRoleID, 'name': newRole}}
create_status = s.post(add_url,data=json.dumps(payload, separators=(',', ':')),headers=headers)
return create_status
# Activate Changes
def activateChanges(s):
activation_url = base_url + 'ecAdminActivateStatus/activate'
activation_status = s.put(activation_url, headers=headers)
return activation_status
f = createSessionCC(username, password, apiKey)
# Add user and display creation status
print("\nCreation Status:")
print(createAdmin(f).text)
# Display activation status
print("\nActivation Status:")
print(activateChanges(f).text)
[]
# Import Required Modules
import time, requests, json, urllib3, getpass
# Variables
cloudName = input("Cloud Name (e.g., zscloud.net): ")
username = input("Username: ")
password = getpass.getpass("Password: ")
apiKey = input("APIKey: ")
updUsername = input("Enter the user name of the Admin to update (e.g., Admin User): ")
userID = input("Enter the user ID of the Admin to update (e.g., 12345): ")
updPassword = getpass.getpass("Enter the Admin user's updated password: ")
updLoginName = input("Enter the Admin user's updated login name (e.g., admin@zscaler.com): ")
updEmail = input("Enter the Admin user's updated email address (e.g., admin@zscaler.com): ")
updRole = input("Enter the Admin user's updated role assignment (e.g., Super Admin): ")
updRoleID = input("Enter the role ID associated with the role assigned to the Admin user in the previous step: ")
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
def createSessionCC(username, password, apiKey):
auth_url = base_url + 'auth'
now = int(time.time() * 1000)
payload = {'apiKey':obfuscateApiKey(apiKey), 'username':username, 'password':password, 'timestamp':now  }
s = requests.Session()
# Added verify=False to bypass ZCC certificate otherwise call may fail with unable to verify SSL cert for certain cloud
r = s.post(auth_url,data=json.dumps(payload),headers=headers, verify=False)
return s
# Update Admin User
def updateAdmin(s):
add_url = base_url + 'adminUsers/' + userID
payload = {'userName':updUsername, 'loginName':updLoginName, 'password':updPassword, 'email':updEmail, 'role':{'id': updRoleID, 'name': updRole}}
create_status = s.put(add_url,data=json.dumps(payload, separators=(',', ':')),headers=headers)
return create_status
# Activate Changes
def activateChanges(s):
activation_url = base_url + 'ecAdminActivateStatus/activate'
activation_status = s.put(activation_url, headers=headers)
return activation_status
f = createSessionCC(username, password, apiKey)
# Add user and display creation status
print("\nCreation Status:")
print(updateAdmin(f).text)
# Display activation status
print("\nActivation Status:")
print(activateChanges(f).text)
[]
# Import Required Modules
import time, requests, json, urllib3, getpass
# Variables
cloudName = input("Cloud Name (e.g., zscloud.net): ")
username = input("Username: ")
password = getpass.getpass("Password: ")
apiKey = input("APIKey: ")
userID = input("Enter the user ID of the Admin to delete (e.g., 12345): ")
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
def createSessionCC(username, password, apiKey):
auth_url = base_url + 'auth'
now = int(time.time() * 1000)
payload = {'apiKey':obfuscateApiKey(apiKey), 'username':username, 'password':password, 'timestamp':now  }
s = requests.Session()
# Added verify=False to bypass ZCC certificate otherwise call may fail with unable to verify SSL cert for certain cloud
r = s.post(auth_url,data=json.dumps(payload),headers=headers, verify=False)
return s
# Delete Admin User
def deleteAdmin(s):
delete_url = base_url + 'adminUsers/' + userID
delete_admin = s.delete(delete_url,headers=headers)
return delete_admin
# Activate Changes
def activateChanges(s):
activation_url = base_url + 'ecAdminActivateStatus/activate'
activation_status = s.put(activation_url, headers=headers)
return activation_status
f = createSessionCC(username, password, apiKey)
delete_result = deleteAdmin(f)
# Display deletion status
print("\nDeletion Status:")
print(delete_result)
# Display activation status
print("\nActivation Status:")
print(activateChanges(f).text)
[]
# Import Required Modules
import time, requests, json, urllib3, getpass
# Variables
cloudName = input("Cloud Name (e.g., zscloud.net): ")
username = input("Username: ")
password = getpass.getpass("Password: ")
apiKey = input("APIKey: ")
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
def createSessionCC(username, password, apiKey):
auth_url = base_url + 'auth'
now = int(time.time() * 1000)
payload = {'apiKey':obfuscateApiKey(apiKey), 'username':username, 'password':password, 'timestamp':now  }
s = requests.Session()
# Added verify=False to bypass ZCC certificate otherwise call may fail with unable to verify SSL cert for certain cloud
r = s.post(auth_url,data=json.dumps(payload),headers=headers, verify=False)
return s
# Get Admin Roles
def getAdminRoles(s):
user_url = base_url + 'adminRoles'
list_of_users = s.get(user_url, headers=headers)
return list_of_users.json()
f = createSessionCC(username, password, apiKey)
# Print retrieved Admin Roles
print(str(getAdminRoles(f)))
[]
# Import Required Modules
import time, requests, json, urllib3, getpass
# Variables
cloudName = input("Cloud Name (e.g., zscloud.net): ")
username = input("Username: ")
password = getpass.getpass("Password: ")
apiKey = input("APIKey: ")
roleID = input("Admin Role ID: ")
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
def createSessionCC(username, password, apiKey):
auth_url = base_url + 'auth'
now = int(time.time() * 1000)
payload = {'apiKey':obfuscateApiKey(apiKey), 'username':username, 'password':password, 'timestamp':now  }
s = requests.Session()
# Added verify=False to bypass ZCC certificate otherwise call may fail with unable to verify SSL cert for certain cloud
r = s.post(auth_url,data=json.dumps(payload),headers=headers, verify=False)
return s
# Get Admin Roles
def getAdminRoles(s):
user_url = base_url + 'adminRoles?id=' + roleID
list_of_users = s.get(user_url, headers=headers)
return list_of_users.json()
f = createSessionCC(username, password, apiKey)
# Print retrieved Admin Roles
print(str(getAdminRoles(f)))
[]
# Import Required Modules
import time, requests, json, urllib3, getpass
# Variables
cloudName = input("Cloud Name (e.g., zscloud.net): ")
username = input("Username: ")
password = getpass.getpass("Password: ")
apiKey = input("APIKey: ")
newRoleName = input("Enter the new role name: ")
apiMgmt = input("API Key Management Permission? Please answer READ_ONLY, READ_WRITE, or NONE (case sensitive): ")
cloudProv = input("Cloud Connector Provisioning Permission? Please answer READ_ONLY, READ_WRITE, or NONE (case sensitive): ")
locMgmt = input("Location Management Permission? Please answer READ_ONLY, READ_WRITE, or NONE (case sensitive): ")
ecDash = input("Dashboard Access Permission? Please answer READ_ONLY, or NONE (case sensitive): ")
ecFwd = input("Traffic Forwarding Policy Permission? Please answer READ_ONLY, READ_WRITE, or NONE (case sensitive): ")
ecTmplt = input("Location Template Permission? Please answer READ_ONLY, READ_WRITE, or NONE (case sensitive): ")
remoteMgmt = input("Remote Management Permission? Please answer READ_WRITE, or NONE (case sensitive): ")
adminMgmt = input("Admin User Management Permission? Please answer READ_ONLY, READ_WRITE, or NONE (case sensitive): ")
nssMgmt = input("NSS Logging Configuration Permission? Please answer READ_WRITE, or NONE (case sensitive): ")
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
def createSessionCC(username, password, apiKey):
auth_url = base_url + 'auth'
now = int(time.time() * 1000)
payload = {'apiKey':obfuscateApiKey(apiKey), 'username':username, 'password':password, 'timestamp':now  }
s = requests.Session()
# Added verify=False to bypass ZCC certificate otherwise call may fail with unable to verify SSL cert for certain cloud
r = s.post(auth_url,data=json.dumps(payload),headers=headers, verify=False)
return s
# Create Admin Role
def createRole(s):
add_url = base_url + 'adminRoles'
payload = {
'rank':'7',
'name':newRoleName,
'policyAccess':'NONE',
'alertingAccess':'READ_ONLY',
'dashboardAccess':'NONE',
'reportAccess':'NONE',
'analysisAccess':'NONE',
'usernameAccess':'NONE',
'deviceInfoAccess':'NONE',
'adminAcctAccess':'READ_WRITE',
'featurePermissions':{
'APIKEY_MANAGEMENT':apiMgmt,
'EDGE_CONNECTOR_CLOUD_PROVISIONING':cloudProv,
'EDGE_CONNECTOR_LOCATION_MANAGEMENT':locMgmt,
'EDGE_CONNECTOR_DASHBOARD':ecDash,
'EDGE_CONNECTOR_FORWARDING':ecFwd,
'EDGE_CONNECTOR_TEMPLATE':ecTmplt,
'REMOTE_ASSISTANCE_MANAGEMENT':remoteMgmt,
'EDGE_CONNECTOR_ADMIN_MANAGEMENT':adminMgmt,
'EDGE_CONNECTOR_NSS_CONFIGURATION':nssMgmt
},
'roleType':'EDGE_CONNECTOR_ADMIN'
}
create_status = s.post(add_url,data=json.dumps(payload, separators=(',', ':')),headers=headers)
return create_status
# Activate Changes
def activateChanges(s):
activation_url = base_url + 'ecAdminActivateStatus/activate'
activation_status = s.put(activation_url, headers=headers)
return activation_status
f = createSessionCC(username, password, apiKey)
# Add role and display creation status
print("\nCreation Status:")
print(createRole(f).text)
# Display activation status
print("\nActivation Status:")
print(activateChanges(f).text)
[]
# Import Required Modules
import time, requests, json, urllib3, getpass
# Variables
cloudName = input("Cloud Name (e.g., zscloud.net): ")
username = input("Username: ")
password = getpass.getpass("Password: ")
apiKey = input("APIKey: ")
roleName = input("Enter the role name to update: ")
roleID = input("Enter the role ID to update: ")
apiMgmt = input("API Key Management Permission? Please answer READ_ONLY, READ_WRITE, or NONE (case sensitive): ")
cloudProv = input("Cloud Connector Provisioning Permission? Please answer READ_ONLY, READ_WRITE, or NONE (case sensitive): ")
locMgmt = input("Location Management Permission? Please answer READ_ONLY, READ_WRITE, or NONE (case sensitive): ")
ecDash = input("Dashboard Access Permission? Please answer READ_ONLY, or NONE (case sensitive): ")
ecFwd = input("Traffic Forwarding Policy Permission? Please answer READ_ONLY, READ_WRITE, or NONE (case sensitive): ")
ecTmplt = input("Location Template Permission? Please answer READ_ONLY, READ_WRITE, or NONE (case sensitive): ")
remoteMgmt = input("Remote Management Permission? Please answer READ_WRITE, or NONE (case sensitive): ")
adminMgmt = input("Admin User Management Permission? Please answer READ_ONLY, READ_WRITE, or NONE (case sensitive): ")
nssMgmt = input("NSS Logging Configuration Permission? Please answer READ_WRITE, or NONE (case sensitive): ")
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
def createSessionCC(username, password, apiKey):
auth_url = base_url + 'auth'
now = int(time.time() * 1000)
payload = {'apiKey':obfuscateApiKey(apiKey), 'username':username, 'password':password, 'timestamp':now  }
s = requests.Session()
# Added verify=False to bypass ZCC certificate otherwise call may fail with unable to verify SSL cert for certain cloud
r = s.post(auth_url,data=json.dumps(payload),headers=headers, verify=False)
return s
# Update Admin Role
def updateRole(s):
add_url = base_url + 'adminRoles/' + roleID
payload = {
'rank':'7',
'name':roleName,
'policyAccess':'NONE',
'alertingAccess':'READ_ONLY',
'dashboardAccess':'NONE',
'reportAccess':'NONE',
'analysisAccess':'NONE',
'usernameAccess':'NONE',
'deviceInfoAccess':'NONE',
'adminAcctAccess':'READ_WRITE',
'featurePermissions':{
'APIKEY_MANAGEMENT':apiMgmt,
'EDGE_CONNECTOR_CLOUD_PROVISIONING':cloudProv,
'EDGE_CONNECTOR_LOCATION_MANAGEMENT':locMgmt,
'EDGE_CONNECTOR_DASHBOARD':ecDash,
'EDGE_CONNECTOR_FORWARDING':ecFwd,
'EDGE_CONNECTOR_TEMPLATE':ecTmplt,
'REMOTE_ASSISTANCE_MANAGEMENT':remoteMgmt,
'EDGE_CONNECTOR_ADMIN_MANAGEMENT':adminMgmt,
'EDGE_CONNECTOR_NSS_CONFIGURATION':nssMgmt
},
'roleType':'EDGE_CONNECTOR_ADMIN'
}
create_status = s.put(add_url,data=json.dumps(payload, separators=(',', ':')),headers=headers)
return create_status
# Activate Changes
def activateChanges(s):
activation_url = base_url + 'ecAdminActivateStatus/activate'
activation_status = s.put(activation_url, headers=headers)
return activation_status
f = createSessionCC(username, password, apiKey)
# Update role and display creation status
print("\nCreation Status:")
print(updateRole(f).text)
# Display activation status
print("\nActivation Status:")
print(activateChanges(f).text)
[]
# Import Required Modules
import time, requests, json, urllib3, getpass
# Variables
cloudName = input("Cloud Name (e.g., zscloud.net): ")
username = input("Username: ")
password = getpass.getpass("Password: ")
apiKey = input("APIKey: ")
roleID = input("Enter the role ID to update: ")
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
def createSessionCC(username, password, apiKey):
auth_url = base_url + 'auth'
now = int(time.time() * 1000)
payload = {'apiKey':obfuscateApiKey(apiKey), 'username':username, 'password':password, 'timestamp':now  }
s = requests.Session()
# Added verify=False to bypass ZCC certificate otherwise call may fail with unable to verify SSL cert for certain cloud
r = s.post(auth_url,data=json.dumps(payload),headers=headers, verify=False)
return s
# Delete Admin Role
def deleteRole(s):
delete_url = base_url + 'adminRoles/' + roleID
delete_role = s.delete(delete_url,headers=headers)
return delete_role
# Activate Changes
def activateChanges(s):
activation_url = base_url + 'ecAdminActivateStatus/activate'
activation_status = s.put(activation_url, headers=headers)
return activation_status
f = createSessionCC(username, password, apiKey)
delete_result = deleteRole(f)
# Display deletion status
print("\nDeletion Status:")
print(delete_result)
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