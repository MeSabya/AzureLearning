# Develop Solutions That Use Cosmos DB Storage 

## Usecases:
1️⃣ **Use Core (SQL) to store a product catalog**

#### Description:
You've decided to look at how the new project is going to store the catalog for your customer facing e-commerce site. The sales team is likely to need support for adding new product categories quickly. The team had issues in the past as the old system that was using a relational database was too structured. Any necessary changes to add properties to products required downtime to update the table schemas, queries, and databases.

A flat, denormalized table was being used, which also lead to many columns being empty. The database needs to store products in a way that will enable filtering data based on the category where the products are located.

For example:
- A clothing product needs to be searchable by sex, size, color, and style.
- A TV needs to be searchable on LCD or OLED, screen resolution, screen ratio, and HDR support.
- A DVD needs to have a region, the languages supported, and any extras.

#### Problem analysis
The sales team's primary requirement is to support semi-structured data. The schema needs to be flexible in order to store an ever-increasing number of product categories. The system needs to support searching and sorting across many different properties. There is a structured relational database that can be used to import data.


#### Recommended API: Core (SQL) 
❓ Why ?
The existing app uses a traditional relational database, which means that none of the other APIs are currently being used. However, Core (SQL) won't allow for any code reuse, but your team should quickly get up-to-speed with the SQL-like query language that is supported by Core (SQL).

Supporting new product categories is an important requirement for your project, and the Core (SQL) schema is flexible and requires a schemaless data store. As a result of this architecture, bringing a new product category online is as simple as adding a document for the new product. Changes to the schema or taking the database offline are not required.

Why not any of the other APIs?
Using the decision matrix from the previous unit, you can see why the other APIs are not a good solution for this scenario:

#### WHY NOT ANY OF THE OTHER APIS?
```table
API	                                 Description
------------           ---------------------------------------------------------------------------------------------------------------------------------------------
Azure Table	           This allow existing apps that are based on the Table API access to Azure Cosmos DB. However, new projects should always choose Core (SQL).
Cassandra	             isn't a good choice in this particular scenario, because the schema is unknown and will change over time.
Gremlin	               isn't a good choice since the scenario doesn't need to process graph-based data.
MongoDB	               MongoDB's lack of support for SQL-like queries give Core (SQL) an advantage for your existing relational database users.
```
#### Reference:
[use-the-core-sql-api-to-store-a-product-catalog](https://docs.microsoft.com/en-us/learn/modules/choose-api-for-cosmos-db/4-use-the-core-sql-api-to-store-a-product-catalog)

2️⃣ **Use the Gremlin (graph) API as a recommendation engine**
#### Description 
The marketing team wants to be able to offer additional product recommendations while customers are browsing products on your e-commerce site. For example, the team would like to provide suggestions like, "people who bought this product also bought that product", and "people who viewed this product also are viewing that product." The products that are recommended first should be your most popular products, therefore a method needs to be provided that will enable ranking the relationships between products.

#### Problem analysis
The data store needs to be able to assign weight values to the relationships between products. For example, you might store a count of the number of times that a relationship occurs. With that in mind, each time that a person buys "Product A" and "Product B", the relationship link between these two products needs to be incremented. This relationship counter is meta-data that needs to be stored in a database.

![image](https://user-images.githubusercontent.com/33947539/145349997-d6a08ddb-fed1-4b96-b3e4-8fbeccceb373.png)

#### Other Example of usecases
👉 The e-commerce application has a requirement to support a shopping basket. Customers can add and remove products, and any discounts (like buy one get one free) need to be kept in the basket. The sales team wants the flexibility to offer different kinds of discounts, and to add or remove different product categories.
**Core (SQL): This type of data is modeled best by documents. Core (SQL) is the best choice for a new system.**

👉The risk department has asked if the new project could implement some form of fraud detection and prevention. The guidance is that the fraud system would need to be able to track the relationship between customers, payment types, billing and delivery addresses, IP address, geolocation, and past purchase history. Anything that doesn't fit into normal behavior should be flagged.
**Gremlin Graph: as Complex relationships, and needed to store metadata against them is best supported by a graph mode of data. **

👉 The sales team would like to offer a chat feature for customers. Messages will have a fixed number of characters and be simple. The schema is fixed, and the sales team has an existing chat app for which they have built up many CQL statements for creating reports. They would like to reuse them if possible.

**Cassandra** 



