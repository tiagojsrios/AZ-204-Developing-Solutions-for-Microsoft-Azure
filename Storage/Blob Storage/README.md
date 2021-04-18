# Azure Blob Storage

Azure Blob storage is an object storage solution optimized for storing massive amounts of unstructured data, such as text or binary data. Blob storage is ideal for:

- Serving images or documents directly to a browser, including full static websites.
- Storing files for distributed access.
- Streaming video and audio.
- Storing data for backup and restoration, disaster recovery, and archiving.
- Storing data for analysis by an on-premises or Azure-hosted service.

Azure Storage supports three kinds of blobs:

| Blob type | Description |
|--------------|------------------------|
| Block blobs  | Block blobs are used to hold text or binary files up to ~5 TB (50,000 blocks of 100 MB) in size. The primary use case for block blobs is the storage of files that are read from beginning to end, such as media files or image files for websites. They are named block blobs because files larger than 100 MB must be uploaded as small blocks. These blocks are then consolidated (or committed) into the final blob. |
| Page blobs   | Designed for scenarios that involve random-access reads and writes. Page blobs are used to store the virtual hard disk (VHD) files used by Azure Virtual Machines, but they're great for any scenario that involves random access. |
| Append blobs | Specialized block blobs that support only appending new data (not updating or deleting existing data), but they're very efficient at it. Append blobs are great for scenarios like storing logs or writing streamed data.A single append blob can be up to 195 GB. |

In Blob storage, every blob lives inside a blob container. You can store an unlimited number of blobs in a container and an unlimited number of containers in a storage account. Containers are "flat" — they can only store blobs, not other containers.

Technically, containers are "flat" and do not support any kind of nesting or hierarchy. But if you give your blobs hierarchical names that look like file paths (such as finance/budgets/2017/q1.xls), the API's listing operation can filter results to specific prefixes. This feature is often called virtual directories because some tools and client libraries use it to visualize and navigate Blob storage as if it was a file system.