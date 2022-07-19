## How does intra-account container copy work?

Intra-account container copy jobs perform offline data copy using the source container's incremental change feed log.
* Within the platform, we allocate two 4-vCPU 16-GB memory server-side compute instances per Azure Cosmos DB account by default.
* The instances are allocated when one or more container copy jobs are created within the account.
* The container copy jobs run on these instances.
* The instances are shared by all the container copy jobs running within the same account.
* The platform may de-allocate the instances if they're idle for >15 mins.

> NOTE: We currently only support offline container copy. So, we strongly recommend to stop performing any operations on the source container prior to beginning the container copy. Item deletions and updates done on the source container after beginning the copy job may not be captured. Hence, continuing to perform operations on the source container while the container job is in progress may result in data missing on the target container.


## Factors affecting the rate of container copy job
The rate of container copy job progress is determined by these factors:
* Source container/database throughput setting.
* Target container/database throughput setting.
* Server-side compute instances allocated to the Azure Cosmos DB account for the performing the data transfer.

> IMPORTANT:
The default SKU offers two 4-vCPU 16-GB server-side instances per account.

## FAQs

### Is there an SLA for the container copy jobs?
Container copy jobs are currently supported on best-effort basis. We don't provide any SLA guarantees for the time taken to complete these jobs.

### Can I create multiple container copy jobs within an account?
Yes, you can create multiple jobs within the same account. The jobs will run consecutively. You can list all the jobs created within an account and monitor their progress.

### Can I copy an entire database within the Azure Cosmos DB account?
You'll have to create a job for each collection in the database.

### I have an Azure Cosmos DB account with multiple regions. In which region will the container copy job run?
The container copy job will run in the write region. If there are accounts configured with multi-region writes, the job will run in one of the regions from the list.

### What happens to the container copy jobs when the account's write region changes?
The account's write region may change in the rare scenario of a region outage or due to manual failover. In such scenario, incomplete container copy jobs created within the account would fail. You would need to recreate such jobs. Recreated jobs would then run against the new (current) write region.

### Why is a new database '_datatransferstate' created in the account when I run container copy jobs?. Am I being charged for this database?
* '_datatransferstate' is a temporary database that is created while running container copy jobs. This database gets used to store the state and progress of the copy job. 
* The database uses manual provisioned throughput of 800 RUs. You will be charged for this.
* Deleting this database will remove the container copy job history from the account. It can be safely deleted once all the jobs have completed, if you no longer need the job history.

