1. Resource Group
Resource Group Name: cms

2. SQL Database
DB name: cms
Server: cms1234.database.windows.net
DB region: us-east
Admin login: csadmin
Admin password: A123456!
Resource group: cms
DB workload env: Development
DB compute + storage: DTU - Basic
Press the "Next: Networking" button, then select "Public Endpoint", and set both of the Firewall rules that appear to "Yes".
Set everything else to default
Run SQL queries in sql_scripts/ directory after completion, starting from the users table. Don't forget to take screenshots.

3. Storage Account
Resource group: cms
Storage account name: images1233 (needs to be unique)
Advanced - Allow enabling anonymous access on individual containers: Enable
Advanced - Access tier: Cool
Network access: Enable public access from all networks (the default)
Create container named "images". Set its access level to Container.
From Security + networking > Access keys:
Blob Storage key: i9CnYaI9jOAutwAo7Lg9huZqme0Ub55as4Wn9Bm7s3dXarNiRAXZCMstT80tr1RB2+7ueo0Cmszy+AStFZNo0A==


4. Microsoft Entra ID
4.1. App Registration
Name: cmsEntraID
Who can use? "Accounts in any organizational directory (Any Microsoft Entra ID tenant - Multitenant) and personal Microsoft accounts (e.g. Skype, Xbox)"
4.2. Secret Creation
Secret description: test
Secret Key: 5f0e7bc9-83e9-4493-b814-f4c512295c40
Client Secret: vTq8Q~G.YTyUa2yJKgTGzu3EgBeSUYAn~PKoAdhf
Application (client) ID: 2a09207f-3346-4430-861d-5b9af282b26b

5. Application
Name: udacitycms1234.azurewebsites.net
Runtime stack: Python 3.10
Pricing Plan: Free F1
If you are getting a "Validation failed for a resource" error, pick a different region.
After creation:

Settings -> Environment variables - Add the following variables (sample values are included, replace them with your values):
BLOB_ACCOUNT: images1233
BLOB_CONTAINER: images
BLOB_STORAGE_KEY: i9CnYaI9jOAutwAo7Lg9huZqme0Ub55as4Wn9Bm7s3dXarNiRAXZCMstT80tr1RB2+7ueo0Cmszy+AStFZNo0A==
SQL_SERVER: cms1234.database.windows.net
SQL_DATABASE: cms
SQL_USER_NAME: cmsadmin
SQL_PASSWORD: A123456!
CLIENT_SECRET: vTq8Q~G.YTyUa2yJKgTGzu3EgBeSUYAn~PKoAdhf
SECRET_KEY: 5f0e7bc9-83e9-4493-b814-f4c512295c40
CLIENT_ID: 2a09207f-3346-4430-861d-5b9af282b26b
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
