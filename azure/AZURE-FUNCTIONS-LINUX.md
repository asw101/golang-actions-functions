# AZURE-FUNCTIONS

## variables
```bash
RESOURCE_GROUP='200300-functions'
LOCATION='eastus'
RANDOM_STR='691d03'
if [ -z "$RANDOM_STR" ]; then RANDOM_STR=$(openssl rand -hex 3); else echo $RANDOM_STR; fi
STORAGE_NAME="storage${RANDOM_STR}"
FUNCTION_NAME="functions${RANDOM_STR}"
```

## functions
```bash
az group create -l $LOCATION -n $RESOURCE_GROUP

az storage account create -g $RESOURCE_GROUP -l $LOCATION -n $STORAGE_NAME \
    --kind StorageV2 \
    --sku Standard_LRS

az functionapp create -g $RESOURCE_GROUP -s $STORAGE_NAME -n $FUNCTION_NAME \
    --consumption-plan-location $LOCATION \
    --os-type Linux \
    --runtime python \
    --functions-version 3

az functionapp config appsettings set -g $RESOURCE_GROUP -n $FUNCTION_NAME \
    --settings "WEBSITE_MOUNT_ENABLED=1"
```

## deploy
```bash
RESOURCE_GROUP='200300-functions'
RANDOM_STR='691d03'
FUNCTION_NAME="functions${RANDOM_STR}"
cp host.linux.json host.json
source deploy-storage.sh
```
