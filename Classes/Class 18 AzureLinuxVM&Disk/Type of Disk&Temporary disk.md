## **Types of Disks in Azure Virtual Machines**  

### **1. Overview of Azure Disks**  
Azure provides different types of disks for Virtual Machines (VMs), each serving a specific purpose:  
- **OS Disk** – Stores the operating system.  
- **Temporary Disk** – Used for temporary storage.  
- **Data Disk** – Used for storing application data.  

---

### **2. OS Disk (Operating System Disk)**  
- **Purpose:** Stores the operating system and system files.  
- **Storage Type:** Managed disk (Premium SSD, Standard SSD, or Standard HDD).  
- **Persistence:** **Persistent** across VM reboots and shutdowns.  
- **Default Size:** Varies by OS, usually **30GB - 128GB**.  
- **Attached As:** **/dev/sda** (Linux) or **C:** drive (Windows).  
- **Backup:** Supports Azure Backup and Snapshots.  
- **Limitations:** Cannot be detached from the VM while running.  

---

### **3. Temporary Disk**  
- **Purpose:** Provides temporary storage for **paging/swap files** and short-term operations.  
- **Storage Type:** **Locally attached SSD**.  
- **Persistence:** **Non-persistent** – Data is lost if the VM is deallocated or restarted.  
- **Default Size:** Varies by VM size, typically **5GB to 200GB**.  
- **Attached As:** **/dev/sdb** (Linux) or **D:** drive (Windows).  
- **Best Practices:**  
  - Do not store important data on the temporary disk.  
  - Used for **pagefile.sys (Windows)** or **swap partition (Linux)**.  
  - Data resets after VM redeployment.  

---

### **4. Data Disk**  
- **Purpose:** Stores applications, databases, and user data.  
- **Storage Type:** Managed disk (Premium SSD, Standard SSD, Standard HDD, Ultra Disk).  
- **Persistence:** **Persistent** – Data remains even after VM reboots.  
- **Maximum Size:** **32TB per disk** (up to 256TB per VM with multiple disks).  
- **Attached As:** **/dev/sdc, /dev/sdd, etc. (Linux)** or **E:, F:, etc. (Windows)**.  
- **Backup:** Supports Azure Backup, Snapshots, and Replication.  
- **Best Practices:**  
  - Format and mount the disk before use.  
  - Use **LVM (Logical Volume Manager)** for better disk management.  
  - Use **Ultra Disk** for high IOPS workloads (Databases, SAP).  

---

### **5. Disk Storage Types in Azure**  
- **Premium SSD** – High-performance, low-latency SSD for production workloads.  
- **Standard SSD** – Cost-effective SSD for general-purpose workloads.  
- **Standard HDD** – Low-cost option for infrequent access workloads.  
- **Ultra Disk** – Best for high-throughput applications like databases.  

This covers the different types of disks in **Azure Virtual Machines**, including their use cases and best practices. 🚀
---------------------------------------------------------------------------------------------------------------------------------

## **Temporary Disk in Azure**  

### **1. Overview of Temporary Disk**  
- Azure Virtual Machines come with a **Temporary Disk**, which provides short-term storage.  
- It is **locally attached SSD storage** used primarily for caching and paging operations.  
- The disk is **non-persistent**, meaning data is lost when the VM is restarted, stopped, or deallocated.  

---

### **2. Characteristics of Temporary Disk**  
- **Attached by Default**: Every Azure VM gets a temporary disk by default.  
- **High-Speed Performance**: Uses locally attached SSD for fast read/write operations.  
- **Non-Persistent Storage**: Data stored in the temporary disk is lost when:  
  - VM is **deallocated** or **restarted**  
  - VM undergoes **hardware maintenance**  
- **Default Disk Size**: The size varies based on VM SKU (ranges from **4GB to 200GB**).  
- **Location in OS**:  
  - **Windows:** Mounted as the `D:` drive.  
  - **Linux:** Mounted as `/dev/sdb` or `/mnt`.  

---

### **3. Uses of Temporary Disk**  
- **Pagefile / Swap Space**  
  - **Windows:** Used for `pagefile.sys` (virtual memory).  
  - **Linux:** Used as **swap space** for managing memory efficiently.  
- **Cache Storage** for temporary computations.  
- **Short-Term Data Processing** tasks that don’t need persistence.  

---

### **4. Limitations of Temporary Disk**  
- **Data Loss**: If the VM is restarted, resized, or deallocated, the temporary disk is wiped.  
- **Not for Persistent Storage**: Should not be used for applications that require data retention.  
- **No Backup Support**: Azure Backup does not cover temporary disks.  

---

### **5. Best Practices**  
- **Avoid Storing Important Data**: Use **OS Disk** or **Data Disks** for persistent storage.  
- **Use for Performance-Intensive Tasks**: Leverage the high-speed nature for temporary workloads.  
- **Configure Swap/Pagefile Properly**: Ensure proper allocation based on workload needs.  

This summarizes **Temporary Disks in Azure**, including their purpose, usage, and best practices. 🚀