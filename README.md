1. Resource Group
Resource Group Name: cms

2. SQL Database
DB name: cms
Server: cms1111.database.windows.net
DB region: us-east
Admin login: cmsadmin
Admin password: A123456!
Resource group: cms
DB workload env: Development
DB compute + storage: DTU - Basic
Press the "Next: Networking" button, then select "Public Endpoint", and set both of the Firewall rules that appear to "Yes".
Set everything else to default
Run SQL queries in sql_scripts/ directory after completion, starting from the users table. Don't forget to take screenshots.

3. Storage Account
Resource group: cms
Storage account name: images12332 (needs to be unique)
Advanced - Allow enabling anonymous access on individual containers: Enable
Advanced - Access tier: Cool
Network access: Enable public access from all networks (the default)
Create container named "images". Set its access level to Container.
From Security + networking > Access keys:
Blob Storage key: Qz/Xyta3qKeyenoOu7ZopQAouyO3ULXbVU5sGNcjQ66oiVNVouk/ESwNXOqoaySBylOszdM9tkep+AStf21SoA==


4. Microsoft Entra ID
4.1. App Registration
Name: cmsEntraID
Who can use? "Accounts in any organizational directory (Any Microsoft Entra ID tenant - Multitenant) and personal Microsoft accounts (e.g. Skype, Xbox)"
4.2. Secret Creation
Secret description: test
Secret Key: af1dadb3-3496-4270-93f5-50d88e04d473
Client Secret:IYc8Q~VpZzN4nylj1OJJxpzxFJVw9p6yUM5uocfW
Application (client) ID: ab7d6fc1-36f7-4284-afce-dd7e58f958c6

5. Application
Name: udacitycms1234.azurewebsites.net
Runtime stack: Python 3.10
Pricing Plan: Free F1
If you are getting a "Validation failed for a resource" error, pick a different region.
After creation:

Settings -> Environment variables - Add the following variables (sample values are included, replace them with your values):
BLOB_ACCOUNT: images12332
BLOB_CONTAINER: images
BLOB_STORAGE_KEY: Qz/Xyta3qKeyenoOu7ZopQAouyO3ULXbVU5sGNcjQ66oiVNVouk/ESwNXOqoaySBylOszdM9tkep+AStf21SoA==
SQL_SERVER: cms1111.database.windows.net
SQL_DATABASE: cms
SQL_USER_NAME: cmsadmin
SQL_PASSWORD: A123456!
CLIENT_SECRET:IYc8Q~VpZzN4nylj1OJJxpzxFJVw9p6yUM5uocfW
SECRET_KEY: af1dadb3-3496-4270-93f5-50d88e04d473
CLIENT_ID: ab7d6fc1-36f7-4284-afce-dd7e58f958c6
Deployment Center
Source: GitHub
Pick the repo that contains the starter files.

6. Setting up OAuth2
At this point, your application should already be running. You should already be able to log in with username admin and password pass and you can create new posts or update existing ones.

The next part is getting the OAuth2 login to work.

Go to Microsoft Entra ID > App Registrations, click on the App Registration created earlier, and then pick Authentication from the left sidebar.

6.1. Microsoft Entra ID - Authentication - Add a Platform - Web
Redirect URIs: https://[IP ADDRESS FROM VM or WEB APP ADDRESS]/getAToken
logout URL: https://[IP ADDRESS FROM VM or WEB APP ADDRESS]/login
