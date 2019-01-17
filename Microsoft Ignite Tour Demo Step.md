# Microsoft Ignite Tour Demo Step

## a. Demo Single Container
> Use microsoft/dotnet-samples:aspnetapp
> Or abc12207/dotnet-samples:aspnetapp

Upload to Azure Container Registry
1. Login into ACR
```bash
az login

az acr login --msignitetour
```

2. Set image name and tag
```bash
docker tag abc12207/dotnet-samples:aspnetapp msignitetour.azurecr.io/dotnet-samples:aspnetapp
```

3. Push to ACR
```bash
docker push msignitetour.azurecr.io/dotnet-samples:aspnetapp
```
---
## b. Demo Multi Container use Docker Compose, use wordpress as example

### 1. wordpress with mysql database (all container)
1. Use wordpress-docker-compose-v1.yml

### 2. wordpress with Azure Database for MySQL
1. Create Azure Database for MySQL
  - Config firewall to allow Azure Service pass.
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

3. Use wordpress-docker-compose-v2.yml

### 3. wordpress with persistent storage
1. Set Web App AppSettings
   - WEBSITES_ENABLE_APP_SERVICE_STORAGE
     - TRUE

2. Use wordpress-docker-compose-v3.yml

> Or you can mount Azure Storage

### 4. wordpress with Redis container
1. Set Web App AppSettings
   - WP_REDIS_HOST
     - redis

2. Use wordpress-docker-compose-v4.yml

### 5. CICD
1. Use Azure DevOps -> IgniteTour-Sin
2. Use VS2019 new aspnetcore mvc project
3. Commit to the Azure Repos
4. Set Build Pipeline
   - Set Trigger
   - Set Build Task
   - Set Publish Task
   - Save & Queue
5. Set ACR webhook
6. Commit new code
  - See how it goes
