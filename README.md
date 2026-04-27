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
