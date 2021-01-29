
# Push a Tomcat Docker image to Azure Container Registry

## Prerequisites

This example assumes you have previously completed the following examples.

1. [Create an Azure Resource Group](../../group/create/)
1. [Create an Azure Container Registry](../create/)

## Build the WAR file

<!-- workflow.cron(0 9 * * 2) -->
<!-- workflow.include(../create/README.md) -->

To build the WAR file use the following command line:


<!-- workflow.run()

cd acr/tomcat

  -->

```shell
  mvn package
```

## Build and push the Docker image to your Azure Container Registry

To build and push the Docker image to your ACR use the command lines below:

```shell
  export ACR_TOMCAT_IMAGE=tomcat:latest

  az acr build --registry $ACR --image $ACR_TOMCAT_IMAGE .
```

<!-- workflow.run()

cd ../..

  -->

<!-- workflow.directOnly()

export RESULT=$(az acr repository show --name $ACR --image $ACR_TOMCAT_IMAGE)
az group delete --name $RESOURCE_GROUP --yes || true

if [[ -z $RESULT ]]; then
  echo "Unable to find $ACR_TOMCAT_IMAGE image"
  exit 1
fi

  -->

## Cleanup

Do NOT forget to remove the resources once you are done running the example.

2m