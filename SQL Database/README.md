# Azure SQL Database

Azure SQL Database is available in three different deployment options:

- **Single database:** A single database that is billed and managed on a per database level.


The Azure SQL Database allows you to choose from two different purchasing models:

- **Database Transaction Unit (DTU):** DTUs are calculated based on a formula combining compute, storage, and I/O resources.

- **vCore:** The vCore model allows you to purchase a specified number of vCores based on your given workloads. vCore databases have a specific relationship between the number of cores and the amount of memory and storage provided to the database.

Azure SQL Database also includes automatic backups, automatic patching, built-in high availability and SQL Server feature enhancements without the need to upgrade software.

## Backups 

Backups are performed automatically without any intervention from you. Backups are stored in Azure blob geo-redundant storage and by default are retained for between 7 and 35 days, based on the service tier of the database.

It is worth stating that manual backups of databases are not permitted and the platform will deny any request to do so.

It is not possible to restore over an existing database. If a database needs to be restored, the existing database must be dropped or renamed prior to initiating the restore.

- **Restore using the Azure portal:** Using the Azure portal you have the option of restoring a database to the same Azure SQL Database server, or you can use the restore to create a new database on a new server in any Azure region.

- **Restore using scripting Languages:** Both PowerShell and Azure CLI can be utilized in order to restore a database.

## Active geo-replication

As transactions are committed to the primary (and its replicas within the same region), the transactions are sent to the secondaries to be replayed. The secondary databases are readable and can be used to offload read-only workloads. Furthermore, the secondary databases can be in the same region as the primary or in another Azure region.

## Failover groups

Failover groups are built on top of the technology used in geo-replication, but provide a single endpoint for connection. The major reason for using failover groups is that the technology provides endpoints, which can be utilized to route traffic to the appropriate replica. Your application can then connect after a failover without connection string changes.

## Serverless

Azure SQL Database serverless is a compute tier that will automatically scale up or down the resources for a given database based on demand. If the workload no longer requires compute resources, the database will become “paused” and you will not be charged during the period when the database is in this state. When a connection attempt is made, the database will “resume” and become available.

Another difference between serverless and the normal vCore model of Azure SQL Database is that with serverless you can specify a minimum and maximum number of vCores. Memory and I/O limits are proportional to the range that is specified.

Any applications using serverless should be configured to handle connection errors and include retry logic, as connecting to a paused database will generate a connection error.

## Elastic Pools

A group of databases that are managed together and share a common set of resources. Also facilitate easy scalability up to the set limits such that if a single database within the pool needs resources due to an unpredictable workload, the resources are there. If the entire pool needs additional resources, a simple slider option within the Azure portal will facilitate scaling the elastic pool up or down.

## Hyperscale

Azure SQL Database Hyperscale changes the paradigm and allows for databases to be 100 TB or more. Hyperscale introduces new horizontal scaling techniques to add compute nodes as the data sizes grow.

## Azure SQL Managed Instance

Azure SQL Managed Instance allows for easy migration paths for existing applications by allowing restores from on-premises backups. Unlike Azure SQL Database, which is designed around single database structures, Managed Instance provides an entire SQL Server instance, allowing up to 100 databases, as well as providing access to the system databases. 

Managed Instance provides other features that are not available in Azure SQL Database, including cross-database queries, common language runtime (CLR) and access to system database.

One key difference between Azure SQL Managed Instance and Azure SQL Database is that with MI you can manually make a copy-only backup of a database.

It offers auto-failover groups as a means to implement disaster recovery. This process asynchronously replicates data from the Azure SQL Managed Instance to a secondary; however, it is currently limited to the paired Azure region of the primary copy, and only one replica is allowed. In the event of a failover, application connection strings will automatically be routed to the appropriate instance.