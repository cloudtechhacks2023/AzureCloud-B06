## **Image Capture in Azure**  

### **1. What is an Image in Azure?**  
- An **Azure Image** is a **generalized snapshot** of a Virtual Machine (VM) that can be used to deploy multiple VMs with the same configuration.  
- It includes the **OS, installed applications, and custom configurations**.  
- It helps in **standardized deployments** and **scalability**.  

---

### **2. Types of Images in Azure**  
1. **Marketplace Image**  
   - Pre-built images provided by Microsoft and third-party vendors.  
   - Examples: Ubuntu, Windows Server, RHEL, CentOS, SQL Server images.  

2. **Custom Image**  
   - A VM image captured from an existing Azure VM with custom configurations.  
   - Used for deploying identical VMs in an environment.  

3. **Shared Image Gallery (SIG)**  
   - Allows storing and distributing **custom images** across subscriptions and regions.  
   - Supports **versioning** and **replication**.  

---

### **3. Steps to Capture an Image in Azure**  

#### **A. Prepare the VM for Image Capture**  
1. **Deallocate the VM**  
   ```bash
   az vm deallocate --resource-group <resource-group> --name <vm-name>
   ```
2. **Generalize the VM** (Removes machine-specific data)  
   - **Windows:**  
     ```powershell
     Sysprep.exe /generalize /shutdown
     ```
   - **Linux:**  
     ```bash
     sudo waagent -deprovision+user
     sudo shutdown -h now
     ```

---

#### **B. Capture the Image**  
1. **Using Azure Portal**  
   - Go to **Virtual Machines** → Select VM → Click **Capture**.  
   - Enter the **Image Name** and select **Resource Group**.  
   - Choose **Automatically delete this VM after creating the image** (optional).  
   - Click **Create**.  

2. **Using Azure CLI**  
   ```bash
   az image create --resource-group <resource-group> --name <image-name> \
   --source <vm-name> --os-type Linux
   ```

---

### **4. Deploy VM from Captured Image**  
- **From Azure Portal:**  
  - Go to **Images** → Select the captured image → Click **Create VM**.  
- **Using CLI:**  
  ```bash
  az vm create --resource-group <resource-group> --name <new-vm> \
  --image <image-name> --admin-username azureuser --generate-ssh-keys
  ```

---

### **5. Best Practices**  
- Always **generalize** the VM before capturing the image.  
- Use **Shared Image Gallery (SIG)** for scalable deployments.  
- **Keep Image Versions** to track changes and rollbacks.  
- Automate image creation with **Azure DevOps Pipelines** or **Packer**.  

This covers **Image Capture in Azure**, including types, steps, and best practices. 🚀

--------------------------------------------------------------------------------------------------------------------------
### **Azure Disk Snapshots – A Complete Guide**  

#### **🔹 What is an Azure Disk Snapshot?**  
An **Azure Disk Snapshot** is a **point-in-time, read-only backup** of a **Managed Disk** that helps in **disaster recovery, migration, and cloning** of virtual machines. Snapshots ensure **data protection** by enabling you to restore a disk to a previous state without affecting the original disk.  

#### **🔹 Types of Snapshots in Azure**  
1. **Full Snapshot**:  
   - Captures the entire disk as a single backup.  
   - Storage consumption equals the size of the disk.  
   - Suitable for one-time backups and migrations.  

2. **Incremental Snapshot** (Recommended) 🚀  
   - Captures **only the changes** since the last snapshot.  
   - **Cost-efficient**, as it reduces storage usage.  
   - Ideal for frequent backups and disaster recovery.  

#### **🔹 Why Use Azure Snapshots?**  
✅ **Instant Backup & Restore** – Quickly recover data in case of failure.  
✅ **Efficient Disaster Recovery** – Restore VMs effortlessly.  
✅ **Faster VM Deployment** – Clone VMs for staging and testing.  
✅ **Optimized Storage Costs** – Use incremental snapshots to save costs.  
✅ **Seamless Migration** – Move workloads across Azure regions.  

#### **🔹 How to Create a Snapshot in Azure?**  
📌 **Via Azure Portal**  
1️⃣ Navigate to **Azure Portal** → **Disks** → Select the **Managed Disk**.  
2️⃣ Click **Create Snapshot** and choose the **Storage Type (Standard/Premium SSD/HDD)**.  
3️⃣ Configure **Incremental Snapshot** for cost efficiency.  
4️⃣ Click **Review + Create** → Confirm the snapshot creation.  

📌 **Via Azure CLI**  
```sh
az snapshot create --resource-group MyResourceGroup --name MySnapshot \
 --source /subscriptions/{subscription-id}/resourceGroups/MyResourceGroup/providers/Microsoft.Compute/disks/MyDisk \
 --location eastus --incremental true
```

📌 **Via PowerShell**  
```powershell
New-AzSnapshot -ResourceGroupName "MyResourceGroup" -SnapshotName "MySnapshot" `
 -SourceUri "/subscriptions/{subscription-id}/resourceGroups/MyResourceGroup/providers/Microsoft.Compute/disks/MyDisk"
```

#### **🔹 Restoring a Disk from Snapshot**  
1️⃣ Go to **Azure Portal** → **Snapshots** → Select the snapshot.  
2️⃣ Click **Create Disk** to generate a new disk from the snapshot.  
3️⃣ Attach the new disk to a Virtual Machine.  

#### **🔹 Snapshot Management Best Practices**  
🔹 **Use Incremental Snapshots** to reduce storage costs.  
🔹 **Automate Snapshot Creation** using Azure CLI, PowerShell, or Terraform.  
🔹 **Set Retention Policies** to auto-delete older snapshots and optimize storage.  
🔹 **Use Azure Backup** for long-term retention and compliance.  

#### **🔹 Terraform Code for Azure Snapshots**  
```terraform
resource "azurerm_snapshot" "example" {
  name                = "mySnapshot"
  resource_group_name = "MyResourceGroup"
  location            = "East US"
  create_option       = "Copy"
  source_uri          = azurerm_managed_disk.example.id
}
```

💡 **Pro Tip:** Combine **Azure Policy** and **Automation** to enforce snapshot retention policies and optimize backup strategies!  

Would you like a hands-on demo or need help with automated snapshot scheduling? 🚀