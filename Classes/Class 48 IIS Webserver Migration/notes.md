

## 🛠️ Prerequisites

### 🔹 On-Premises Server

- **IIS Installation**: Ensure that Internet Information Services (IIS) is installed and running.
- **Web Deploy Tool**: Install the Web Deploy tool (msdeploy).
- **Web Management Service**: Verify that the Web Management Service (WMSVC) is installed and running. ([Extend and Migrate an on-premises site to Microsoft Azure - Configuration Manager | Microsoft Learn](https://learn.microsoft.com/en-us/mem/configmgr/core/support/azure-migration-tool?utm_source=chatgpt.com))

### 🔹 Azure Virtual Machine

- **VM Setup**: Create a Windows Server VM in Azure.
- **IIS and Web Deploy**: Install IIS and the Web Deploy tool on the Azure VM.
- **Firewall Configuration**: Configure firewall rules to allow traffic on ports 80 (HTTP), 443 (HTTPS), and 8172 (Web Deploy).
- **Web Management Service**: Ensure that the Web Management Service (WMSVC) is installed and running.

---

## 🚀 Migration Steps

### 1. 🧾 Assess Dependencies

- **Identify Dependencies**: On the source server, run the following command to identify dependencies:

  ```bash
  msdeploy -verb:getDependencies -source:apphostconfig="Default Web Site"
  ```


- **Review Output**: Review the output and install any missing features or components on the destination server.

### 2. 📦 Choose a Migration Method

#### Option A: 🔄 Live Sync (Direct Transfer)

- **Initiate Live Sync**: From the source server, execute:

  ```bash
  msdeploy -verb:sync -source:apphostconfig="Default Web Site" -dest:apphostconfig="Default Web Site",computername=AzureVMName,username=YourUsername,password=YourPassword
  ```


- **Ensure Port Accessibility**: Make sure port 8172 is open on both the Azure VM's firewall and its Network Security Group (NSG) settings.

#### Option B: 📁 Offline Sync (Package and Deploy)

- **Create Deployment Package**: On the source server:

  ```bash
  msdeploy -verb:sync -source:apphostconfig="Site1" -dest:archivedir=c:\archive\package.zip
  ```


- **Transfer Package**: Move the package to the Azure VM.

- **Import Package**: On the Azure VM:

  ```bash
  msdeploy -verb:sync -source:archivedir=c:\archive\package.zip -dest:appHostConfig="Site1"
  ```


#### Option C: ⚙️ Migrate IIS Settings Only

- **Export IIS Settings**: On the source server: ([Extend and Migrate an on-premises site to Microsoft Azure - Configuration Manager | Microsoft Learn](https://learn.microsoft.com/en-us/mem/configmgr/core/support/azure-migration-tool?utm_source=chatgpt.com))

  ```bash
  msdeploy -verb:sync -source:webserver -dest:package=c:\folder\package.zip -disableLink:Content
  ```


- **Manual Content Transfer**: Manually copy website content to the Azure VM.

---

## 🔧 Post-Migration Configuration

- **Application Pools**: Manually create necessary application pools on the Azure VM before importing the site.
- **Bindings and Certificates**: Verify and configure site bindings (e.g., hostnames, ports). Install and bind SSL certificates as needed.
- **Firewall and NSG Settings**: Ensure that required ports (80, 443, 8172) are open on both the Windows Firewall and Azure NSG.
- **Testing**: Access the website using its public IP or domain name to confirm successful deployment.

---

## 🛠️ Troubleshooting Tips

- **Connection Issues**:
  - Verify that the Web Management Service is running on the Azure VM.
  - Ensure correct credentials are used during deployment.
  - Check firewall and NSG settings for open ports.

- **Deployment Errors**:
  - Review logs in IIS Manager and Event Viewer for detailed error messages.
  - Confirm that all dependencies and required features are installed on the Azure VM.

- **Performance Issues**:
  - Monitor resource utilization on the Azure VM to ensure it meets the application's requirements.

---

For a visual guide on setting up an Azure VM, configuring IIS, and deploying a website, you can refer to the following video tutorial:

[Azure VM creation, Configure IIS, deploy website Part 3](https://www.youtube.com/watch?v=yO1XZt0ysjs)

--- 