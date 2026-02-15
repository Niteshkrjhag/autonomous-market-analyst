# Sentinel — Autonomous Market Research Agent

Sentinel is a self-hosted, agentic research system designed to move beyond static automation and enable **stateful, memory-aware market analysis**.

It continuously monitors changes across competitors, remembers historical context, and reports **only meaningful strategic deltas** instead of raw noise.

---

## 🎥 Demo

> Click to watch the system in action 👇

https://github.com/user-attachments/assets/eea69795-9ca4-4982-ae74-620c829a0e33

---

## 🧠 What Problem Does Sentinel Solve?

Most automated research tools are **stateless**:
- They scrape entire pages repeatedly  
- They lack historical awareness  
- They overwhelm users with unchanged or irrelevant data  

Sentinel answers a more useful question:

> **“What has changed since the last time I checked?”**

---

## 🏗️ High-Level Architecture

Sentinel is built as a **Plan → Act → Observe** loop with explicit memory.

- **Orchestration:** n8n  
  Handles workflow control, scheduling, and state transitions.

- **Reasoning Layer:** Gemini Pro  
  Interprets raw data, filters noise, and identifies strategic signals.

- **Data Acquisition:** Tavily  
  Provides real-time web access beyond static knowledge cutoffs.

- **Memory Layer:** Pinecone (Vector Database + RAG)  
  Stores historical observations and enables semantic comparison across time.

---

## 🔄 Execution Flow

1. Triggered on a schedule  
2. Retrieves historical context from vector memory  
3. Gathers fresh web data  
4. Compares new findings against prior knowledge  
5. Notifies only when meaningful changes are detected  

### Workflow Logic
<div align="center">
  <img src="https://github.com/user-attachments/assets/4f3b3f76-9860-43a4-ac19-b1aa98ea2598" width="800">
</div>
<div align="center">
  <text>Fig: Autonomous Market Intelligence Agent</text>
</div>

1.  **Trigger:** Scheduled timer (e.g., Weekly at 9 AM).
2.  **Context Check:** Agent queries Pinecone: *"What did we know about [Competitor] last week?"*
3.  **Live Research:** Agent queries Tavily: *"What is [Competitor]'s pricing today?"*
4.  **Delta Analysis:** Gemini compares Old vs. New.
    * *No Change:* Log and sleep.
    * *Change Detected:* Generate briefing & update Vector DB.

### Before Running Agent Database Entries

<div align="center">
  <img src="https://github.com/user-attachments/assets/b14afd8f-c8f7-4d11-b70e-c96469817c58" width="800">
</div>
<div align="center">
  <text>Fig: Before Running Agent Database Entries</text>
</div>

### After Running Agent Database Entries

<div align="center">
  <img src="https://github.com/user-attachments/assets/5b62b89d-5cd5-4b14-8fa3-228105474b7e" width="800">
</div>
<div align="center">
  <text>Fig: After Running Agent Database Entries</text>
</div>

## Result is sent to Slack
<div align="center">
  <img src="https://github.com/user-attachments/assets/7b09a1de-479b-4d54-b639-c3cfa737505e" width="800">
</div>
<div align="center">
  <text>Fig: Slack UI after agent process the user input and sends to slack</text>
</div>

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


## 🚀 Future Enhancements

- Supervisory LLM for research quality validation  
- Structured JSON outputs for downstream systems  
- Improved rate-limiting and fault tolerance  
- Multi-agent collaboration patterns  

---

## 🧪 Status

This project is a **proof-of-concept** focused on system design and agentic patterns rather than production scale.

---

## 📌 Tech Stack

- n8n  
- Google Gemini Pro  
- Tavily Search API  
- Pinecone Vector Database  
- Docker  

---

## 📄 License

MIT License
