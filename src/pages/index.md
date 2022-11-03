# Prerequisites

Install the Fly.io CLI tool: https://fly.io/docs/hands-on/install-flyctl/ on your local machine.

## Deploying Noiise App to Fly.io
1) Open the noiise repo/directory in a new terminal window.  
2) Type `Flyctl launch` and hit enter.  
3) If asked to authenticate, use this command: `Flyctl auth login`  
Credentials are stored here in Sync: https://cp.sync.com/files/2260640976  .
  
*When deploying an app it may say you've reached your 2 app limit, in which case you can go to the Fly.io Dashboard and delete those existing apps: https://fly.io/app/sign-in?return_to=%2Fdashboard .  
This is done in the 'Settings' section of the website at the bottom of the page.*


## TOML FIle Creation
When deploying an app to Fly.io a *TOML file* is created and will appear in your local noiise repo/directory.   
Fly.io will hopefully recognize this file in future deployments and will already know what you've chosen as configurations: location of servers, name of app etc.  
*I've noticed that this isn't always the case and you may need to manually delete the existing apps through the dashboard (steps listed above).*


## Postgres

Fly.io is smart enough to notice that we need a Postgres database in our app. As a result it will ask you if you want to create one. If it doesn't assk that usually means that you already have one deployed.  

Your credentials will only be shown to you **only once** if you proceed with creating a Postgres DB on FLy.io.  

We shouldn't need to touch the database once it's setup and deleting it will mean having to migrate existing users. It also means having to associate the app to the DB again, as it wouldn't know to do this automatically. It will however do this automatically if the app and DB are deployed together (At the same time). When a DB is attached to your app you'll receive a message like:

```
The following secret was added to noiise: DATABASE_URL=postgres://noiise:CKfKGrvSV7Pd3Dap@top2.nearest.of.noiise-db.internal:5432/noiise
Postgres cluster noiise-db is now attached to noiise
```
The above is not an actual DB URL.  

Please note that adding```?SSL=true``` to a Database URI/URL won't work on FLy.io like it does for other databses liksuch as e ElephantSQL or Heroku.

## Postgres TLS

Please note that TLS is not used on Fly.io for Postgres. Be sure to remove any reference in our Vapor code to it. For example 
in: ```App/configure.swift```


## Postgres Commands
1) Connect to your Fly.io Postgres DB:  
`flyctl postgres connect --app noiise-db `  
OR   
`flyctl ssh console --app noiise-db `  

2) Show users in users Table  
`\l `  
`\c noiise_accounts `  
`\dt SELECT * FROM users `  

# Postgres User Migration
https://www.postgresqltutorial.com/postgresql-tutorial/import-csv-file-into-posgresql-table/ 

3) Creating Mr. Chiu Manually:  
`INSERT INTO users VALUES ('4bc140c3-17cc-4df5-bd50-08b962fce8ef', 'Chiu', 'chiu@moe.ca', '$2b$12$EHpM9qNmOw575EQtFNYugOfJ8xTXlwgk0cOB9E/xYkTtFwCydZMWG'); 
`

# Create a PostgresDB (standalone)
```flyctl postgres create```.   
Details below, such as password. 

### Connect to it
```flyctl postgres connect -a noiise-staging-db```. 

### Creating a Proxy to access it with a GUI (Optional)
flyctl proxy 5432 -a noiise-staging-db

## Attach the DB to the existing app
Run this first to unset the current one:  
```flyctl secrets unset -a noiise-staging DATABASE_URL ```  
Then:  
```flyctl pg attach -a noiise-staging noiise-staging-db```

# Deploy an existing app
In the earlier deployment example we were deploying for the first time. When you make changes and want to re-deploy (outside of a pipeline) you
can do so through the ```flyctl deploy``` command.

# TLS/SSL
1) Go to the Fly.io dashboard and locate the Noiise app: https://fly.io/app/sign-in?return_to=%2Fdashboard  
![dashboard](../dashboard.png "Dashboard View")  
2) Click on the `noiise` app  
3) Go to Certificates 
![dashboard](../dash_cert.png "Dashboard View of Certificates")  
4) Click `Add Certificates`  
5) Enter the url: `noiise.ca`        
![dashboard](../dash_cert_url.png  "Dashboard View of entering Cert. URL")  
6) Click **Create** button  
7) **View** the certificate  
8) Go to your hosting platform (GoDaddy for example)  
9) In the DNS section, enter the records requested for CNAME, AAAA and A.  
10) Test out www. , http:// , and https:// addresses afterwards.
