---

# **Azure Backup & Restore**

## **1. Introduction to Azure Backup**
- Azure Backup is a cloud-based backup solution that provides data protection and disaster recovery.
- It helps in backing up on-premises servers, Azure Virtual Machines (VMs), SQL databases, file shares, and workloads.
- Eliminates the need for on-premises backup infrastructure.
- Provides automated backup scheduling, data retention, and security features.

## **2. Azure Backup Components**
- **Recovery Services Vault**: A storage container in Azure that holds backup data.
- **Azure Backup Agent**: Used to back up files and folders from on-premises to Azure.
- **Azure Backup Server (MABS)**: A modified version of System Center Data Protection Manager (DPM) for hybrid backup.
- **Azure Site Recovery (ASR)**: Provides disaster recovery solutions for entire workloads.
- **Azure Blob Storage**: Stores backup data in either standard or archive tiers.

## **3. Backup Methods**
### **A. Azure VM Backup**
- Uses Azure Backup extension to create snapshots.
- Supports full, incremental, and application-consistent backups.
- Backup frequency: Daily or multiple times a day.
- Retention: Short-term (daily, weekly) & long-term (monthly, yearly).

### **B. On-Premises Backup to Azure**
- **Azure Backup Agent**: Backs up files and folders to Azure.
- **Azure Backup Server (MABS)**: Backs up Hyper-V, VMware VMs, SQL databases, and system state.
- **System Center DPM**: Used for enterprise backup management.

### **C. SQL Server Backup in Azure**
- Backup directly from SQL Server running in Azure VM.
- Provides automated backup with long-term retention policies.
- Supports point-in-time recovery.

### **D. Azure File Share Backup**
- Protects Azure Files with Recovery Services Vault.
- Supports snapshots for quick restores.
- Allows granular file/folder recovery.

## **4. Backup Policies**
- **Define backup frequency** (daily, weekly, monthly).
- **Retention period**: Set data retention for short-term (weeks) or long-term (years).
- **Geo-redundant storage (GRS) vs. Locally redundant storage (LRS)**:
  - LRS keeps multiple copies within a single region.
  - GRS replicates data across regions for high availability.

## **5. Restore Methods**
### **A. Azure VM Restore**
- Restore entire VM from the latest or older backup.
- Restore disks only and attach them to another VM.
- Use **Replace existing VM** or **Create a new VM** option.

### **B. File & Folder Restore**
- Restore specific files from backed-up data without recovering the entire VM.
- Available for on-premises and Azure file shares.

### **C. SQL Database Restore**
- Restore entire database or perform point-in-time recovery.
- Supports differential and transaction log backups.

### **D. Azure Blob Storage Restore**
- Restores deleted or corrupted blobs using **Soft Delete** and **Point-in-Time Recovery**.

## **6. Security & Compliance in Azure Backup**
- **Multi-Factor Authentication (MFA)** for backup security.
- **Soft Delete**: Protects backup data from accidental deletion.
- **Immutable Backups**: Prevents data tampering and ransomware attacks.
- **Azure RBAC (Role-Based Access Control)**: Restricts backup access.
- **Encryption**: Uses Azure Storage encryption for data protection.

## **7. Cost Management in Azure Backup**
- Backup pricing depends on:
  - Storage type (LRS, GRS).
  - Amount of data stored.
  - Retention period.
  - Recovery operations.

- **Azure Cost Management** tool helps in monitoring backup costs.

## **8. Best Practices for Azure Backup**
- Define a clear **backup & retention policy**.
- Use **Application-Consistent Backups** for VMs.
- Enable **Soft Delete & Multi-Factor Authentication**.
- Test backups periodically to ensure successful restores.
- Optimize backup storage by **tiering data to archive storage**.
- Automate backup reports and alerts using **Azure Monitor**.

---