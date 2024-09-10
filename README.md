## Run and create the secrets : AZURE_CREDENTIALS
~~~bash
az ad sp create-for-rbac \
    --name "ghActionAzureVote" \
    --scope /subscriptions/<SUBSCRIPTION_ID>/resourceGroups/<RESOURCE_GROUP> \
    --role Contributor \
    --json-auth
~~~

To create an App Service based on AZ-CLI

~~~bash
az appservice plan create \
   --resource-group MY_RESOURCE_GROUP \
   --name MY_APP_SERVICE_PLAN \
   --is-linux
~~~

~~~bash
az webapp create \
    --name MY_WEBAPP_NAME \
    --plan MY_APP_SERVICE_PLAN \
    --resource-group MY_RESOURCE_GROUP \
    --runtime "DOTNET|5.0"
~~~

Create ACR and AKS
~~~bash
az group create --name myResourceGroup --location eastus
~~~
 
~~~bash
az acr create --resource-group myResourceGroup --name $ACRNAME --sku Basic
~~~

~~~bash

az aks install-cli

az aks create \
    --resource-group myResourceGroup \
    --name myAKSCluster \
    --node-count 2 \
    --generate-ssh-keys \
    --attach-acr $ACRNAME

az aks get-credentials --resource-group myResourceGroup --name myAKSCluster

kubectl get nodes

~~~
