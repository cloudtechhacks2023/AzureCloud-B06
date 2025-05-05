
---

# 🌐 **Azure Disaster Recovery (DR) Setup: Region-to-Region**

## 📌 **Overview**

Azure Site Recovery (ASR) enables seamless replication of Azure Virtual Machines (VMs) from one region to another, ensuring business continuity during planned or unplanned outages. This guide outlines the steps to set up DR across Azure regions.

---

## ✅ **Prerequisites**

Before initiating the DR setup, ensure the following:

* **Azure Subscription**: Active subscription with appropriate permissions.
* **Virtual Machines**: Identify VMs to be replicated.
* **Permissions**:

  * Ability to create and manage Recovery Services Vaults.
  * Permissions to create VMs in the target region.
  * Assign the "Site Recovery Contributor" role for Site Recovery operations.
* **Network Connectivity**: VMs should have outbound internet access to communicate with ASR services.

---

## 🛠️ **Step-by-Step Setup**

### 1. **Create a Recovery Services Vault**

1. Navigate to the Azure portal.
2. Search for and select **"Recovery Services vaults"**.
3. Click **"Create"** and provide:

   * **Name**: Unique name for the vault.
   * **Subscription**: Select your subscription.
   * **Resource Group**: Choose existing or create new.
   * **Location**: Select the primary region (source region).
4. Click **"Review + Create"** and then **"Create"**.

### 2. **Enable Replication for Azure VMs**

1. In the Azure portal, go to **"Recovery Services vaults"** and select your vault.
2. Under **"Getting Started"**, click **"Site Recovery"**.
3. In the **"Prepare Infrastructure"** section:

   * **Source**: Azure.
   * **Target**: Azure.
4. Click **"OK"**.
5. In the **"Enable replication"** section:

   * **Source Location**: Select the primary region.
   * **Source Subscription**: Choose your subscription.
   * **Source Resource Group**: Select the resource group containing the VMs.
   * **Target Location**: Choose the secondary region.
   * **Target Subscription**: Select your subscription.
   * **Target Resource Group**: Choose existing or create new.
6. Select the VMs you want to replicate.
7. Configure replication settings:

   * **Replication Policy**: Use default or customize as needed.
   * **Storage Account**: Choose or create a cache storage account in the source region.
8. Click **"Enable Replication"**.

*Note*: The initial replication might take time depending on the size of the VMs.

### 3. **Monitor Replication Status**

* Navigate to the **"Recovery Services vault"**.
* Under **"Protected Items"**, select **"Replicated Items"**.
* Monitor the replication health and status of each VM.

### 4. **Performing a Failover**

In the event of a disaster:

1. Go to the **"Recovery Services vault"**.
2. Under **"Protected Items"**, click **"Replicated Items"**.
3. Select the VM you want to failover.
4. Click **"Failover"**.
5. Choose a recovery point:

   * **Latest Processed**: Low RTO.
   * **Latest**: Low RPO.
   * **Latest App-Consistent**: Ensures application consistency.
   * **Custom**: Select a specific recovery point.
6. Optionally, select **"Shut down machine before beginning failover"** to minimize data loss.
7. Click **"OK"** to start the failover process.

*Note*: After failover, the VM will be available in the target region.

### 5. **Commit the Failover**

Once the VM is running successfully in the target region:

1. In the **"Recovery Services vault"**, under **"Replicated Items"**, select the VM.
2. Click **"Commit"** to finalize the failover.

*Note*: Committing deletes all the available recovery points for the VM in Site Recovery.

### 6. **Re-Protect the VM**

To replicate the VM back to the primary region:

1. Ensure the primary region is operational.
2. In the **"Recovery Services vault"**, under **"Replicated Items"**, select the VM.
3. Click **"Re-Protect"**.
4. Configure the replication settings to replicate from the secondary region back to the primary.

---

## 📊 **Additional Considerations**

* **Testing Failover**: Regularly perform test failovers to ensure DR readiness without impacting production.
* **Automation**: Use Azure Automation or Azure DevOps for automating DR processes.
* **Cost Management**: Monitor costs associated with replication and storage in both regions.
* **Compliance**: Ensure the DR setup complies with organizational and regulatory requirements.

---

## 📚 **Resources**

For more detailed information, refer to the official Microsoft documentation:

* [Set up disaster recovery to a secondary Azure region for an Azure VM](https://learn.microsoft.com/en-us/azure/site-recovery/azure-to-azure-quickstart)

