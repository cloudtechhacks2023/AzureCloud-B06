
### ✅ Azure Monitoring Overview
- **Azure Monitor** is a centralized service that monitors the performance and health of Azure resources.
- It provides tools to **collect, analyze, and take action** on logs, metrics, and alerts.

---

### 🔔 Alerts
- **Purpose**: Alerts notify you when a resource's performance or health crosses a defined threshold.
- **Types of Alerts**:
  - **Metric Alerts**: Based on real-time numeric values (e.g., CPU > 80%)
  - **Activity Log Alerts**: Based on Azure resource management events
  - **Log Alerts**: Based on queries run in Log Analytics (KQL)
- **Main Components**:
  - **Scope**: The targeted resource or resource group
  - **Condition**: The rule to trigger an alert (e.g., CPU > 90%)
  - **Action Group**: Defines what happens after the alert (e.g., Email, SMS, Webhook, Azure Function)
  - **Alert Rule**: A complete alert configuration combining the above

---

### 📊 Log Analytics Workspace
- **Log Analytics** is a tool within Azure Monitor used to collect, store, and query logs.
- Uses **KQL (Kusto Query Language)** to analyze data.
- **Log Analytics Workspace**:
  - A centralized place to store logs from multiple resources
  - Allows cross-resource querying and correlation
  - Offers data retention settings for compliance and cost control

---

### 🧠 Analytics Agent (Log Analytics Agent)
- Also called **Microsoft Monitoring Agent (MMA)**
- This is an agent that sends data from Azure VMs or on-premises machines to the **Log Analytics Workspace**.
- **Key Features**:
  - Collects performance counters, event logs, IIS logs, etc.
  - Supports both Windows and Linux
  - Being **deprecated** in favor of **Azure Monitor Agent (AMA)**

---

### 🛠️ Diagnostic Settings / Diagnostic Agent
- **Diagnostic Settings** allow you to export resource logs and metrics.
- Possible destinations:
  - Log Analytics Workspace
  - Azure Storage Account
  - Event Hub
- **Supported Resources**: VMs, App Services, Azure SQL, Key Vault, etc.
- Useful for continuous monitoring without needing an agent (platform-level logging)
- This is more of a configuration setting than an actual agent

---

### ⚠️ Important Notes
- **Azure Monitor Agent (AMA)** is the **new recommended agent**.
  - It offers better performance and central management.
  - Uses **Data Collection Rules (DCRs)** to control what data to collect and from where.
- Older agents like **MMA** and **Diagnostic Extension** are being phased out and replaced with AMA.

