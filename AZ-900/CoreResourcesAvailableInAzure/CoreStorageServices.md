# Core storage services:
- **Azure Blobs**: A massively scalable object store for text and binary data. Also includes support for big data analytics through Data Lake Storage Gen2.
- **Azure Files**: Managed file shares for cloud or on-premises deployments.
- **Azure Queues**: A messaging store for reliable messaging between application components.
- **Azure Tables**: A NoSQL store for schemaless storage of structured data.
- **Azure Disks**: Block-level storage volumes for Azure VMs.

## Azure Blob:
Azure Blob storage is Microsoft's object storage solution for the cloud. Blob storage is optimized for storing massive amounts of unstructured data.

***Blob storage is designed for***:
- Serving images or documents directly to a browser.
- Storing files for distributed access.
- Streaming video and audio.
- Writing to log files.
- Storing data for backup and restore, disaster recovery, and archiving.
- Storing data for analysis by an on-premises or Azure-hosted service.

### Blob storage resources:
Blob storage offers three types of resources:

1. The storage account
2. A container in the storage account
3. A blob in a container

![image](https://user-images.githubusercontent.com/33947539/140956864-bb5f58c4-5b58-4f2b-b367-90e45409fd24.png)
#### Storage account: 
A storage account provides a unique namespace in Azure for your data. Every object that you store in Azure Storage has an address that includes your unique account name.
#### Containers:
A container organizes a set of blobs, similar to a directory in a file system.
#### Blobs:
Azure Storage supports three types of blobs:

- ##### Block blobs:
store text and binary data. Block blobs are made up of blocks of data that can be managed individually. Block blobs can store up to about 190.7 TiB.

- ##### Append blobs :
are made up of blocks like block blobs, but are optimized for append operations. Append blobs are ideal for scenarios such as logging data from virtual machines.
- ##### Page blobs:
Page blobs store virtual hard drive (VHD) files and serve as disks for Azure virtual machines. 

## Hot, Cool, and Archive access tiers for blob data
Azure storage offers different access tiers so that you can store your blob data in the most cost-effective manner based on how it is being used. 
Azure Storage access tiers include:

##### Hot tier - 
An online tier optimized for storing data that is accessed or modified frequently. The Hot tier has the highest storage costs, but the lowest access costs.
##### Cool tier - 
An online tier optimized for storing data that is infrequently accessed or modified. Data in the Cool tier should be stored for a minimum of 30 days. The Cool tier has lower storage costs and higher access costs compared to the Hot tier.
##### Archive tier -
An offline tier optimized for storing data that is rarely accessed, and that has flexible latency requirements, on the order of hours. Data in the Archive tier should be stored for a minimum of 180 days.

## Azure Files:
Azure Files enables you to set up highly available network file shares that can be accessed by using the standard Server Message Block (SMB) protocol. 
That means that multiple VMs can share the same files with both read and write access.
File shares can be used for many common scenarios:
- Many on-premises applications use file shares
- Configuration files can be stored on a file share and accessed from multiple VMs.
- Resource logs, metrics, and crash dumps are just three examples of data that can be written to a file share and processed or analyzed later.

## Queue storage:
Say you want your customers to be able to upload pictures, and you want to create thumbnails for each picture. 
You could have your customer wait for you to create the thumbnails while uploading the pictures. 
An alternative would be to use a queue. When the customer finishes their upload, write a message to the queue. 

Then have an Azure Function retrieve the message from the queue and create the thumbnails. Each of the parts of this processing can be scaled separately,
giving you more control when tuning it for your usage.

## Disk storage:
- An Azure managed disk is a virtual hard disk (VHD). You can think of it like a physical disk in an on-premises server but, virtualized. 
- Azure-managed disks are stored as page blobs, which are a random IO storage object in Azure.
Then have an Azure Function retrieve the message from the queue and create the thumbnails. Each of the parts of this processing can be scaled separately.
