### **Steps to Create an Azure Storage Account Using Azure Portal**  

#### **Step 1: Log in to Azure Portal**  
1. Go to [Azure Portal](https://portal.azure.com).  
2. Sign in with your Azure account credentials.  

#### **Step 2: Navigate to Storage Accounts**  
1. In the Azure Portal **search bar**, type **Storage Accounts** and click on it.  
2. Click on **+ Create** to start the storage account creation process.  

#### **Step 3: Configure Basic Settings**  
1. **Subscription**: Select the appropriate **Azure Subscription**.  
2. **Resource Group**: Choose an existing **resource group** or create a new one.  
3. **Storage Account Name**: Enter a **unique name** for your storage account (e.g., `mystorageaccount123`).  
4. **Region**: Select a **region** where you want to deploy the storage account.  
5. **Performance**: Choose between:  
   - **Standard** (for general-purpose workloads)  
   - **Premium** (for low-latency and high-performance storage)  
6. **Redundancy (Replication Type)**: Select the replication type:  
   - **LRS (Locally Redundant Storage)** – Replicates data within a single region.  
   - **GRS (Geo-Redundant Storage)** – Replicates data to a secondary region.  
   - **RA-GRS (Read-Access Geo-Redundant Storage)** – Same as GRS but allows read access.  
   - **ZRS (Zone-Redundant Storage)** – Replicates data across availability zones.  

#### **Step 4: Configure Advanced Settings (Optional)**  
1. **Security Features**: Enable options like:  
   - Enable **Azure Defender for Storage** (optional, for threat protection).  
   - Choose **Access Tier** (**Hot** for frequently accessed data, **Cool** for infrequent access).  
2. **Data Protection**:  
   - Enable **soft delete** for blobs and files (optional).  
   - Enable **versioning** (optional, useful for tracking changes).  

#### **Step 5: Review & Create**  
1. Click **Review + Create** to validate the configuration.  
2. After validation, click **Create** to deploy the storage account.  

#### **Step 6: Verify the Storage Account**  
1. Once deployment is complete, go to **Resource → Storage Account**.  
2. Under **Containers**, create a **new container** to store blobs.  
3. Under **File Shares**, create a **new file share** for cloud-based file storage.  

Your **Azure Storage Account** is now successfully created! 🚀


=================================================================================================================================
### **Steps to Create a Container in Azure Storage Account Using Azure Portal**  

#### **Step 1: Log in to Azure Portal**  
1. Open [Azure Portal](https://portal.azure.com).  
2. Sign in with your Azure account credentials.  

#### **Step 2: Navigate to the Storage Account**  
1. In the Azure Portal **search bar**, type **Storage Accounts** and select it.  
2. Click on the **Storage Account** where you want to create the container.  

#### **Step 3: Open the Blob Service**  
1. In the left-side menu, under **Data storage**, click on **Containers**.  
2. Click on **+ Container** to create a new container.  

#### **Step 4: Configure Container Settings**  
1. **Name**: Enter a **unique name** for the container (e.g., `mycontainer`).  
2. **Public Access Level** (Choose the access level based on your requirement):  
   - **Private (default)** – No public access, only authorized users can access it.  
   - **Blob (Anonymous Read Access for Blobs Only)** – Public can read blobs, but cannot list them.  
   - **Container (Anonymous Read Access for Container & Blobs)** – Public can read all blobs and list them.  
3. Click **Create** to finalize the container creation.  

#### **Step 5: Verify the Container**  
1. The newly created container will appear in the **Containers** list.  
2. Click on the container to **upload** blobs (files) using the **Upload** button.  

Your **Azure Blob Storage Container** is now successfully created! 🚀

=================================================================================================================================================
### **Steps to Create a File Share in Azure Storage Account Using Azure Portal**  

#### **Step 1: Log in to Azure Portal**  
1. Open [Azure Portal](https://portal.azure.com).  
2. Sign in with your Azure account credentials.  

#### **Step 2: Navigate to the Storage Account**  
1. In the Azure Portal **search bar**, type **Storage Accounts** and select it.  
2. Click on the **Storage Account** where you want to create the file share.  

#### **Step 3: Open the File Shares Section**  
1. In the left-side menu, under **Data storage**, click on **File shares**.  
2. Click on **+ File share** to create a new file share.  

#### **Step 4: Configure File Share Settings**  
1. **Name**: Enter a **unique name** for the file share (e.g., `myfileshare`).  
2. **Quota (Optional)**: Set the maximum storage limit (in GB). If not set, the file share will grow as needed.  
3. **Tier Selection** (Choose based on your workload):  
   - **Transaction optimized** – For frequent access.  
   - **Hot** – High-performance workloads.  
   - **Cool** – Infrequent access, lower cost.  
   - **Premium** – SSD-based storage for high performance.  
4. Click **Create** to finalize the file share creation.  

#### **Step 5: Verify the File Share**  
1. The newly created file share will appear in the **File Shares** list.  
2. Click on the file share to **upload files** or **create directories**.  

Your **Azure File Share** is now successfully created! 🚀