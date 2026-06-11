# Automated Fraud Risk Analyzer & Real-Time Alerting Pipeline

An enterprise-grade, event-driven automation pipeline designed to ingest transaction data, evaluate multi-layered financial risk rules via custom JavaScript logic, and execute conditional data logging and multi-tiered email routing. Built natively inside **n8n**, this system bridges operational data stores with real-time incident response mechanisms.

---

## 📐 Project Architecture & Visual Workflow

The diagram below illustrates the active visual layout of the automated pipeline inside the n8n orchestrator dashboard:

### 1. Central Core Workflow Engine
[My workflow 3 (1).json](https://github.com/user-attachments/files/28853112/My.workflow.3.1.json)
<img width="1825" height="841" alt="WORKFLOW ARCHITECTURE" src="https://github.com/user-attachments/assets/5badfee2-70ce-4956-9b98-dbfd4a66ebcc" />

*Figure 1: Complete node topology routing from automated ingestion to multi-branch JavaScript validation gates and notification layers.*

### 2. Live Database & Transaction Ledger (Google Sheets)
<img width="1847" height="666" alt="GOOGLE SHEET" src="https://github.com/user-attachments/assets/35200d89-d533-4c52-9d59-2fa83f96c0d7" />

*Figure 2: Production transaction sheet displaying calculated variables like Risk Scores, Triggered Rules, and structural Risk Status outputs synced dynamically.*

### 3. Incident Severity Payloads (Real-Time Communication Output)
The automated system triggers distinct communication packages depending on the risk severity computed:

#### 🚨 Incident Type A: High-Risk Escalation Alert
<img width="1583" height="852" alt="HIGH RISK MAIL" src="https://github.com/user-attachments/assets/61c9b548-bf04-4b3d-a321-ef2d4cdb7322" />

*Figure 3: Instant HTML alert dispatched via Gmail gateway enforcing instant account suspension and immediate risk management team intervention.*

#### ⚠️ Incident Type B: Medium-Risk Flagged Alert
<img width="1557" height="841" alt="MEDIUM RISK MAIL" src="https://github.com/user-attachments/assets/81fe9fe2-7de5-4615-a769-b0af9e6a7d6e" />

*Figure 4: Automated shadow-monitoring notice transmitted to queue specialists for detailed profile investigation.*

---

## 🚀 Pipeline Data Process Lifecycle

The architecture utilizes a modular router-pattern to ingest, analyze, and dispatch records efficiently:

1. **Ingestion:** Pulls live transaction records dynamically from dedicated data sheets (`Transaction_Data`).
2. **Analysis Engines:** A centralized JavaScript processing layer maps schemas, cleans dirty metrics, tracks historical flags, and computes risk scores across 10+ vectors simultaneously.
3. **Conditional Routing:** An array of structured `If-Else` logic gates segment flows based on final algorithmic severity tiers (`HIGH RISK`, `MEDIUM RISK`, `LOW RISK`, `CLEAR`).
4. **Data Synchronization:** Updates target spreadsheets with generated audit metrics (`Rules_Triggered`, `Risk_Score`, `Fraud_Status`) mapping precisely to unique key structures (`Transaction_ID`).
5. **Real-Time Notification Gateways:** Distributes isolated HTML/CSS formatted email payloads dynamically matching the triage severity requirement.

---

## 🛠️ Tech Stack & Integrations

* **Orchestration Engine:** n8n (Workflow Automation Engine)
* **Computation Core:** Node.js / JavaScript (ES6 Execution Layer)
* **Data Layer:** Google Sheets API v4
* **Communication Gateway:** Gmail OAuth2 Framework
* **Configuration Syntax:** JSON

---

## 🧠 Risk Assessment Engine (Rule Configurations)

The custom JavaScript logic evaluates incoming ledger feeds against strict enterprise threat patterns. Every matched rule increments a rolling numerical `Risk_Score`:

| Rule Code | Vector Target | Threat Condition Specification |
| :--- | :--- | :--- |
| **R1:HighValue** | Velocity Check | Gross transaction volume exceeds ₹50,000 |
| **R2:RoundAmount** | Behavior Pattern | Exact common laundering figures (₹10k, ₹50k, ₹100k) |
| **R3:MicroProbe** | Account Lifecycle | Small probe volumes (< ₹10) on highly novel accounts (< 30 days) |
| **R4:VelocityBreach**| Geolocation | Impossible physical transit constraints flagged (`Impossible_Travel = Yes`) |
| **R5:MulePattern** | Liquidity Drain | Sudden massive fund outflow balance ratio metrics exceeding 90% |
| **R6:OffHours** | Temporal Integrity | High-risk timing patterns occurring between 01:00 AM and 04:00 AM |
| **R7:DormantSpike** | Historical Delta | Extended dormancy accounts (> 90 days) with less than 2 historical transactions |
| **R8:FirstHighVal** | Cold-Start Risk | First-time transaction (`Prev_Txn_Count = 0`) exceeding structural limit of ₹40,000 |
| **R9:ForeignLoc** | Perimeter Security | Source point marked as unknown origins or non-domestic foreign zones |
| **R11:UPIAbuse** | Channel Integrity | High-volume UPI transfer mechanics exceeding arbitrary limit thresholds (> ₹5,000) |
| **R12:CrossBorder** | Regulatory Risk | Mid-tier cross-border currency corridor transfers falling between ₹40,000 and ₹49,999 |

### 📊 Severity Tier Matrix Mapping
* `Score = 0` $\rightarrow$ **CLEAR**
* `Score = 1` $\rightarrow$ **LOW RISK**
* `Score = 2 to 3` $\rightarrow$ **MEDIUM RISK**
* `Score >= 4` $\rightarrow$ **HIGH RISK**

---

## 💻 Installation & Local Deployment

### Prerequisites
* A running instance of **n8n** (Cloud or local host container setup).
* Valid Google Workspace account with OAuth2 client authorization credentials active for both Sheets and Gmail APIs.

### Workflow Import Steps
1. Clone this repository to your local directory.
2. Open your centralized n8n workspace UI dashboard.
3. Select **Workflows** $\rightarrow$ **Import from File** and select the production `workflow.json` package bundle from your repository.
4. Open the **Get row(s) in sheet** node, select your credential configuration asset, and match your active target Google Sheet Spreadsheet URL identifier.
5. Save changes and toggle the workflow activation status indicator to **Active**.
