

## **AWS to Azure Migration using Azure Migrate - Part 1: Assessment**

### **Overview**

Azure Migrate is a Microsoft tool that helps assess and migrate on-premises or cloud-based workloads (e.g., AWS) to Azure. The **Assessment phase** evaluates the readiness, sizing, and cost of migrating AWS instances to Azure VMs.

---

## **1. Prerequisites**

* **Azure Subscription**
* **Admin access to AWS instances**
* **Azure Migrate project created** in Azure portal
* **Outbound internet access** from AWS VMs (or ExpressRoute/VPN if applicable)

---

## **2. Set Up Azure Migrate Project**

* Go to **Azure Portal > Azure Migrate**
* Click **+ Add Tool** under "Assess and Migrate"
* Select **‘Servers’** as the migration scenario
* Create or select an existing **Azure Migrate project**
* Choose **"Discovery and Assessment"** tool – Microsoft tool

---

## **3. Download and Set Up Azure Migrate Appliance**

### a. Download Appliance:

* Download the **Azure Migrate Appliance OVA/Installer**
* Deploy it in AWS (as a VM)

  * OS: Windows Server (for installer)
  * RAM: 16 GB, Disk: 80 GB, 4 vCPUs

### b. Configuration:

* Provide Azure Migrate Project Key during setup
* Appliance connects to Azure securely
* Discover AWS VMs using:

  * **vCenter (if used)**
  * **IP range scan**
  * Or **import CSV** for disconnected environments

---

## **4. Discovery Phase**

* Appliance collects metadata from AWS VMs:

  * CPU, memory, disk, NICs, OS, etc.
  * Performance data (if enabled) over 1 day to 1 month
* After discovery, data is pushed to Azure Migrate project

---

## **5. Create Assessment**

### Assessment Types:

* **Azure Readiness**
* **Cost Estimation**
* **Sizing Recommendations**

### Configuration Options:

* Target Azure Region
* Pricing Tier (Pay-as-you-go, Reserved Instances)
* Performance-based or As-on-prem sizing
* Reserved Capacity (1- or 3-year)
* Offer and currency
* Include Azure Hybrid Benefit (AHB) for OS licensing savings

---

## **6. Review Assessment**

* **Readiness Report**:

  * Shows which VMs are ready to migrate
  * Lists unsupported features or dependencies

* **Cost Estimation**:

  * Estimated monthly cost in Azure
  * Based on size, usage, pricing tier

* **Sizing Recommendations**:

  * Suggested VM SKU in Azure
  * Based on actual usage (performance-based) or existing size

---

## **7. Export & Share Reports**

* Download assessment reports in **Excel** or **CSV**
* Share with stakeholders or planning team

---

## **8. Next Steps After Assessment**

* Identify remediation steps for **non-ready VMs**
* Plan dependencies and group migration sets
* Move to **Part 2: Migration Phase**

---

W
