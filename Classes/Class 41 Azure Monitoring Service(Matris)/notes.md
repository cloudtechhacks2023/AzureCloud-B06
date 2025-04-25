
## 🔍 **Azure Monitoring Services – Notes**

---

### ✅ **Introduction to Azure Monitoring**

- Azure Monitor is a service that helps you monitor the **performance, availability, and health** of your Azure resources.
- It collects, analyzes, and visualizes **metrics and logs** from your infrastructure and applications.
- Azure Monitor enables you to set **alerts**, create **dashboards**, and trigger **automation** based on insights.

---

### 📦 **Main Components of Azure Monitor**

#### 1. **Metrics**
- Numerical performance data collected in near real-time.
- Comes in a **time-series** format.
- Default platform metrics are automatically collected for most Azure resources.

#### 2. **Logs (Log Analytics)**
- Collects structured and unstructured event and diagnostic data.
- Data is stored in a Log Analytics workspace and can be queried using **Kusto Query Language (KQL)**.

#### 3. **Alerts**
- Allow you to define rules to trigger **notifications or actions** when certain thresholds are met.
- Supports email, SMS, webhooks, Logic Apps, and Azure Automation.

#### 4. **Application Insights**
- Designed for monitoring **application performance and usage**.
- Collects telemetry from applications (server-side and client-side) to help detect failures and performance issues.

#### 5. **Diagnostic Settings**
- Allows you to route **metrics and logs** to destinations like **Log Analytics, Event Hub, or Storage Account**.

#### 6. **Workbooks**
- Used to create **custom dashboards** and visualizations.
- Combines text, analytics queries, metrics, and parameters into rich interactive reports.

#### 7. **Network Watcher**
- Helps monitor and diagnose network issues.
- Tools include: **NSG flow logs**, **Connection troubleshoot**, **Packet capture**, etc.

---

## 📊 **Azure Metrics – In-Depth**

### 🧠 **What Are Metrics?**

- Metrics are **numerical values** representing the **state and performance** of a resource.
- They are collected in **time-series** format — i.e., values are associated with timestamps.
- Examples: CPU utilization, memory usage, disk IOPS, network traffic.

---

### 📚 **Types of Metrics**

#### 1. **Platform Metrics**
- Automatically collected by Azure for most resources.
- Examples:
  - **Virtual Machine**: CPU Percentage, Disk Read/Write, Network In/Out
  - **Storage Account**: Transactions, Egress
  - **Azure SQL Database**: DTU usage, Deadlocks

#### 2. **Custom Metrics**
- Created and sent manually by users via Application Insights, Azure SDKs, or REST APIs.
- Useful when monitoring custom applications or business logic.

---

### 🏗️ **Metric Structure**

Every metric in Azure has the following elements:

1. **Namespace** – Identifies the group of metrics (e.g., Microsoft.Compute/virtualMachines)
2. **Metric Name** – The actual metric you want to monitor (e.g., `Percentage CPU`)
3. **Time Series** – A stream of timestamped values
4. **Dimensions** – Optional properties to break down the metric (e.g., per disk, per NIC)

---

### 🔍 **Metric Aggregation Types**

Azure Monitor supports several types of aggregation for metrics:

- **Average** – Mean value over the time period
- **Minimum** – Lowest recorded value
- **Maximum** – Highest recorded value
- **Total** – Sum of values
- **Count** – Number of samples in the time window

---

### 📈 **Use Cases of Azure Metrics**

- **Monitor performance** of Azure resources (CPU, memory, disk, etc.)
- **Create alert rules** based on specific conditions (e.g., CPU > 80%)
- **Enable autoscaling** for VM scale sets or App Services
- **Visualize metrics** using dashboards and workbooks

---

### 🛠️ **Working with Metrics in Azure Portal**

Steps to view metrics:

1. Go to **Azure Portal → Monitor → Metrics**
2. Select the **resource** you want to monitor
3. Choose a **metric** (e.g., CPU Percentage)
4. Set **aggregation type** and **time range**
5. Optionally filter by **dimensions** (e.g., per disk or per NIC)

---

### 🔔 **Creating Metric Alerts**

1. Define the **resource and metric** to monitor.
2. Set the **condition** (e.g., CPU > 80% for 5 minutes).
3. Choose **evaluation frequency** and **action group** (email, SMS, Logic App, etc.).
4. Save and test the alert.

---

