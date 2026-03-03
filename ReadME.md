# 💰 FinanceManager-n8n — AI Powered Personal Finance Command Router

An AI-assisted automation workflow built using **n8n** that converts natural language financial commands into structured actions such as recording income, expenses, or savings.

This project demonstrates **AI + Automation + Clean Workflow Architecture** using webhook triggers, LLM parsing, command routing, and structured responses.

---

## 🚀 Problem It Solves

Tracking personal finances is often slow and manual. Users typically need to:

* Open apps
* Fill forms
* Categorize transactions manually

This workflow enables:

> **Natural language → Structured financial action**

Example:

```
"Salary 50000 for Jan"
```

Automatically becomes:

```json
{
  "type": "INCOME",
  "amount": 50000,
  "month": "Jan"
}
```

The system interprets intent using AI and routes it through an automation pipeline.

---

## 🧠 System Architecture

```
Webhook Trigger
      ↓
Input Validation
      ↓
AI Agent (LLM Parsing)
      ↓
Normalize Command
      ↓
Command Router
   ↙      ↓       ↘
Income  Expense   Failure
      ↓
Webhook Response
```

Design Principle:

* Clean routing logic
* Separation of parsing and execution
* Extensible automation system

---

## ⚡ Trigger

**Webhook (POST request)**

Endpoint after deployment:

```
POST /webhook/finance-manager
```

Example request:

```bash
curl -X POST http://localhost:5678/webhook/finance-manager \
-H "Content-Type: application/json" \
-d "Salary 50000 for Jan"
```

---

## 🧩 Nodes Used

| Node                 | Purpose                 |
| -------------------- | ----------------------- |
| Webhook              | Receives user command   |
| IF Node              | Validates input         |
| OpenAI Chat Model    | Parses natural language |
| Function (Normalize) | Standardizes output     |
| Router (IF Nodes)    | Routes command type     |
| Income Node          | Handles income events   |
| Expense Node         | Handles expense events  |
| Default Failure      | Error handling          |
| Respond to Webhook   | Returns API response    |

---

## 📥 Sample Input

```
"Bought groceries worth 1200"
```

---

## 📤 Sample Output

```json
{
  "status": "SUCCESS",
  "message": "Expense of 1200 recorded for groceries"
}
```

---

## 🖼 Screenshots

<img width="1917" height="867" alt="FinanceManager_on_n8n" src="https://github.com/user-attachments/assets/e1bf57d4-30f9-4ce2-a5c6-328ca46c980c" />


## 🛠 Setup Instructions

### 1. Install n8n

```bash
npm install -g n8n
n8n
```

Open:

```
http://localhost:5678
```

---

### 2. Import Workflow

* Download `finance-manager-n8n.json`
* Import into n8n editor

---

### 3. Configure OpenAI Credentials

Add your API key inside:

```
OpenAI Chat Model Node
```

---

### 4. Activate Workflow

Click **Activate** → Send POST request.

---

## 🧱 Tech Stack

* n8n Automation
* OpenAI API
* Webhooks
* JavaScript Function Nodes
* JSON Routing Logic

---

## 🔒 Security Notes

* API keys are not stored in repository
* Credentials managed via n8n credential manager
* Webhook endpoint intended for local/demo usage

---

## 📈 Future Improvements

* Persistent database storage
* Google Sheets integration
* Budget analytics dashboard
* Telegram / WhatsApp interface
* Scheduled financial summaries
* Multi-user authentication

---

## 👨‍💻 Author

Built as part of an AI automation learning and systems-engineering journey focused on scalable product development.

---

## ⭐ Why This Project Matters

This project demonstrates:

* AI integration into real workflows
* Automation system design
* Event-driven architecture
* Practical LLM application beyond chat interfaces

---

If you found this useful, consider starring ⭐ the repository.
