
## **Azure Linux Virtual Machine Notes**  

### **1. Introduction to Azure Linux Virtual Machine**  
- Azure Virtual Machine (VM) allows users to deploy and manage Linux-based workloads in the cloud.  
- It provides Infrastructure as a Service (IaaS) with scalability, high availability, and cost-effectiveness.  
- Azure supports multiple Linux distributions like Ubuntu, CentOS, RHEL, Debian, and SUSE.  

### **2. Creating an Azure Linux VM**  
- Login to Azure Portal: [https://portal.azure.com](https://portal.azure.com)  
- Navigate to **Virtual Machines** > Click **Create** > **Azure Virtual Machine**  
- Select **Subscription & Resource Group**  
- Choose **Region**, **VM Name**, and **Image (OS)** (e.g., Ubuntu 20.04 LTS)  
- Configure **Size (vCPU & RAM)** based on workload  
- Set **Administrator Account** (SSH Public Key or Password)  
- Configure **Networking** (Assign Virtual Network, Subnet, Public IP, and NSG)  
- Enable monitoring (Boot diagnostics, Azure Monitor, Log Analytics)  
- Click **Review + Create** and Deploy  

### **3. Connecting to Azure Linux VM**  
- **Using SSH (Linux/Mac)**  
  ```bash
  ssh -i <private-key.pem> username@public-ip
  ```
- **Using SSH (Windows with PowerShell/CMD)**  
  ```powershell
  ssh username@public-ip
  ```
- **Using Azure Bastion (Without Public IP)**  
  - Go to **VM Overview** > **Connect** > **Bastion** > Enter Credentials  

### **4. Managing Azure Linux VM**  
- **Start/Stop VM**  
  ```bash
  az vm start --resource-group <resource-group> --name <vm-name>
  az vm stop --resource-group <resource-group> --name <vm-name>
  ```
- **Resize VM** (Increase CPU/RAM)  
  ```bash
  az vm resize --resource-group <resource-group> --name <vm-name> --size Standard_D2s_v3
  ```
- **Attach Data Disk**  
  ```bash
  az vm disk attach --resource-group <resource-group> --vm-name <vm-name> --name <disk-name>
  ```

### **5. Configuring Azure Linux VM**  
- **Updating Packages**  
  ```bash
  sudo apt update && sudo apt upgrade -y  # (Ubuntu/Debian)
  sudo yum update -y                     # (RHEL/CentOS)
  ```
- **Installing Web Server (Apache/Nginx)**  
  ```bash
  sudo apt install apache2 -y     # Ubuntu  
  sudo systemctl start apache2  
  sudo systemctl enable apache2  

  sudo yum install nginx -y       # RHEL/CentOS  
  sudo systemctl start nginx  
  sudo systemctl enable nginx  
  ```
- **Opening Firewall for Web Traffic**  
  ```bash
  sudo ufw allow 80/tcp   # Ubuntu  
  sudo firewall-cmd --add-port=80/tcp --permanent && sudo firewall-cmd --reload  # RHEL  
  ```

### **6. Security Best Practices**  
- **Disable Root Login** (`/etc/ssh/sshd_config`)  
  ```bash
  PermitRootLogin no
  ```
- **Change Default SSH Port**  
  ```bash
  sudo nano /etc/ssh/sshd_config
  Port 2222
  sudo systemctl restart sshd
  ```
- **Use Azure NSG (Network Security Groups)**  
  - Allow only necessary ports (e.g., 22 for SSH, 80/443 for Web)  
  - Block unnecessary inbound traffic  

### **7. Monitoring and Backup**  
- **Enable Azure Monitor** for performance metrics  
- **Set Up Auto-shutdown** to save cost  
- **Enable Azure Backup** for VM snapshots  

### **8. Deleting Azure Linux VM**  
- Delete VM but keep the disk:  
  ```bash
  az vm delete --resource-group <resource-group> --name <vm-name> --yes
  ```
- Delete VM with Disk and Network Interface:  
  ```bash
  az resource delete --ids $(az vm show --resource-group <resource-group> --name <vm-name> --query "id" -o tsv)
  ```

This provides a complete guide for deploying and managing a **Linux Virtual Machine on Azure**. 🚀