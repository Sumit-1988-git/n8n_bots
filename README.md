# 📌 N8N Bots

This repository contains workflows and resources to build domain-specific chatbots powered by n8n, ngrok, OpenAI, Telegram, and Pinecone vector search. Each use case demonstrates how to upload documents, extract and embed knowledge, and query through Telegram.

## 🚀 Key Features

- 🤖 **Telegram chatbot for real-time Q&A**
- 📄 **Uses a structured Onboarding FAQ PDF**
- 🧠 **Answers are generated only from uploaded context (no hallucinations)**
- 🌐 **Supports vector search with Pinecone + OpenAI embeddings**
- 🛠️ **Built entirely in n8n (low-code/no-code automation)**

## 📁 Use Cases

### 1. 🎓 Syllabus Advisor Bot
- **File:** `Syllabus_Advisor.json`  (n8n workflow for Telegram-triggered bot)
- **Folder:** `Test_Docs`  (Contains PDFs to be uploaded for the Knowledge base)
- **Folder:** `Results`  (Snippets of the Bot response)

**Upload:** Subject-wise syllabus PDFs  
**Telegram Query Example:**  
“What is the total marks for Theory?”

---

### 2. 🛠 API Manual Helper
- **File:** `API_Helper.json`  (n8n workflow for Telegram-triggered bot)
- **Folder:** `Test_Docs`  (Contains PDFs to be uploaded for the Knowledge base)
- **Folder:** `Results`  (Snippets of the Bot response)

**Upload:** API manuals (PDFs)  
**Telegram Query Example:**  
“Tell me about GET /api/v1/project-tasks/{id}?”

---

### 3. 📝 Meeting Summary Bot
- **File:** `Meeting_Summary.json`  (n8n workflow for Telegram-triggered bot)
- **Folder:** `Test_Docs`  (Contains PDFs to be uploaded for the Knowledge base)
- **Folder:** `Results`  (Snippets of the Bot response)

**Upload:** Meeting transcripts  
**Telegram Query Example:**  
“What was the target set for budget?”

---

### 4. 👔 Resume Finder Bot
- **File:** `Resume_Finder.json`  (n8n workflow for Telegram-triggered bot)
- **Folder:** `Test_Docs`  (Contains PDFs to be uploaded for the Knowledge base)
- **Folder:** `Results`  (Snippets of the Bot response)

**Upload:** Resumes (Google Drive or Local)  
**Telegram Query Example:**  
“Is there a resume with Data Scientist experience?”

---

### 5. 📌 Jira Docs Bot
- **File:** `Jira_helper.json`  (n8n workflow for Telegram-triggered bot)
- **Folder:** `Test_Docs`  (Contains PDFs to be uploaded for the Knowledge base)
- **Folder:** `Results`  (Snippets of the Bot response)

**Upload:** PRDs or Jira tickets  
**Telegram Query Example:**  
“Total how many epics are present”

---

## 🧱 Tech Stack

- **n8n** – Workflow automation
- **ngrok** – For Webhook
- **Telegram Bot API** – User interface
- **OpenAI (GPT-4.1)** – Language understanding
- **Pinecone** – Semantic vector database
- **Google Drive** – Document hosting & triggering

## 🧠 How It Works

### 1️⃣ Vector Creation (Content Ingestion)
- Watches Google Drive for the onboarding PDF
- Splits content into chunks
- Generates OpenAI embeddings
- Stores chunks as vectors in Pinecone

### 2️⃣ Telegram Assistant Workflow
- Listens for new messages on Telegram
- Matches query against vector store (contextual search)
- Uses OpenAI to summarize matching answer
- Replies in chat or responds:  
  "Sorry! I can't find relevant information from the knowledge base."

## 🔐 Prerequisites

- Telegram Bot Token
- OpenAI API Key
- Pinecone API Key
- Google Drive OAuth2 credentials
- n8n self-hosted or cloud account
- ngrok

## 🛠️ Getting Started

1. Clone the repository:
    ```bash
    git clone https://github.com/<your-username>/n8n_bots.git
    ```

2. Import workflows (.json) into n8n instance.

3. Set up credentials for:
    - Telegram
    - OpenAI
    - Pinecone
    - Google Drive

4. Upload the PDF to the specified Drive folder.

5. Start chatting on Telegram!

## 📌 Note:

You can refer this link for n8n and ngrok integration
https://youtu.be/dMH6q_NkY9w?si=R3HHTO7cGvtgGJ6f

While setting environment variables for WEBHOOK follow the below steps
* On Linux and Mac, you can set environment variables directly WEBHOOK_URL=[Your static url from ngrok] n8n
* On Windows you have to set the variable like this in the CMD prompt:
```
  set WEBHOOK_URL=[Your new static URL from ngrok ]
  
  n8n start
```
