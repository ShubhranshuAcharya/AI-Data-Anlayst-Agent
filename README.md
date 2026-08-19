# AI Data Analyst Agent 🚀

> An autonomous data analytics workflow built with **n8n, Google Gemini, and Google Workspace APIs** that transforms Google Sheets data into actionable insights, audit-ready reports, and executive email summaries.

[![n8n](https://img.shields.io/badge/n8n-2.36.0+-EA4B71.svg)](https://n8n.io/)
[![Google Gemini](https://img.shields.io/badge/Google_Gemini-3.1_Flash--Lite-4285F4.svg)](https://deepmind.google/technologies/gemini/)
[![Google Workspace](https://img.shields.io/badge/Google_Workspace-Sheets%20%7C%20Docs%20%7C%20Drive%20%7C%20Gmail-34A853.svg)](https://workspace.google.com/)
[![License](https://img.shields.io/badge/License-MIT-yellow.svg)](LICENSE)

---

## 📌 Overview

The **AI Data Analyst Agent** automates the process of turning raw spreadsheet data into structured business insights.

Users provide a **Google Sheets URL or Sheet ID** through the n8n chat interface. The workflow validates the source, dynamically discovers the available sheet, retrieves the dataset, performs deterministic data cleaning and statistical analysis, generates an audit-ready Google Docs report, and sends an executive HTML summary through Gmail.

The workflow also provides a Gemini-powered conversational path for general questions and natural-language interactions.

## 🎥 Demo

<p align="center">
  <video src="./asset/Agent Workflow demo.mp4" controls width="100%">
  Your browser does not support the video tag.
  </video>
</p>

### What the demo covers

`Chat Input → Sheet Discovery → Data Ingestion → Statistical Analysis → Google Docs Report → Gmail Delivery`
  ▶️ <strong>Click the preview to watch the complete demo</strong>
</p>

The demo covers:

`Chat Input → Sheet Discovery → Data Ingestion → Statistical Analysis → Google Docs Report → Gmail Delivery`

---

### 📸 Workflow Preview

<p align="center">
  <img src="[./assets/workflow.png](https://drive.google.com/file/d/12P6wep0xLunVPgHm3T50qhai_10rotok/view?usp=sharing)" alt="AI Data Analyst Agent n8n Workflow" width="100%">
</p>

### 📊 Generated Analysis Report

<p align="center">
  <img src="./assets/analysis-report.png" alt="Generated Data Analysis Report" width="90%">
</p>

### 💬 Chat Interface

<p align="center">
  <img src="./assets/chat-interface.png" alt="AI Data Analyst Chat Interface" width="80%">
</p>

### Core Workflow

```text
User Input
    ↓
Intent Detection
    ↓
Sheet Validation & Discovery
    ↓
Data Ingestion
    ↓
Data Cleaning & Analysis
    ↓
┌───────────────┬────────────────┐
│               │                │
▼               ▼                ▼
Chat         Google Docs       Gmail
KPIs         Audit Report      HTML Report
```

---

## ✨ Key Features

* 💬 **Conversational Data Analysis** — Analyze Google Sheets through a natural-language chat interface.
* 🔍 **Dynamic Sheet Discovery** — Extracts Sheet IDs and discovers sheet tabs through Google Sheets REST API v4.
* 📊 **Deterministic Analytics** — Calculates revenue, record volume, mean, median, category distributions, and performance KPIs programmatically.
* 🧹 **Data Sanitization** — Handles missing values, duplicate records, and schema validation before analysis.
* 📝 **Automated Audit Reports** — Generates timestamped Google Docs containing structured analytical results.
* 📧 **Executive Email Reports** — Sends responsive HTML summaries containing key KPIs and direct report links.
* 🧠 **AI Conversation Memory** — Maintains conversational context using n8n Simple Memory.
* 🛡️ **Fault-Tolerant Execution** — Uses dedicated validation, fetch, and analysis error paths.
* 🔄 **Automated Multi-Channel Delivery** — Delivers results through chat, Google Docs, and Gmail.

---

## 🏗️ Architecture

```text
┌───────────────────────────────────────────────────────────────┐
│                    USER / CHAT INTERFACE                      │
└───────────────────────────────┬───────────────────────────────┘
                                │
                                ▼
                    ┌───────────────────────┐
                    │    ANALYZE INTENT?    │
                    └───────────┬───────────┘
                                │
                 ┌──────────────┴──────────────┐
                 │                             │
                 ▼                             ▼
        ┌─────────────────┐          ┌──────────────────┐
        │  SHEET REQUEST  │          │  GENERAL QUERY   │
        └────────┬────────┘          └────────┬─────────┘
                 │                            │
                 ▼                            ▼
        ┌─────────────────┐          ┌──────────────────┐
        │ EXTRACT SHEET ID│          │     AI AGENT     │
        └────────┬────────┘          │ Gemini + Memory  │
                 │                   └────────┬─────────┘
                 ▼                            │
        ┌─────────────────┐                   ▼
        │  SHEET VALIDATION│           ┌───────────────┐
        └────────┬────────┘            │ CHAT RESPONSE │
                 │                     └───────────────┘
                 ▼
        ┌─────────────────────┐
        │ GET SPREADSHEET INFO│
        └──────────┬──────────┘
                   │
                   ▼
        ┌─────────────────────┐
        │   FETCH SHEET DATA  │
        └──────────┬──────────┘
                   │
                   ▼
        ┌─────────────────────┐
        │     RUN ANALYSIS    │
        │ Cleaning + Metrics  │
        └──────────┬──────────┘
                   │
          ┌────────┴────────┐
          │                 │
          ▼                 ▼
 ┌─────────────────┐  ┌──────────────────┐
 │ PREPARE CHAT    │  │ CREATE ANALYSIS  │
 │ RESPONSE / KPIs │  │       DOC        │
 └─────────────────┘  └────────┬─────────┘
                               │
                               ▼
                      ┌──────────────────┐
                      │ WRITE DOC CONTENT│
                      └────────┬─────────┘
                               │
                               ▼
                      ┌──────────────────┐
                      │ SEND REPORT EMAIL│
                      └──────────────────┘
```

---

## 🛠️ Tech Stack

| Category                | Technologies                                                                  |
| ----------------------- | ----------------------------------------------------------------------------- |
| **Workflow Automation** | n8n, JavaScript, n8n Expressions                                              |
| **AI / LLM**            | Google Gemini 3.1 Flash-Lite, LangChain, Simple Memory                        |
| **Data & Analytics**    | JavaScript, Statistical Aggregation, Data Cleaning, Schema Validation         |
| **APIs & Integration**  | REST APIs, Google Sheets API v4, Google Drive API, Google Docs API, Gmail API |
| **Data Format**         | JSON, Structured API Payloads                                                 |
| **Reporting**           | Google Docs, HTML, CSS, Automated Email Reports                               |
| **Authentication**      | OAuth 2.0, API Key Authentication                                             |
| **Reliability**         | Error Routing, Retry Policies, Input Validation, Fault-Tolerant Execution     |

---

## 🔄 How It Works

### 1. Input & Intent Detection

The n8n chat trigger receives the user's message and determines whether the request is a general conversation or a spreadsheet analysis request.

### 2. Sheet Discovery

For spreadsheet requests, the workflow extracts the Google Sheet ID using pattern matching and retrieves spreadsheet metadata through the Google Sheets REST API.

Sheet tabs are discovered dynamically rather than being hardcoded.

```javascript
{{ $json.sheets[0].properties.title }}
```

### 3. Data Ingestion & Cleaning

The selected dataset is retrieved and validated before analysis.

The processing layer handles:

* Missing values
* Duplicate records
* Schema validation
* Data type validation
* Input consistency

### 4. Statistical Analysis

The workflow performs deterministic calculations including:

* Total revenue
* Record volume
* Average order value
* Median order value
* Category percentage distribution
* Top-performing categories
* Key performance metrics

Numerical calculations are performed programmatically instead of relying on the LLM, reducing the risk of mathematical hallucinations.

### 5. Automated Reporting

After analysis, the workflow creates a timestamped Google Docs report containing the analytical results.

### 6. Executive Notification

An HTML-formatted email is generated through Gmail containing:

* Key KPI cards
* Summary metrics
* Category distributions
* Direct link to the generated Google Docs report

---

## 🎯 Design Decisions

### Deterministic Analytics

The system separates numerical computation from LLM reasoning.

**Gemini handles:**

* Natural-language interaction
* Conversational responses
* General questions

**The analytics engine handles:**

* Data cleaning
* Aggregations
* Statistical calculations
* KPI generation

This hybrid approach improves reliability while retaining a natural conversational interface.

### Dynamic Schema Inspection

The workflow retrieves spreadsheet metadata dynamically through the API, eliminating the need to configure specific sheet-tab names manually.

### Fault-Tolerant Workflow

External API operations contain dedicated validation and error-handling paths for:

* Invalid Sheet IDs
* Missing permissions
* Data-fetch failures
* Analysis failures
* API errors

### Automated Retry Handling

External AI and API operations can use configurable retry policies to improve resilience against temporary failures.

---

## 📊 Example Output

```text
Total Revenue:          $1180.78
Average Order Value:    $47.23
Median Order Value:     $24.99
Records Analyzed:       25
Total Units Sold:       41
Top Category:           Dolls
Category Revenue Share: 17.8%
```

The results are delivered through:

```text
Chat
 └── Executive KPIs

Google Docs
 └── Structured Analysis Report

Gmail
 └── Executive HTML Summary
```

---

## ⚙️ Setup & Deployment

### Prerequisites

* n8n instance — self-hosted or cloud
* Google account with required Workspace API access
* Google Gemini API access

### 1. Import Workflow

Import the following workflow into your n8n instance:

```text
AI Data Analyst Agent.json
```

Navigate to:

```text
Workflows → Import from File
```

### 2. Configure Credentials

Configure the following credentials in n8n:

```text
Google Sheets OAuth2
Google Docs OAuth2
Google Drive OAuth2
Gmail OAuth2
Google Gemini API Key
```

### 3. Configure Workflow Nodes

Update the environment-specific configuration:

```text
Create Analysis Doc
└── Google Drive Folder ID

Send Report Email
└── Recipient Email Address
```

### 4. Activate & Run

Activate the workflow and open the n8n chat interface.

Example input:

```text
Analyze this Google Sheet:

https://docs.google.com/spreadsheets/d/YOUR_SHEET_ID/edit
```

The workflow automatically executes:

```text
Validate → Discover → Fetch → Clean → Analyze → Report → Notify
```

---

## 📁 Project Structure

```text
AI-Data-Analyst-Agent/
│
├── AI Data Analyst Agent.json
├── README.md
└── LICENSE
```

---

## 🔐 Security

Credentials are managed through n8n's credential management system.

> **Never commit API keys, OAuth tokens, passwords, or other sensitive credentials to the repository.**

---

## 🎥 Demo

> 📹 **Walkthrough & Execution:** Add your demo video or GIF here.

```text
Demo:
https://youtu.be/YOUR_VIDEO_ID
```

---

## 🚀 Future Improvements

* Natural-language querying across datasets
* Automated anomaly and outlier detection
* Advanced data visualizations
* Support for CSV and Excel uploads
* Scheduled recurring analysis
* Multi-sheet and multi-dataset analysis
* Looker Studio / Power BI integration
* Predictive analytics capabilities

---

## 👤 Author

**Shubhranshu Acharya**

Software Engineer | Full-Stack + AI | LLM Integrations | AI-Driven Product Development

📧 **Email:** [shubhranshuacharya23@gmail.com](mailto:shubhranshuacharya23@gmail.com)

---

## 📄 License

This project is licensed under the **MIT License**. See [LICENSE](LICENSE) for details.

---

⭐ **If you found this project useful, consider giving it a star.**
