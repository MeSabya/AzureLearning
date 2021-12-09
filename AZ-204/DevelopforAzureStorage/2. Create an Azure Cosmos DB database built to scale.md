## Create an Azure Cosmos DB account in the Azure portal

### What is an Azure Cosmos DB account?

An Azure Cosmos DB account is an Azure resource that acts as the organizational entity for your databases. It connects your usage to your Azure subscription for billing purposes.

#### Reference 
https://docs.microsoft.com/en-us/learn/modules/create-cosmos-db-for-scale/2-create-an-account

### What is a request unit?
- Azure Cosmos DB measures throughput using something called a request unit (RU). 
- Request unit usage is measured per second, so the unit of measure is request units per second (RU/s). 
- You must reserve the number of RU/s you want Azure Cosmos DB to provision in advance
- **A single request unit, one RU, is equal to the approximate cost of performing a single GET request on a 1-KB document using a document's ID.**

- While you estimate the number of RUs per second to provision, consider the following factors:
   - **Item size**: As the size of an item increases, the number of RUs consumed to read or write the item also increases.
   - **Item indexing**: By default, each item is automatically indexed. Fewer RUs are consumed if you choose not to index some of your items in a container.
   - **Item property count**: Assuming the default indexing is on all properties, the number of RUs consumed to write an item increases as the item property count increases.
   - **Indexed properties**: An index policy on each container determines which properties are indexed by default. To reduce the RU consumption for write operations, limit the  
     number of indexed properties.
   - **Data consistency**: The strong and bounded staleness consistency levels consume approximately two times more RUs on read operations when compared to that of other relaxed consistency levels.
   - **Query patterns**: The complexity of a query affects how many RUs are consumed for an operation. Factors that affect the cost of query operations include:

      1. The number of query results
      2. The number of predicates
      3. The nature of the predicates
      4. The number of user-defined functions
      5. The size of the source data
      6. The size of the result set
      7. Projections 

 - **If you attempt to use throughput higher than the one provisioned, your request will be rate-limited.**
 - **The number of RUs used for a given database operation over the same data does not varie over time**
 - **If you provision 'R' RUs on an Azure Cosmos container (or a database), Azure Cosmos DB ensures that 'R' RUs are available in each region associated with your account.** 
