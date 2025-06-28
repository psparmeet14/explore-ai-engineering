# Large Language Models (LLMs) – Study Notes

## 1. What *is* a Large Language Model?

| Term                              | Concise Definition                                                                                                                                                                            |
| --------------------------------- | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| **Large Language Model (LLM)**    | A neural network trained on vast text corpora that *predicts the next token* in a sequence, enabling it to generate and understand natural language at scale.                                 |
| **Foundation Model**              | Any very-large neural model (text, image, code, multi-modal, etc.) that is pre-trained on broad data and later **adapted** to many downstream tasks. LLMs are a *subset* focused on language. |
| **Generative vs. Discriminative** | Generative models produce new data (e.g., text). Discriminative models classify or score existing data. Most state-of-the-art LLMs (GPT, Llama, Gemini) are *generative*.                     |

### Key Idea

> By learning to predict the next token billions of times, the model implicitly learns grammar, facts, reasoning heuristics, and stylistic patterns.

---

## 2. Key Terms Explained Simply

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

## 3. GPT in Context

| Acronym | Meaning                              | Notes                                                                                                                                |
| ------- | ------------------------------------ | ------------------------------------------------------------------------------------------------------------------------------------ |
| **GPT** | *Generative Pre-trained Transformer* | “Transformer” is the neural architecture; “Pre-trained” means first trained on general data; “Generative” highlights text synthesis. |

* **GPT-n** (n = 1, 2, 3, 4 …) is OpenAI’s LLM series.
* GPT-3 (2020) has **175 B parameters** and was trained on \~570 GB of cleaned text (≈300 B tokens).
* GPT models are *instances* of LLMs, not synonyms – e.g., Claude, PaLM, Llama, Mistral are other LLM families.

---

## 4. Scale: Data & Parameters

### 4.1 Data Volumes

* **Rough thumb-rule**: plain-text English averages \~4–5 characters per word plus a space ⇒ **1 GB ≈ 200 M tokens**.
* State-of-the-art LLMs are trained on **hundreds of billions to trillions of tokens** (hundreds of gigabytes **compressed**, several **terabytes** uncompressed).
* “1 petabyte of training data” is a common *sound-bite* but *not literal* for GPT-3/4. Reality: curated high-quality subsets are smaller but still massive.

### 4.2 Parameters, Explained Simply

> **Parameters are the knobs the model can tune during training.** Each parameter is a weight in the network. More parameters → higher capacity to model complex patterns, but also higher computational cost and risk of overfitting without enough data.

| Model (public)     | Parameters | Training Tokens |
| ------------------ | ---------: | --------------: |
| GPT-2 (2019)       |      1.5 B |            40 B |
| GPT-3 (2020)       |      175 B |           300 B |
| Llama 2-70B (2023) |       70 B |             2 T |

*Note: private GPT-4 parameters are undisclosed.*

---

## 5. Anatomy of an LLM Pipeline

1. **Data Collection & Curation**
   – Web crawl, books, code, papers, conversations → deduplication, filtering, tokenization.
2. **Architecture** — *Transformer* layers with self-attention + feed-forward networks; position embeddings track order.
3. **Pre-Training** — Self-supervised next-token prediction at massive scale (compute measured in *“GPU-years”*).
4. **Post-Training / Alignment**
   a. **Supervised Fine-Tuning (SFT)** on labelled task data.
   b. **Reinforcement Learning from Human Feedback (RLHF)** or **DPO** for helpfulness, honesty, safety.
   c. **Tool / function calling** or **RAG** (Retrieval-Augmented Generation) to inject fresh knowledge.
5. **Inference & Serving** — Quantization, sharding, GPU/CPU/ASIC deployment, caching.

---

## 6. Customisation Techniques

| Technique                    | When to Use                                 | Pros                            | Cons                                      |
| ---------------------------- | ------------------------------------------- | ------------------------------- | ----------------------------------------- |
| **Prompt Engineering**       | Fast iteration, zero-shot or few-shot tasks | No training cost                | Limited control, can be brittle           |
| **Adapters / LoRA / Q-LoRA** | Need domain adaptation with *small compute* | Cheap, merge-able               | Slight latency overhead                   |
| **Full Fine-Tuning**         | Ample proprietary data, large budget        | Best quality                    | Expensive, risk of forgetting base skills |
| **RAG**                      | Knowledge changes frequently                | Latest facts, small model edits | Extra infra (vector DB, retriever)        |

---

## 7. Business & Product Use-Cases

1. **Customer Support Automation** (chat & voice, 24×7, multilingual)
2. **Content Generation & Personalisation** (blogs, ad copy, video scripts)
3. **Software Engineering Co-pilots** (code completion, review, migration)
4. **Data Analytics & BI** (natural-language SQL, narrative insights)
5. **Knowledge Management** (semantic search, document Q\&A)
6. **Creative Tools** (game narrative, marketing design, storyboarding)

> **Tip:** Map a use-case to *effort × impact*. Start with a constrained domain + human-in-the-loop.

---

## 8. Limitations & Risks

* **Hallucinations** – model may fabricate facts with high confidence.
* **Bias & Fairness** – reflects training data prejudice.
* **Privacy & IP Leakage** – risk when exposing sensitive data.
* **Compute & Energy Cost** – training can emit thousands of tonnes of CO₂.
* **Security** – prompt injections, jailbreaks, data exfiltration.

Mitigations include *rigorous evals*, *guardrails*, *RAG*, *monitoring*, and *policy/legal review*.

---

## 9. Evaluation Metrics (Quick Glance)

| Type                  | Examples                                     |
| --------------------- | -------------------------------------------- |
| **Intrinsic**         | Perplexity, BERTScore, MAUVE                 |
| **Task-Specific**     | BLEU, ROUGE (summarisation), CodeEval        |
| **Human / Alignment** | Helpful-Harmless scores, adversarial testing |

---

## 10. Further Reading

* *Attention Is All You Need* – Vaswani et al., 2017 (Transformer paper)
* *Language Models are Few-Shot Learners* – Brown et al., 2020 (GPT-3)
* *Llama 2 Model Card* – Meta AI, 2023
* *Prompt Engineering Guide* – [https://github.com/dair-ai/Prompt-Engineering-Guide](https://github.com/dair-ai/Prompt-Engineering-Guide)

---

### Changelog

| Date       | Note                                                          |
| ---------- | ------------------------------------------------------------- |
| 2025-06-28 | Initial draft generated via ChatGPT + basic terminology added |
