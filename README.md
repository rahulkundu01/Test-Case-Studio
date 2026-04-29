# § TestCase Studio — ISTQB QA Intelligence Platform

A browser-based AI tool that converts BRS, FRS, and test plan documents into complete ISTQB-standard test cases, with integrated bug reporting and export.

---

## 🚀 Quick Start

1. Open `index.html` in Chrome or Edge
2. Enter your **Anthropic API key** (`sk-ant-...`) in the top bar
3. Upload your documents or paste content
4. Click **✦ Generate Test Cases**

> Get your API key: https://console.anthropic.com

---

## ✨ Features

### 📂 Document Input (All Formats)
| Format | Support |
|--------|---------|
| PDF    | ✅ (filename-based context) |
| Word (.docx / .doc) | ✅ Full text extraction |
| Excel (.xlsx / .xls) | ✅ All sheets extracted |
| Plain Text (.txt) | ✅ |
| CSV    | ✅ |
| Paste  | ✅ Direct text input |

### 📋 ISTQB-Standard Test Case Fields
Every generated test case includes:
- **TC ID** — Auto-numbered (TC-001, TC-002...)
- **Title** — Descriptive test scenario name
- **Module / Feature** — From document analysis
- **Objective** — What the test verifies
- **Type** — Functional / Integration / Regression / UAT / Smoke
- **Priority** — Critical / High / Medium / Low
- **Prerequisites** — Preconditions before test execution
- **Test Data** — Sample data for execution
- **Test Steps** — Step-by-step actions with per-step expected results
- **Expected Result** — Overall test pass condition
- **Actual Result** — Updated during execution
- **Status** — Not Run / Pass / Fail / Blocked / Deferred
- **Remarks** — Notes

### 🐛 Bug Report (ISTQB Defect Template)
Pre-filled when you click "Report Bug" on any failed test:
- Bug ID (auto-generated BUG-001, BUG-002...)
- Title, Severity, Priority, Status
- Module, Environment, Build/Version
- Assignee, Reporter, Date
- Description, Steps to Reproduce
- Expected vs Actual Result
- Impact / Risk assessment
- Attachments/Evidence references

### 📊 Export Options
- **Excel (.xlsx)** — Two sheets: Test Cases + Bug Reports
- **CSV** — All test cases in flat format
- **Bug PDF** — Print-ready individual bug report (browser print dialog)

### 🔍 Views
- **Overview** — Document analysis summary + stats cards
- **Test Cases (Table)** — Filterable, searchable table with status dropdowns
- **Detail View** — Card-by-card ISTQB format with numbered steps
- **Bug Reports** — All filed bugs with severity color coding

---

## ⚙️ Configuration Options
- Project name, Module, Version, Author
- Test type focus (Functional / Integration / Regression / UAT / Smoke)
- Priority filter (All / Critical only / High+ / Medium+)
- Toggle: Edge cases, Negative tests, Test data, API cases, Prerequisites

---

## 🔑 Privacy
API key stored only in browser `localStorage`. All processing is directly between your browser and the Anthropic API.


# 🤖 Using TestCase Studio Pro WITHOUT an API Key
You have 3 free options to use this tool without any API key or subscription.

### Option 1 — Claude.ai (Free tier available)
Best for: Most accurate ISTQB/Jira output

Open the tool → Toggle AI Source to "Manual (No API)"
Upload your documents / paste content in the sidebar
Click "📋 Generate Prompt (No API)"
Click "⎘ Copy Prompt"
Go to → https://claude.ai (free account)
Paste the prompt → hit Enter
Copy the JSON response Claude gives you
Back in the tool → paste into the "Import JSON" box → click Import

✅ Done! Your test cases appear instantly.

### Option 2 — ChatGPT (Free tier available)
Best for: Familiar interface
Same steps as above, but go to → https://chat.openai.com

Tip: Use GPT-4o for best results. If the output is truncated, ask:
"Continue the JSON from where you stopped"


### Option 3 — Google Gemini (Free)
Best for: Google Workspace users
Same steps, go to → https://gemini.google.com

## Option 4 — Run Ollama Locally (100% Offline, Free)
Best for: Teams with data privacy requirements
Setup (one-time, ~5 minutes)
bash# 1. Install Ollama
### Windows: https://ollama.com/download/windows
### Mac:     https://ollama.com/download/mac

### 2. Pull a model (choose one)
ollama pull llama3.1          # 8B — fast, decent quality
ollama pull mistral           # 7B — great for structured output
ollama pull qwen2.5:14b       # 14B — best quality for test cases

### 3. Start Ollama server
ollama serve
### This runs a local API at http://localhost:11434
Use with the tool

Open index.html
Toggle AI Source to "Claude API"
In the API key field type: ollama
The tool will send requests to http://localhost:11434


Note: Ollama mode uses a slightly simplified JSON request.
Quality depends on the model. llama3.1 or qwen2.5 recommended.


### Expected JSON Format
When pasting AI output, it must match this structure:
```json{
  "analysis": "Brief summary of what was analyzed",
  "project": "Project Name",
  "module": "Module Name",
  "testCases": [
    {
      "id": "TC-001",
      "key": "PROJ-TC-001",
      "summary": "Verify login with valid credentials",
      "feature": "Authentication",
      "epic": "Login Module",
      "type": "Functional",
      "priority": "Critical",
      "assignee": "QA Engineer",
      "fixVersion": "v1.0",
      "labels": ["smoke", "regression"],
      "objective": "Ensure valid users can log in successfully",
      "preconditions": "User account exists in the system",
      "testData": "Username: testuser@example.com, Password: Test@123",
      "steps": [
        {"step": 1, "action": "Navigate to login page", "expected": "Login page displays"},
        {"step": 2, "action": "Enter valid credentials", "expected": "Fields accept input"},
        {"step": 3, "action": "Click Login", "expected": "User redirected to dashboard"}
      ],
      "expectedResult": "User successfully logs in and sees the dashboard",
      "status": "To Do",
      "actualResult": "",
      "remarks": ""
    }
  ]
} ```

## Tips for Better Results

Be specific in your document — the more detail in your BRS/FRS, the better the test cases
Paste the full prompt — don't edit it before sending to the AI
If JSON is incomplete — ask the AI: "Please complete the JSON, you were cut off"
For large documents — split into sections and generate test cases per module
