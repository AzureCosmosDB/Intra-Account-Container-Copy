## List all the container copy jobs created in an account
To list all the container copy jobs created in an account:

az cosmosdb dts list --account-name $accountName --resource-group $resourceGroup

## Pause a container copy job
In order to pause an ongoing container copy job, you may use the command:

az cosmosdb dts pause --account-name $accountName --resource-group $resourceGroup --job-name $jobName

## Resume a container copy job
In order to resume an ongoing container copy job, you may use the command:

az cosmosdb dts resume --account-name $accountName --resource-group $resourceGroup --job-name $jobName
