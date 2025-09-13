# 🧠 MCP Chatbot – Memory + Actions + Web Automation

[![Python](https://img.shields.io/badge/Python-3.10%2B-blue)](https://www.python.org/)
[![LangChain](https://img.shields.io/badge/LangChain-Integration-green)](https://www.langchain.com/)
[![Groq](https://img.shields.io/badge/LLM-Groq%20Llama3-orange)](https://groq.com/)
[![MCP](https://img.shields.io/badge/MCP-Enabled-purple)](https://github.com/modelcontextprotocol)
[![Status](https://img.shields.io/badge/Status-Active-brightgreen)]()

---

## 🚀 Overview

**MCP Chatbot** is an intelligent, interactive agent that:

✅ **Remembers conversations** (built-in memory!)
✅ **Connects to real tools** like browsers, DuckDuckGo, Airbnb
✅ **Takes actions** (navigate, click, search) and observes results
✅ **Uses Groq Llama-3 LLM** for fast reasoning & natural responses
✅ **Implements ReAct (Reason + Action) Loop** for realistic AI behavior

---

## 📸 Demo Run

```bash
You: Latest AI news

Assistant:
Thought: To get the latest AI news, I should search for it online.

Action: browser_navigate
Action Input: {"url": "https://www.cnet.com/search/?q=latest+ai+news"}

Observation: Search results page loaded.

Action: browser_click
Action Input: {"element": "Search results", "ref": "first-result"}

Observation: Opened first news article.

Final Answer: The latest AI news can be found on CNET. Clicked on the first result for you.
```

✅ **The agent thinks, acts, observes, and answers — just like a human researcher!**

---

## 🏗️ Project Structure

```
📂 MCP_Project
 ┣ 📜 browser_mcp.json      # MCP servers config (Playwright, Airbnb, DuckDuckGo)
 ┣ 📜 mcp_chat.py           # Main script with memory-enabled chat loop
 ┣ 📜 .env                  # Store API keys securely (Groq API Key here)
 ┗ 📜 requirements.txt      # Dependencies
```

---

## ⚙️ Installation & Setup

### 1️⃣ Clone Repo

```bash
git clone https://github.com/<your-username>/MCP_Project.git
cd mcpdemo
```

---

### 2️⃣ Create Virtual Environment & Install Dependencies

```bash
python -m venv venv
source venv/bin/activate  # For Mac/Linux
venv\Scripts\activate     # For Windows

pip install -r requirements.txt
```

---

### 3️⃣ Configure Environment Variables

Create a `.env` file in the project root and add:

```ini
GROQ_API_KEY=your_groq_api_key_here
```

---

### 4️⃣ Run MCP Chat

```bash
python app.py
```

---

## 🔧 MCP Configuration

Your `browser_mcp.json` should look like this:

```jsonc
{
  "mcpServers": {
    "playwright": {
      "command": "npx",
      "args": ["@playwright/mcp@latest"]
    },
    "airbnb": {
      "command": "npx",
      "args": ["-y", "@openbnb/mcp-server-airbnb"]
    },
    "duckduckgo-search": {
      "command": "npx",
      "args": ["-y", "duckduckgo-mcp-server"]
    }
  }
}
```

**🔹 Explanation:**

* **Playwright MCP** → Opens browser, navigates, clicks, takes screenshots
* **Airbnb MCP** → Searches for stays & retrieves listing details
* **DuckDuckGo MCP** → Performs fast web search

---

This process allows the bot to behave **autonomously**, instead of just doing simple Q\&A.

---

## 🛠️ Features You Can Test

| **Command**                                       | **What Happens**                         |
| ------------------------------------------------- | ---------------------------------------- |
| `Latest AI news`                                  | Opens browser, searches news, summarizes |
| `airbnb_search "Paris"`                           | Finds stays in Paris (via Airbnb MCP)    |
| `duckduckgo_web_search "AI Jobs 2025"`            | Fetches search results via DuckDuckGo    |
| `Remember that I like OpenAI` → `What do I like?` | Tests conversation memory                |

---

## 📌 Future Improvements

* 🖼️ Display browser screenshots directly in terminal
* 🏢 Integrate **Notion / Slack MCP** for workflow automation
* 🧠 Add **Vector DB memory** for long-term knowledge retention

---

