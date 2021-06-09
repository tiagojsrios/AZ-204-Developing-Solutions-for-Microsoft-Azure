# Chapter 2. Develop for Azure Storage

- You can use different APIs for accessing your Cosmos DB database. Each API offers different feature depending on the way you need to represent your data. Remember that you cannot change the API once you have created your Cosmos DB database.

- Remember that your data is distributed across the different logic partitions by using the partition key. For this reason, once you have chosen a partition key, you cannot change it.

- The consistency level impacts the latency and availability of the data. In general terms, you should avoid the most extreme levels as they have a more significant impact on your program that should be carefully evaluated. If you are unsure of which level of consistency should use, you should use the session level, as this is the best-balanced level.

- You need to plan carefully how to create a new container in Azure Cosmos DB. You can set some of the properties that you can configure only during the creation process. Once you have created the container if you need to modify those properties, you need to create a new container with the needed values and migrate the data to the new container.

- When you are performing copy or move operations on containers or blobs, you are not limited to the same storage account. You can copy blobs and containers between Storage Accounts in different regions or even subscriptions, as long as you have enough privileges for accessing to both accounts.

- When you need to move a blob to any destination, container, or Storage Account, remember that you need first to perform a copy operation and then delete the source blob. There is no such move method in the CloudBlockBlob class.

- Leasing is the mechanism that you need to use to ensure that no other users or processes can access a blob while you are working with it. You can create timed or infinite leases. Remember that you need to release infinite leases manually.

- You should not try to change the access tier for a blob that is stored in an Azure Storage Account Gen1. Only Azure Storage Account Gen2 allows working with access tiers. If you try to use the SetAccessTier() method with a blob in an Azure Storage Account Gen1, you get an exception.

- You can move from hot to cool and vice versa to access tiers without needing to wait for rehydration. The rehydration process only happens when you move a blob from the archive to any other access tier.

1. Cosmos DB is a premium storage service that provides low-latency access to data distributed across the globe.
2. The PartitionKey system property defines the partition where the entity is stored. 
3. Choosing the correct PartitionKey is critical for achieving the right performance level. 
4. You can access Cosmos DB using different APIs: SQL, Table, Gremlin (Graph), MongoDB, and Cassandra. 
5. You can create your custom indexes in Cosmos DB.
6. You can choose the property that is used as the partition key. 
7. You should avoid selecting partition keys that create too many or too few logical partitions. 
8. A logical partition has a limit of 20 GB of storage. 
9. Consistency levels define how the data is replicated between the different regions in a Cosmos DB account. 
10. There are five consistency levels: strong, bounded staleness, session, consistent prefix, and eventual. 
11. Strong consistency level provides a higher level of consistency but also has a higher latency. 
12. Eventual consistency level provides lower latency and lower data consistency. 
13. You can move blob items between containers in the same Storage Account or containers in different Storage Accounts. 
14. Azure Blob Storage service offers three different access tiers with different prices for storage and accessing data.
15. You can automatically manage the movement between access tiers by implementing lifecycle management policies.