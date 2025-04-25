## **Blocking Internet Access on Azure VM Using Azure Firewall**  

Azure Firewall is a cloud-based security service that helps control inbound and outbound traffic. You can use it to block internet access on an Azure VM while allowing required services.

---

### **1. Deploy Azure Firewall**  
#### **Step 1: Create an Azure Firewall Instance**
1. Go to **Azure Portal → Create a Resource → Search "Azure Firewall" → Click Create**.  
2. Select the **Subscription & Resource Group**.  
3. Provide a **Firewall Name** and select the **Region**.  
4. Choose the **Virtual Network (VNet)** where the VM resides.  
5. Create a new **Subnet** named `AzureFirewallSubnet` (mandatory for Azure Firewall).  
6. Select **Firewall Policy** and configure with default settings.  
7. Click **Review + Create** → Deploy.

---

### **2. Configure Route Table to Force Traffic via Firewall**  
#### **Step 2: Create a Route Table**
1. Navigate to **Azure Portal → Route Tables → Create a Route Table**.  
2. Enter **Name, Region, and Resource Group**.  
3. Click **Create**.

#### **Step 3: Add a Custom Route**
1. Open the newly created Route Table.  
2. Go to **Routes → Add Route** and configure:
   - **Route Name:** Block-Internet  
   - **Address Prefix:** `0.0.0.0/0`  
   - **Next Hop Type:** Virtual Appliance  
   - **Next Hop Address:** Private IP of Azure Firewall (found in Azure Firewall Overview)  
3. Click **Save**.

#### **Step 4: Associate Route Table with VM Subnet**
1. Go to the Route Table and select **Subnets**.  
2. Click **Associate** and choose the VM’s **Subnet**.  
3. Click **OK**.

---

### **3. Configure Firewall Rules to Block Internet**  
#### **Step 5: Modify Firewall Policy**
1. Open **Azure Firewall** and go to **Firewall Policies**.  
2. Under **Network Rules**, delete any default outbound allow rules.  
3. Under **Application Rules**, block all outbound traffic:
   - **Rule Collection Name:** Block-Internet  
   - **Priority:** 100  
   - **Action:** Deny  
   - **FQDNs:** `*` (blocks all internet access)  
4. Click **Save**.

---

### **4. Testing and Validation**  
#### **Step 6: Verify Internet Block**
1. Connect to the Azure VM via **RDP/SSH**.  
2. Open a browser and try accessing `google.com`—it should be blocked.  
3. Run `ping 8.8.8.8`—it should time out.

#### **Step 7: Allow Required Services (Optional)**
- If the VM needs access to **Azure services (e.g., Updates, ACR, etc.)**, create **Allow Rules**:
  - **Application Rules** → Allow `*.azure.com`
  - **Network Rules** → Allow specific outbound IP ranges

---

### **Best Practices**
- **Use Private Endpoints** for Azure services to avoid internet dependency.  
- **Monitor Logs** using **Azure Monitor & Log Analytics**.  
- **Enable Just-In-Time (JIT) Access** for controlled VM access.  

This setup ensures the VM cannot access the internet while maintaining security and compliance. 🚀

# **Azure DDoS Protection**  

Azure DDoS Protection helps safeguard Azure resources against **Distributed Denial-of-Service (DDoS) attacks** by automatically detecting and mitigating malicious traffic.

---

## **1. Types of Azure DDoS Protection**
### **a) Azure DDoS Protection Basic**
- **Enabled by default** for all Azure services.  
- **Protects against common DDoS attacks** at the network level.  
- **No additional cost** but provides only basic mitigation.

### **b) Azure DDoS Protection Standard**
- **Advanced protection** for Virtual Networks (VNets).  
- **Real-time attack detection** and mitigation.  
- **Provides telemetry, analytics, and alerts** in Azure Monitor.  
- **24/7 support from Microsoft DDoS Rapid Response Team**.  
- **Custom policies** to allow/block specific traffic patterns.  
- **Cost:** Based on protected resources.

---

## **2. How Azure DDoS Protection Works**
- **Traffic Monitoring:** Constantly analyzes incoming traffic for anomalies.  
- **Automatic Mitigation:** When an attack is detected, it blocks malicious traffic while allowing legitimate traffic.  
- **Integration with Web Application Firewall (WAF):** Adds extra protection for web applications.  

---

## **3. Configuring Azure DDoS Protection Standard**
### **Step 1: Create a DDoS Protection Plan**
1. Go to **Azure Portal → Search "DDoS Protection Plans" → Click Create**.  
2. Select **Subscription & Resource Group**.  
3. Enter a **Name** and choose a **Region**.  
4. Click **Review + Create → Create**.  

### **Step 2: Enable DDoS Protection for a Virtual Network**
1. Navigate to **Azure Portal → Virtual Networks**.  
2. Select the VNet you want to protect.  
3. Go to **DDoS Protection** under Settings.  
4. Click **Enable DDoS Protection Standard** and select the created **DDoS Protection Plan**.  
5. Click **Save**.

### **Step 3: Configure Alerts and Monitoring**
1. Go to **Azure Monitor → Alerts → Create Alert Rule**.  
2. Select **Target** as the protected VNet.  
3. Choose a **Condition** (e.g., "DDoS Attack detected").  
4. Set up **Action Group** for email/SMS notifications.  
5. Click **Create**.

---

## **4. Features of Azure DDoS Protection Standard**
- **Traffic Analytics:** Logs attack details for analysis.  
- **Adaptive Real-Time Protection:** Detects unusual traffic patterns dynamically.  
- **Cost Protection:** Offers service credits for false-positive mitigation events.  
- **Integration with WAF:** Enhances security for web applications.  

---

## **5. Best Practices for DDoS Protection**
- **Enable DDoS Protection Standard for critical workloads**.  
- **Use Web Application Firewall (WAF) with Azure Application Gateway** for Layer 7 protection.  
- **Monitor traffic with Azure Monitor and Log Analytics**.  
- **Use rate-limiting rules and Network Security Groups (NSGs) for additional filtering**.  

This setup ensures **protection against large-scale DDoS attacks**, keeping applications highly available and secure. 🚀