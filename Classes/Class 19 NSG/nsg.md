
### **Azure Network Security Groups (NSG) - Explained**  

#### **1. What is Azure NSG?**  
- Azure Network Security Group (NSG) is a security feature that controls inbound and outbound traffic to Azure resources.  
- It acts as a virtual firewall, filtering traffic based on defined security rules.  
- NSGs can be associated with **subnets** or **network interfaces (NICs) of virtual machines** to enforce security policies.  

#### **2. Key Components of NSG**  
- **Security Rules:** Define allowed or denied traffic based on priority, source, destination, port, and protocol.  
- **Inbound Rules:** Control incoming traffic to Azure resources.  
- **Outbound Rules:** Control outgoing traffic from Azure resources.  
- **Priority:** Rules are processed in ascending order, from **lowest (100) to highest (4096)**.  
- **Default Rules:** Pre-configured rules that allow essential Azure services while blocking unwanted traffic.  
- **Custom Rules:** User-defined rules to allow/deny specific traffic.  

#### **3. NSG Rule Structure**  
Each rule consists of:  
- **Priority:** A number from **100 to 4096** (lower numbers take precedence).  
- **Name:** A unique identifier for the rule.  
- **Source & Destination:** Can be an IP range, Virtual Network, Internet, or Any.  
- **Port Range:** Specifies allowed or blocked port numbers (e.g., 80 for HTTP, 443 for HTTPS).  
- **Protocol:** Can be **TCP, UDP, or Any**.  
- **Direction:** Either **Inbound** or **Outbound**.  
- **Action:** **Allow** or **Deny** traffic.  

#### **4. Default NSG Rules in Azure**  
- **Inbound:**  
  - **Allow VNet Inbound (65000)** – Allows communication within the Virtual Network.  
  - **Allow Load Balancer Inbound (65001)** – Allows Azure Load Balancer probes.  
  - **Deny All Inbound (65500)** – Blocks all other inbound traffic.  
- **Outbound:**  
  - **Allow VNet Outbound (65000)** – Allows outbound traffic within the Virtual Network.  
  - **Allow Internet Outbound (65001)** – Allows all outbound traffic to the Internet.  
  - **Deny All Outbound (65500)** – Blocks all other outbound traffic.  

#### **5. Associating NSG with Azure Resources**  
- **Subnet Level:** Controls traffic for all resources inside the subnet.  
- **NIC Level:** Controls traffic specific to an individual VM.  
- **NSG Processing Order:**  
  - If both **Subnet NSG and NIC NSG** are applied, **both** must allow the traffic for it to pass.  

#### **6. Best Practices for NSG**  
- Follow the **Principle of Least Privilege** (Allow only required traffic).  
- Use **Application Security Groups (ASG)** for simplified rule management.  
- Regularly review and optimize rules to remove unnecessary access.  
- **Log and Monitor** NSG rules using Azure Monitor and NSG Flow Logs.  
- **Avoid overly permissive rules** like “Allow Any” unless necessary.  

#### **7. NSG vs Azure Firewall**  
| Feature | NSG | Azure Firewall |  
|---------|-----|---------------|  
| Traffic Filtering | Layer 3 & 4 (IP & Ports) | Layer 3, 4, & 7 (Deep Packet Inspection) |  
| Stateful Inspection | Yes | Yes |  
| Application Rules | No | Yes |  
| Threat Intelligence | No | Yes |  
| Logging | Basic Logging | Advanced Logging & Threat Detection |  

#### **8. Real-World Use Cases**  
- **Secure Web Applications**: Restrict access to only specific IPs and ports (e.g., allow 443 for HTTPS traffic).  
- **Internal Services Protection**: Limit database access within a Virtual Network.  
- **Multi-Tier Architecture**: Define NSG rules to isolate Web, App, and Database layers.  
- **DDoS Mitigation**: Block suspicious inbound traffic at NSG before reaching the VM.  

Would you like me to add any **diagrams or practical scenarios** for better understanding? 🚀