

### ✅ **Azure Monitoring Agent (AMA)**

**Overview:**
- The Azure Monitoring Agent is the **new unified agent** for collecting monitoring data from **Azure and on-premises virtual machines**.
- It replaces legacy agents like **Log Analytics Agent (MMA)**, **Telegraf**, and **Diagnostics Extension**.

**Features:**
- Collects performance data, event logs, syslogs, and custom logs.
- Supports **data collection rules (DCRs)** for centralized configuration.
- Supports Windows and Linux VMs (Azure, on-prem, other clouds).
- Sends data to **Log Analytics workspace**, **Azure Monitor Metrics**, or both.
- Better security with **managed identity** support.

**Benefits over legacy agents:**
- Unified configuration and data pipeline.
- Better performance and lower overhead.
- No dependency on the workspace at install time.
- Native support for **Azure Arc-enabled servers**.

**Installation:**
- Use **Azure Policy**, **Azure CLI**, **PowerShell**, or **VM Extension**.
- Configure using **Data Collection Rules (DCRs)**.

**Use Cases:**
- Centralized logging and monitoring.
- Custom log and metrics collection.
- Better integration with Azure Monitor and Sentinel.

---

### 🌐 **Azure Network Watcher**

**Overview:**
- A regional service for monitoring and diagnosing network conditions in Azure.
- Helps analyze and diagnose issues with **network traffic**, **connections**, **NSG rules**, and **routing**.

**Key Features:**

1. **Topology Viewer**  
   - Visualizes your network resources (VNet, NICs, NSGs, etc.).

2. **Connection Troubleshoot**  
   - Checks connectivity between a source and destination (VM to VM, IP, FQDN).

3. **IP Flow Verify**  
   - Determines if traffic is allowed/denied by NSG rules.

4. **Next Hop**  
   - Shows the next hop in the routing path from a VM to a destination.

5. **Effective Security Rules**  
   - Shows effective NSG rules applied on a NIC.

6. **Packet Capture**  
   - Captures traffic on a VM’s NIC for deep analysis.

7. **Traffic Analytics**  
   - Provides flow analytics using **NSG Flow Logs** and **Log Analytics**.

8. **Connection Monitor**  
   - End-to-end connection monitoring and alerting across regions and networks.

**Use Cases:**
- Troubleshooting connectivity issues.
- Monitoring traffic flow and security.
- Verifying NSG and routing configurations.
- Capturing packets for deep inspection.

