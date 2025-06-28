# explore-ai-engineering

👉 [Basics of LLMs](BasicsOfLLMs.md)

# 🧠 What is MCP (Model Context Protocol)?

**Model Context Protocol (MCP)** is a bridge or communication protocol that allows **LLMs** (like ChatGPT) to interact with external systems in a **structured, programmable** way.

LLMs (Language Models) like ChatGPT can only generate text.

But if you want to use LLMs to get real work done—like **booking a cab**, **making a payment**, or **querying a database**—you need a backend that can act on their outputs.

**MCP is the standardized way to connect LLMs (clients) to those systems (servers via APIs).**

> Imagine the LLM is your brain, and MCP is like the hands and legs—so your brain can make things happen in the world.

---

## ⚙️ Key Components of MCP

| Role            | What it Does                                             |
|-----------------|----------------------------------------------------------|
| **Client (LLM)**   | Generates a structured request (e.g., JSON command)     |
| **MCP Server**     | Exposes APIs that perform real actions                  |
| **Applications**   | Use these APIs to do useful work (like RAG, SEO, etc.) |

---

## 📦 Use Cases of MCP

- **SEO**: Generate, test, and optimize web content.
- **RAG (Retrieval-Augmented Generation)**: Use LLM + real-time database for better answers.
- **Applications (e.g., Car Rental)**:  
  LLM suggests a car → MCP calls aggregator API → books the car.
