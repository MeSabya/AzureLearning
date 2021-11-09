# Three Pillars: Account, Database, Container
Cosmos DB (CDB) — a document store which is an evolution of a previously relatively popular Azure Document DB. 
Microsoft product team managed to differentiate Cosmos DB from competitors by offering 
“API endpoint of your choice”, “infinite scale”, “unlimited DB size” with “minimum configuration”.

![image](https://user-images.githubusercontent.com/33947539/140972929-b48cce11-b4a5-4dfc-a1cc-9b531ef0c52c.png)
### Account: 
It is an umbrella where you can perform administration tasks, among others:
- Global data replication
- Consistency levels
- Backup strategy
- Private endpoints
- Firewall rules

An Account can have as many databases created as you want, although only 25 accounts can be provisioned per subscription.

### Database:
Database which is a rather light logical “box” encapsulating data access and capacity allocation. Main features:
- Logically separate containers.
- Advanced user access scenarios to Databases.
- Provisioning of throughput which will be shared between containers in the same DB.

### container:
It is a schema-agnostic container of entities, stored procedures, user-defined functions (UDFs) and triggers.

## API endpoints and Resource Model
Currently CDB supports following API endpoints for your container:

- #### SQL API — successor of Document DB
- #### MongoDB — slim-down version of popular NoSQL database
- #### Cassandra — Apache Cassandra is another NoSQL DB for high throughput and scalability
- #### Gremlin — fully managed Graph database designed for social, geospatial, recommendation applications
- #### Table API — Table Storage with premium capabilities

Based on the API type used for container creation Cosmos DB will provision and project underlying container to table, collection or data structure.

## Provisioned throughput. Shared vs dedicated.
To measure database operation Microsoft introduced normalized measure:
**Request Units (RU)**: RUs encapsulates underlying consumption of CPU, Memory and IOPS. 
All database operations write, point read, query or execution of stored procedures, are measured by RUs.

In Cosmos DB you can provision throughput (RUs) on two levels:
1. Database
2. Container

### provisioned per container:
- It does allocate dedicated physical partition for any specific container.
- In this model of capacity allocation other containers in your database won’t compete for the same resources so you should expect to utilize full potential of provisioned RUs.
- There is a minimum throughput of 400 RUs per container even if you don’t have any data in it.

### Provisioning per database:
- It doesn’t allocate dedicated physical partition for any specific container but instead shares it between all containers in the DB.
- Biggest drawback of such design is a “greedy” container which can max-out throughput consumption and leave all others to wait until resources will free-up.

## References:
- https://medium.com/codex/azure-cosmos-db-introduction-998d246053b7
