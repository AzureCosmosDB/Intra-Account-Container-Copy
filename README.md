# Azure Cosmos DB Intra-account container copy (Private preview)

You can perform offline container copy within an Azure Cosmos DB account using container copy jobs.

This functionality is currently available for Azure Cosmos DB **Cassandra API** and **SQL API** accounts.

If you have not signed-up for this Preview yet, please do so using this [link](https://forms.office.com/r/7t0HGtNvHp).

You may need to copy data within your Azure Cosmos DB account if you want to achieve either of these scenarios:

* Copy all items from one container to another.
* Change the [granularity at which throughput is provisioned - from database to container](https://docs.microsoft.com/azure/cosmos-db/set-throughput#set-throughput-on-a-database-and-a-container) and vice-versa.
* Change the [partition key](https://docs.microsoft.com/azure/cosmos-db/partitioning-overview#choose-partitionkey) of a container.
* Update the [unique keys](https://docs.microsoft.com/azure/cosmos-db/unique-keys) for a container.
* Rename a container/database.
* Adopt new features that are only supported on new containers.

## Overview of steps needed to do a container copy
1.	Create the target Cosmos DB container with the required settings (partition key, throughput granularity, RUs, unique key, etc.).
2. Stop the operations on the source container by pausing the application instances or any clients connecting to it.
3. Create the container copy job.
4. Monitor the progress of the container copy job and wait until it's completed.
4.	Resume the operations by appropriately pointing the application or client to the source or target container copy as intended.

## Try out container copy jobs

* Download this code as a zip file.
* Unzip it.
* Open the folder in [Azure Data Studio](https://docs.microsoft.com/sql/azure-data-studio/download-azure-data-studio?view=sql-server-ver15) (File - Open Folder).
* Run the code cells from either the [SQL container copy notebook](./container-copy-sql.ipynb) or [Cassandra copy container  notebook](./copy-container-cassandra.ipynb).

To learn more about intra-account container copy jobs, [refer to this doc.](./IntraAccountContainerCopy-Details%26FAQs.md)