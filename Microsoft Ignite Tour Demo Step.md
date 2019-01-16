# Microsoft Ignite Tour Demo Step

## a. Demo Single Container
> Use microsoft/dotnet-samples:aspnetapp
> Or abc12207/dotnet-samples:aspnetapp

Upload to Azure Container Registry


## b. Demo Multi Container use Docker Compose
### 1. Demo wordpress with mysql database (all container)
### 2. Demo wordpress with Azure Database for MySQL
1. Create Azure Database for MySQL
  - Setting firewall to allow Azure Service pass.
  - Create wordpress database for web app to use.
    ``` bash
    az mysql db create --resource-group IgniteTour --server-name msignitetour --name wordpress
    ``` 
2. Set Web App AppSettings
  - WORDPRESS_DB_HOST
    - msignitetour.mysql.database.azure.com
  - WORDPRESS_DB_USER
    - abc12207@msignitetour
  - WORDPRESS_DB_PASSWORD
    - x7ANa7sE7h+6P^S!
  - WORDPRESS_DB_NAME
    - wordpress
  - MYSQL_SSL_CA
    - BaltimoreCyberTrustroot.crt.pem
### 3. Demo wordpress with mysql database

### 4. Demo switch Multi to Single then to Multi, Container still exist

### 5. CICD
Use Azure Repos
Commit new code
Trigger build Image and push to Azure Container Registry (CI)
Azure Container Registry trigger Azre Web App (CD)