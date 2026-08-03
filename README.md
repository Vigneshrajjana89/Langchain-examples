# LangChain, LangGraph & LangSmith Examples

Welcome to the **LangChain Examples** repository! This repository contains practical guides, notebooks, and code examples for building LLM applications using the LangChain ecosystem.

---

## 🌟 The Core Ecosystem: Why Use LangChain, LangGraph, and LangSmith?

Modern AI applications require more than just passing text to an API. They require structured reasoning, complex decision-making, tool execution, multi-agent coordination, and deep observability. The LangChain ecosystem is built around three core pillars:

```
+-------------------------------------------------------------------+
|                           LANGSMITH                               |
|                (Observability, Tracing & Evaluation)              |
+-------------------------------------------------------------------+
                                  ^
                                  | Monitors & Debugs
+---------------------------------+---------------------------------+
|                                 |                                 |
|          LANGCHAIN              |            LANGGRAPH            |
|   (Building Blocks & Components)|   (Stateful Agent Workflows)    |
|                                 |                                 |
+---------------------------------+---------------------------------+
```

---

### 1. 🔗 LangChain — The Foundation (Building Blocks)

**Why is it used?**  
LangChain provides unified abstractions and reusable components for connecting LLMs to external data sources, APIs, and custom logic.

* **Unified API for LLMs**: Easily swap between OpenAI (`ChatOpenAI`), Groq (`ChatGroq`), Google Gemini (`ChatGoogleGenerativeAI`), Anthropic, and local models without changing your application code.
* **Prompt Management**: Template prompts with dynamic inputs and safety guardrails.
* **Output Parsers**: Enforce structured outputs (JSON, Pydantic objects, lists) directly from raw text model completions.
* **Tool & Utility Abstractions**: Wrap custom Python functions with the `@tool` decorator so models can execute code, fetch live weather, or search databases.
* **Standard Interface (`LCEL`)**: The LangChain Expression Language allows chaining models, prompts, and parsers using pipe `|` operators.

---

### 2. 📊 LangGraph — Complex & Stateful Agent Orchestration

**Why is it used?**  
While basic LLM chains are linear (Input -> Prompt -> LLM -> Output), real-world AI applications are **cyclical** (Input -> Think -> Tool Call -> Feedback -> Think -> Final Answer). **LangGraph** provides graph-based state management for complex agent workflows.

* **Cyclical Workflows & Loops**: Allows agents to retry, refine answers, or loop continuously until a task condition is met.
* **State Management**: Built on explicit state graphs where each node can read and update a shared state object.
* **Multi-Agent Coordination**: Build teams of specialized agents (e.g., Researcher Agent + Writer Agent + Critic Agent) working together.
* **Human-in-the-Loop**: Pause execution to await human approval or input before proceeding with critical tool calls (like sending emails or executing DB updates).
* **Fault Tolerance & Persistence**: Built-in checkpointing allows pausing, rewinding, and resuming agent executions seamlessly.

---

### 3. 🔍 LangSmith — Observability, Debugging & Evaluation

**Why is it used?**  
LLMs can be non-deterministic, slow, or expensive. **LangSmith** gives developers full visibility into every single step, token, and prompt call within an agent execution.

* **Step-by-Step Tracing**: Inspect exact inputs, system prompts, tool calls, raw model outputs, token usage, and latency for every invocation.
* **Root Cause Debugging**: Instantly diagnose why an agent failed, formatted a tool call incorrectly, or hallucinated.
* **Dataset Management & Evaluation**: Collect real user inputs, create evaluation test suites, and benchmark different model versions or prompt changes.
* **Cost & Latency Monitoring**: Track token counts and API spend across different environments (dev, staging, prod).

---

## 🛠️ Summary: How They Work Together

| Tool | Core Responsibility | Real-World Analog |
| :--- | :--- | :--- |
| **LangChain** | Standard components & model connectors | **The Engine & Parts** |
| **LangGraph** | Complex agent logic, state, & decision loops | **The Steering System & GPS** |
| **LangSmith** | Real-time debugging, tracing, & metrics | **The Dashboard & Diagnostics** |

---

## 🚀 Getting Started

### 1. Prerequisites & Installation
This project uses [`uv`](https://github.com/astral-sh/uv) for fast dependency management.

```powershell
# Clone the repository
git clone https://github.com/Vigneshrajjana89/Langchain-examples.git
cd Langchain-examples

# Sync environment
uv sync
```

### 2. Configure Environment Variables
Create a `.env` file in the project root:

```ini
# Google Gemini / GenAI API Key
GOOGLE_API_KEY=your_google_api_key

# OpenAI API Key
OPENAI_API_KEY=your_openai_api_key

# Groq API Key
GROQ_API_KEY=your_groq_api_key

# LangSmith Tracing (Optional)
LANGCHAIN_TRACING_V2=true
LANGCHAIN_API_KEY=your_langsmith_api_key
```

### 3. Run Notebook Examples
Navigate to the `notebooks/` directory and run the Jupyter notebooks:
* [1-langchainintro.ipynb](notebooks/1-langchainintro.ipynb): Introduction to LangChain agents and tool calling.
* [2-Streamingandbatch.ipynb](notebooks/2-Streamingandbatch.ipynb): Demonstration of `invoke`, `stream`, and `batch` execution modes.
