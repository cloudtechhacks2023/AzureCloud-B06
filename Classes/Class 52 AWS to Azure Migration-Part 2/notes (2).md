

## ✅ **AWS to Azure Migration Using Azure Migrate (via ASR Unified Agent)**

### 🔹 **Overview**

* Azure Migrate provides a central hub to assess and migrate servers to Azure.
* For AWS VM migration, the **ASR (Azure Site Recovery) Unified Replication Agent** is used.
* This approach is *agent-based*, meaning the agent is installed inside each VM.

---

### 🔹 **Pre-requisites**

1. **Azure Subscription** – with owner or contributor rights.
2. **AWS VMs** – Linux or Windows (with supported OS).
3. **Outbound Internet Access** – from the AWS VM (for agent communication).
4. **Ports Open**:

   * HTTPS (443) for Azure Migrate and ASR services.
   * Required internal ports for replication.
5. **Create a Project** – in Azure Migrate.

---

### 🔹 **High-Level Steps**

#### 1. **Set up Azure Migrate Project**

* Go to Azure portal → **Azure Migrate** → **Create project**.
* Select **Geography**, give a name, and create it.

#### 2. **Add Migration Tool**

* Inside the project, go to the **Servers, databases and web apps** tab.
* Under **Migration tools**, click on **Add tools**.
* Select **Azure Migrate: Server Migration**.

#### 3. **Prepare AWS VM for Replication**

* Login to your **AWS VM**.
* Download and install the **Unified Replication Agent**:

  * Download link and registration key will be provided by Azure Migrate.
* Install command (example for Windows):

  ```powershell
  UnifiedAgentInstaller.exe /q /x:<PATH> /RegistrationKey:<KEY>
  ```

  * For Linux, follow Azure's specific shell command with the key.

#### 4. **Install Mobility Service Agent**

* During installation of the Unified Agent, the **Mobility Service** is also installed.
* It enables replication to Azure.

#### 5. **Replicate AWS VMs**

* Back in Azure Migrate portal → **Replicate** → Choose source as **AWS**.
* Select **Yes, with the agent-based method**.
* Provide machine details (OS type, disk, size, etc.).
* Select **target Azure region**, **VM size**, and **network**.

#### 6. **Start Replication**

* Azure will initiate the **initial replication** (full sync).
* After that, **delta sync** will happen continuously.

---

### 🔹 **Test Migration**

* Once initial sync completes:

  * Go to Azure Migrate → Replicated items → Select VM → **Test Migration**.
  * This creates a cloned VM in Azure (non-production).

---

### 🔹 **Perform Final Migration**

* After testing and validation:

  * Click on **Migrate**.
  * Choose whether to shut down source machine.
  * Azure will finalize and bring up the VM in Azure.

---

### 🔹 **Post-Migration Tasks**

* Validate VM boot & services.
* Reconfigure IP, DNS if needed.
* Enable monitoring and backups.
* Remove on-prem or AWS resources if decommissioned.

---

### 🔹 **Advantages of ASR Unified Agent Method**

* Agent-based, suitable for *lift-and-shift* approach.
* No need for vCenter (unlike VMware).
* Continuous replication and minimal downtime.
* Works well even without Hyper-V or VMware setups.

---


