# Solar Panels Belgium – LangGraph Tool-Calling Agent (AWS Bedrock + Claude)

A simple customer-support AI agent built with **LangGraph** and **LangChain** that:
- Collects a user's **monthly electricity cost**
- Optionally uses **Tavily Search** for quick external lookup (if needed)
- Calls a custom tool `compute_savings()` to estimate:
  - number of solar panels
  - installation cost
  - net savings over 10 years
- Uses **AWS Bedrock (Claude 3 Sonnet)** for tool-calling
- Includes **fallback error handling** for tool failures
- Persists conversation state using **LangGraph MemorySaver**

---

## What this project does

This agent behaves like a **Solar Panels Belgium** customer support assistant.

### Flow
1. User chats with the assistant.
2. Assistant extracts **monthly electricity cost** (asks clarifying questions if missing).
3. Assistant calls `compute_savings(monthly_cost)` tool.
4. Tool returns estimated solar setup + savings.
5. The conversation continues with memory (state persists in the graph).

---

## Tech Stack

- **LangChain Core**: prompts, tools, runnables
- **LangGraph**: state machine orchestration + memory
- **AWS Bedrock**: Claude model runtime
- **Tavily**: web search tool integration
- **boto3**: AWS client

---

## Requirements

- Python **3.10+** recommended
- AWS credentials configured locally (for Bedrock access)
- Bedrock access enabled for:  
  `anthropic.claude-3-sonnet-20240229-v1:0`
- Tavily API key (if you want Tavily search to work)

---

## Installation

### 1) Create & activate a virtual environment
```bash
python -m venv .venv
# Windows
.venv\Scripts\activate
# Mac/Linux
source .venv/bin/activate
