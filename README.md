# explore-ai-engineering

👉 [Basics of LLMs](BasicsOfLLMs.md)

# 🧠 Key Terms Explained Simply

| Term                                         | Explanation                                                                                                                                                                                                    |
| -------------------------------------------- | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| **AI (Artificial Intelligence)**             | Making computers do things that typically require human intelligence — like understanding language, recognizing images, or playing games.                                                                      |
| **ML (Machine Learning)**                    | A type of AI where the computer learns from examples or data instead of being explicitly programmed.                                                                                                           |
| **Deep Learning**                            | A subfield of ML using layered neural networks to learn complex patterns — like how your brain processes signals in layers.                                                                                    |
| **LLM (Large Language Model)**               | A type of deep learning model trained on lots of text data to understand and generate human-like language.                                                                                                     |
| **GPT (Generative Pre-trained Transformer)** | A type of LLM that is trained to predict the next word (token) in a sentence and generate text.                                                                                                                |
| **Token**                                    | A small piece of text (like a word or part of a word). Models work by predicting tokens one at a time. For example, "ChatGPT" might be 1 token, "unbelievable" might be split into "un", "believ", and "able". |
| **Transformer**                              | The deep learning architecture used in LLMs. It processes all parts of a sentence at once, which helps with understanding context.                                                                             |
| **Neural Network**                           | A model inspired by how the brain works. It has layers of simple units (neurons) that pass signals to each other to make decisions.                                                                            |
| **Heuristics**                               | Simple rules or shortcuts the model may learn to solve problems faster — not always perfect, but useful for patterns.                                                                                          |
| **Parameter**                                | A number the model adjusts during training to learn patterns in the data. More parameters = more learning power.                                                                                               |
| **Function Calling**                         | A feature in newer LLMs where the model can call external tools or APIs (e.g., check weather, book ticket) by filling in structured requests.                                                                  |
| **RAG (Retrieval-Augmented Generation)**     | Combines search with generation. Instead of just guessing answers, the model retrieves relevant documents first and then answers using them.                                                                   |
| **Quantisation**                             | Compressing a model to make it smaller and faster by reducing precision (e.g., using 8-bit instead of 32-bit numbers).                                                                                         |
| **Sharding**                                 | Splitting a huge model into parts to run it on multiple machines or GPUs.                                                                                                                                      |
| **Customisation Techniques**                 | Ways to adapt LLMs to specific tasks or domains. Includes prompt engineering, fine-tuning, LoRA, and retrieval.                                                                                                |
| **Prompt Engineering**                       | Crafting clever input messages to guide the LLM’s output.                                                                                                                                                      |
| **Fine-Tuning**                              | Training the model again on your specific data to specialize it.                                                                                                                                               |
| **LoRA / Adapters**                          | Lightweight training techniques to customize a model without retraining everything.                                                                                                                            |

---

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
