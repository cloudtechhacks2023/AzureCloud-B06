## **Azure Storage Account Notes**

### **1. Introduction to Azure Storage Account**
- Azure Storage Account is a cloud storage service that provides scalable, durable, and highly available storage for various data types.
- It supports different storage services, including Blob Storage, File Shares, Queues, Tables, and Disks.
- Data is replicated across multiple locations to ensure durability and disaster recovery.

---

### **2. Types of Azure Storage**
- **Blob Storage**: Stores unstructured data like images, videos, logs, and backups.
- **File Storage (Azure Files)**: Managed file shares accessible via SMB or NFS.
- **Queue Storage**: Manages messages in a queue for asynchronous communication.
- **Table Storage**: Stores structured NoSQL data for fast access.
- **Disk Storage**: Provides managed disks for Azure Virtual Machines.

---

### **3. Storage Account Performance Tiers**
- **Standard Performance**: Uses HDD-based storage, suitable for general-purpose workloads.
- **Premium Performance**: Uses SSD-based storage, ideal for high-performance and low-latency applications.

---

### **4. Storage Account Redundancy Options**
- **Locally Redundant Storage (LRS)**: Data is replicated within a single datacenter.
- **Zone Redundant Storage (ZRS)**: Data is replicated across different Availability Zones in the same region.
- **Geo-Redundant Storage (GRS)**: Data is replicated to a secondary region with LRS at both locations.
- **Read-Access Geo-Redundant Storage (RA-GRS)**: Provides read access to the secondary region.

---

### **5. Storage Account Access Tiers (Blob Storage)**
- **Hot Tier**: Optimized for frequently accessed data.
- **Cool Tier**: Suitable for infrequently accessed data.
- **Archive Tier**: Lowest-cost storage for long-term archival data.

---

### **6. Storage Account Authentication & Security**
- **Access Keys**: Two keys are provided for authentication.
- **Shared Access Signatures (SAS)**: Grants limited access with expiration time.
- **Azure AD Authentication**: Uses role-based access control (RBAC) for secure access.
- **Encryption**: Data is encrypted at rest and in transit using Microsoft-managed or customer-managed keys.

---

### **7. Creating an Azure Storage Account (Step-by-Step)**
1. **Go to Azure Portal** → Search for **Storage Accounts**.
2. Click on **Create** → Select the **Subscription** and **Resource Group**.
3. Enter **Storage Account Name** (must be unique globally).
4. Choose the **Region** and **Performance Tier** (Standard/Premium).
5. Select the **Redundancy Option** (LRS, ZRS, GRS, or RA-GRS).
6. Configure **Networking, Security, and Access** settings.
7. Click **Review + Create** → **Create**.

---

### **8. Managing Azure Storage Account**
- **Access Storage via Azure Portal, CLI, PowerShell, or SDKs.**
- **Use Azure Storage Explorer** to manage blobs, files, queues, and tables.
- **Monitor and optimize storage costs** using Azure Monitor and Cost Management.

---

### **9. Azure Storage Pricing**
- Pricing is based on:
  - **Storage capacity** (GB/TB used).
  - **Access tier** (Hot, Cool, Archive).
  - **Replication type** (LRS, ZRS, GRS, RA-GRS).
  - **Operations & Transactions** (Read/Write/Delete requests).

---

Let me know if you need more details or specific use cases! 🚀