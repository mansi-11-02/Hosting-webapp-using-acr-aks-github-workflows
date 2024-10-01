Run the following commands in vm:
Install aws cli
Create resource group
```yml
curl -sL https://aka.ms/InstallAzureCLIDeb | sudo bash
az login
az group create --name git-rg --location francecentral
```

![image](https://github.com/user-attachments/assets/4233c3ae-8200-4359-8ce1-4eaace97f719)

Create acr and aks cluster
```yml
az acr create --resource-group git-rg --name gitacr --sku Basic
ssh-keygen
az aks create --resource-group git-rg --name gitAKSCluster --node-count 1 --enable-addons monitoring --generate-ssh-keys
```
![image](https://github.com/user-attachments/assets/591dec27-0bc1-46a7-bee8-3fcd42f19e5a)

Add Secrets in github repository

```yml
# Copy subscription id
az account list --output table
#paste it here
az ad sp create-for-rbac --name "myApp" --role contributor --scopes /subscriptions/{subscription-id} --sdk-auth
```
![image](https://github.com/user-attachments/assets/3591bd50-73df-4e1e-8374-c22d17dc7569)

Add the json file in secrets by giving name as AZURE_CREDENTIALS

Add deployment and service file in k8s folder
Run the workflow file








