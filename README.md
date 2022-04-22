# Azure Cosmos DB Intra-account container copy (Private preview)

You can perform offline container copy within an Azure Cosmos DB account using container copy jobs.

This functionality is currently available for Azure Cosmos DB **Cassandra API** accounts and will be available soon for **SQL API** accounts.

If you have not signed-up for this Preview yet, please do so using this [link](https://forms.office.com/r/7t0HGtNvHp)

You may need to copy data within your Azure Cosmos DB account if you want to achieve either of these scenarios:

* Copy all items from one container to another.
* Change the [granularity at which throughput is provisioned - from database to container](https://docs.microsoft.com/azure/cosmos-db/set-throughput#set-throughput-on-a-database-and-a-container) and vice-versa.
* Change the [partition key](https://docs.microsoft.com/azure/cosmos-db/partitioning-overview#choose-partitionkey) of a container.
* Update the [unique keys](https://docs.microsoft.com/azure/cosmos-db/unique-keys) for a container.
* Rename a container/database.
* Adopt new features that are only supported on new containers.

To try out container copy jobs:

* Download this code as a zip file.
* Unzip it.
* Open the folder in [Azure Data Studio](https://docs.microsoft.com/sql/azure-data-studio/download-azure-data-studio?view=sql-server-ver15) (File - Open Folder).
* Run the code cells in the [Cassandra copy container  notebook](copy-container-cassandra.ipynb).
