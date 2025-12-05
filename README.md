# ADF_documentation


# ⭐ Azure Key Features and Services — Overview with Examples & Scenarios

This document provides a beginner-friendly yet detailed explanation of some of Microsoft's core Azure concepts including subscriptions, resource groups, the Azure Portal, and command-line interaction tools such as Azure CLI and PowerShell.

---

## 1. Key Features and Services

Azure provides a vast ecosystem of cloud-based services such as compute, networking, analytics, databases, and storage. These services help organizations deploy scalable and secure applications worldwide.

---

## 1.1 🌍 Global Data Centers

Microsoft Azure operates through a vast global network of data centers organized into:

- **Regions**
- **Availability Zones**
- **Edge Locations**

A **Region** is a geographical area like:
- *East US*
- *West Europe*
- *Central India*

Each region typically has multiple data centers for redundancy.

### Why Regions Matter?

- **Compliance Requirements**  
  For example, an Indian bank may legally require customer data to remain in India, so they choose `Central India`.

- **Low Latency**  
  A gaming app targeting Europe users should deploy in `West Europe` or `North Europe` for faster response times.

### Real-World Scenario

A ride-sharing application (like Uber) hosting servers only in `US East` would result in slow performance for users in India. Deploying an additional replica in `Central India` improves latency and user experience drastically.

---

## 1.2 🧾 Azure Subscription and Resource Groups

Azure uses a **Subscription** model to organize and bill services.

---

### 1.2.1 Creating an Azure Subscription

A subscription represents an account with pricing and billing rules. Every service deployed in Azure is tied to a subscription.

#### Example
- You create a subscription named:  
  `Mahendra-Student-Subscription`
  
- Under this subscription, you deploy:
  - 1 Virtual Machine  
  - 2 Storage Accounts  
  - 1 SQL Database  
  - 1 Virtual Network  

All usage across these services appears as a single consolidated bill.

#### Real-World Use Case

A multinational company may have multiple subscriptions:
| Subscription Name | Purpose |
|------------------|---------|
| DEV Subscription | Testing & experimental workloads |
| QA Subscription | Deployment testing | 
| PROD Subscription | Live environment serving customers |

This separation avoids accidental impacts and ensures cost governance.

---

### 1.2.2 Managing Resources in Resource Groups

A **Resource Group (RG)** is a logical container used to organize Azure resources.

Example RG:
```

RG-StudentProject

```

Inside it, you may store:
- VMs
- Virtual Networks
- Storage Accounts

#### Benefits

| Feature | Description |
|--------|-------------|
| Grouping | Easy to manage related services |
| Access Control | Apply RBAC policies to specific groups |
| Cost Tracking | Cost per project/team |
| Deletion Control | Delete all resources together |

#### Scenario

A college team working on a final-year project creates:

```

Subscription: Student-FinalProject
Resource Group: RG-ML-ImageProcessing
Resources: VM + Blob Storage + App Service + DB

```

When the project ends, deleting the resource group removes everything — saving cost.

---

## 1.3 🖥️ Azure Workspace and UI

Azure provides multiple ways to manage services:

- Azure Portal (GUI)
- Azure CLI
- Azure PowerShell
- REST API
- Infrastructure-as-Code (ARM, Bicep, Terraform)

---

### 1.3.1 Navigating the Azure Portal

Azure Portal:  
➡ https://portal.azure.com

Through the portal you can:
- Deploy and manage resources
- Configure monitoring and logs
- View subscription billing
- Apply security policies

#### Example

To create a Virtual Machine:
```

Home → Virtual Machines → Create → Windows/Linux → Configure Network → Review + Create

````

---

### 1.3.2 Overview of Dashboard and Resource Management

The dashboard provides:
- Health monitoring
- Resource insights
- Cost analysis charts
- Recently accessed services

#### Scenario

An IT admin customizes dashboards to monitor:

| Tile | Purpose |
|------|---------|
| VM Metrics | CPU usage, traffic |
| Billing Cost Chart | Track spending |
| Alerts Panel | Monitor outages |

---

### 1.3.3 Azure CLI and PowerShell

Azure supports automation using CLI tools.

---

### 1.3.4 Command-Line Interface Options for Azure

#### Azure CLI Example Commands:

Login:
```sh
az login
````

Create a Resource Group:

```sh
az group create --name RG-Demo --location "East US"
```

Create a Storage Account:

```sh
az storage account create --name mahendrastorage123 --resource-group RG-Demo --location eastus
```

---

### 1.3.5 Scripting with PowerShell

PowerShell is powerful for automation and DevOps activities.

#### Example PowerShell Commands:

```powershell
Connect-AzAccount

New-AzResourceGroup -Name "RG-Lab" -Location "Central India"

New-AzStorageAccount -ResourceGroupName "RG-Lab" `
-Name "mahendrapsstorage" `
-Location "Central India" `
-SkuName "Standard_LRS"
```

#### Real-World Scenario

A DevOps engineer automates the deployment of **50 virtual machines** using a PowerShell script rather than creating them manually.

---

## 📌 Summary

| Feature          | Purpose                                 |
| ---------------- | --------------------------------------- |
| Regions          | Deploy globally and reduce latency      |
| Subscription     | Billing boundary for services           |
| Resource Groups  | Logical structure for management        |
| Azure Portal     | UI for managing services                |
| CLI & PowerShell | Automation and infrastructure scripting |

Azure gives developers and enterprises flexibility to deploy, manage, and scale applications efficiently.

---



# Azure Storage, Data Factory & Integration Overview

This document provides a simplified overview of Azure Storage services, Azure Data Factory concepts, and integration best practices with examples and real-world scenarios.

---

## 🚀 1. Azure Storage Account Types

Azure Storage provides scalable and secure cloud storage with support for multiple data formats.

### 1.1 Blob Storage
Used for storing unstructured data such as images, CSV files, backups, or logs.

**Real-Time Example:**  
A data engineering team stores raw ingestion files in Blob storage before ETL.

### 1.2 File Storage
Managed SMB file shares accessible from cloud or on-prem resources.

**Real-Time Example:**  
Virtual machines mount Azure File Share for shared log storage.

### 1.3 Table Storage
A NoSQL key-value store for structured but non-relational data.

**Real-Time Example:**  
IoT telemetry data stored for scalable fast lookup.

### 1.4 Queue Storage
Messaging store for asynchronous communication between services.

**Real-Time Example:**  
Trigger downstream processing when a file is uploaded.

---

## ⚙️ 2. Azure Data Factory (ADF)

Azure Data Factory is a cloud-based ETL/ELT service used for data orchestration.

### 2.1 Introduction
Used to ingest, transform, schedule, and load data across on-prem and cloud sources.

### 2.2 Key Components

| Component | Description |
|----------|-------------|
| Pipeline | Workflow containing activities |
| Dataset | Schema representation of data |
| Linked Service | Connection metadata to sources |

**Real Scenario:**  
Daily ETL pipelines run at midnight to load data from an on-prem database to Azure Synapse.

---

## 🔐 3. Azure Key Vault

Used to securely store sensitive information like passwords, API keys, and certificates.

**Real Scenario:**  
ADF pipelines use Key Vault to retrieve SQL credentials securely without exposing them.

---

## 🔗 4. Integration with Azure Services

### 4.1 Datasets & Linked Services
Datasets reference data, while Linked Services define connections.

### 4.2 Integration Runtime (IR)

| Type | Purpose |
|------|---------|
| Azure IR | Cloud-to-cloud movement |
| Self-Hosted IR | On-prem to cloud |
| Managed VNet IR | Secure data movement in restricted networks |

### 4.3 Triggers & Monitoring
ADF supports Scheduling, Event-based triggers, and monitoring through the Azure portal with alerts.

**Real Scenario:**  
A file arriving in Blob Storage automatically triggers a pipeline using event triggers.

---

---

# 📘 Azure Data Factory + Databricks + DevOps README

---

## **1️⃣ Activities in Azure Data Factory (ADF)**

Activities in ADF define **what action** should be performed. There are three major types:

* **Data Movement Activities**
* **Execution Control Activities**
* **Control Flow Activities**

---

### **1.1 Data Movement Activities**

Used to move data between supported sources and destinations using **Copy Activity**.

#### **1.1.1 Azure Blob Storage Source/Sink:**

| Scenario | Example                                                                    |
| -------- | -------------------------------------------------------------------------- |
| Source   | Read CSV files from Blob Storage and copy to SQL Database                  |
| Sink     | Store transformed files from SQL/Databricks back to Blob for storage layer |

**Example use case:**

> Source: `raw/customer_data.csv` in Blob → Sink: Azure SQL `dbo.Customers`

#### **1.1.2 Azure SQL Database Source/Sink:**

Used when SQL Database is either the source or destination.

**Real Example:**

> Copy incremental sales data from SQL and store into ADLS Gen2 for reporting.

---

### **1.2 Execution Control Activities**

These help control the **workflow** logic and orchestration.

#### **1.2.1 Execute Pipeline Activity:**

Used to run a pipeline from another pipeline.

**Example:**

> Master Pipeline → Executes pipeline to copy raw → Executes pipeline for validation → Executes data transformation.

#### **1.2.2 If Condition Activity:**

Executes logic based on true/false output.

**Real Scenario:**

> If today's file exists → proceed with load, else send failure notification.

#### **1.2.3 ForEach Activity:**

Loops through a collection of items.

**Example:**

> Iterate through multiple folders/files: `jan`, `feb`, `mar` and load data.

#### **1.2.4 Web Activity:**

Calls REST API endpoint.

**Use Case:**

> Trigger Databricks job or external API before/after pipeline run.

---

### **1.3 Control Flow Activities**

These activities control pipeline structure and behaviour.

#### **1.3.1 Wait Activity:**

Pauses execution for a given time.

**Example:** Wait 5 mins before retrying external API.

#### **1.3.2 Until Activity:**

Loops until a logical condition becomes true.

**Example:** Continue checking file arrival every 10 mins until file exists.

#### **1.3.3 Get Metadata Activity:**

Fetch metadata like file size, existence, folder count.

**Real Case:** Check if today's file exists in storage.

#### **1.3.4 Lookup Activity:**

Fetch single row from a data store.

**Example:** Lookup valid file date or expected record count.

#### **1.3.5 Stored Procedure Activity:**

Runs stored procedure in SQL.

**Use Case:**

> After data load, execute stored procedure for cleansing or merge operation.

---

### **1.4 Pipelines and Triggers**

Pipelines are containers of activities.

Triggers schedule and execute pipelines.

| Trigger Type    | Use Case                                |
| --------------- | --------------------------------------- |
| Schedule        | Run every day at 1 AM                   |
| Tumbling Window | Time-sliced batch data like hourly logs |
| Event Trigger   | Detect file arrival in storage          |

---

## **2️⃣ Azure Databricks Notebooks**

### **2.1 Overview of Azure Databricks Notebook Integration**

ADF can call Databricks notebooks for processing and transformation.

**Use Case:** To perform ETL processing using PySpark.

### **2.2 Notebook Orchestration**

Triggered via:

* **Databricks Notebook Activity**
* **REST Web Activity**

**Example:**

> Copy → Validate → Databricks transform → Load curated layer.

---

## **3️⃣ Azure DevOps CI/CD Integration**

### **3.1 Continuous Integration and Deployment**

Used for:

* Version control of ADF JSON using Git
* Automated deployment to higher environments (Dev → QA → Prod)

**Example Flow:**

```
Developer commits changes → Pull Request → CI pipeline validates JSON → CD publishes ARM templates to prod
```

---





