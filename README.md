# Autonomous Market Intelligence Agent 🤖📊

> An agentic workflow that autonomously researches, filters, and synthesizes market intelligence using Google Gemini, Tavily, and Vector Memory.

## 🚀 Overview
In a world drowning in data, static dashboards aren't enough. This project implements an **Agentic AI loop** that moves beyond simple automation. It acts as a 24/7 analyst that:
1.  **Plans** a research strategy based on a topic.
2.  **Searches** the live web for real-time data (Tavily).
3.  **Recalls** historical context from a Vector Database (Pinecone) to detect changes.
4.  **Synthesizes** a decision-ready executive briefing via Slack.

## 🏗 Architecture
This project is self-hosted using **n8n** on **Docker**.

* **Orchestration:** n8n (Workflow Automation)
* **Reasoning Engine:** Google Gemini Pro / Flash 2.0
* **Tool Use (Function Calling):** Tavily Search API
* **Long-Term Memory (RAG):** Pinecone Vector Database
* **Notification:** Slack Incoming Webhook

### Workflow Logic
![Workflow Diagram](link_to_your_screenshot_here.png)
*(Tip: Take a screenshot of your n8n canvas, upload it to the repo, and link it here)*

1.  **Trigger:** Scheduled timer (e.g., Weekly at 9 AM).
2.  **Context Check:** Agent queries Pinecone: *"What did we know about [Competitor] last week?"*
3.  **Live Research:** Agent queries Tavily: *"What is [Competitor]'s pricing today?"*
4.  **Delta Analysis:** Gemini compares Old vs. New.
    * *No Change:* Log and sleep.
    * *Change Detected:* Generate briefing & update Vector DB.

## 🛠️ How to Run
1.  **Clone the repo:**
    ```bash
    git clone [https://github.com/yourusername/autonomous-market-analyst.git](https://github.com/yourusername/autonomous-market-analyst.git)
    ```
2.  **Import Workflow:**
    * Open your n8n instance.
    * Go to `Workflows` -> `Import from File`.
    * Select `workflows/main_agent_workflow.json`.
3.  **Setup Credentials:**
    * Add your Google Gemini, Tavily, and Pinecone API keys in n8n Credentials.

## 🔮 Future Improvements
* Add multi-agent collaboration (one agent for pricing, one for sentiment).
* Implement a "Supervisor" node to approve reports before sending.

## 📜 License
MIT