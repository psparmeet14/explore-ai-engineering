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

## 2. GPT in Context

| Acronym | Meaning                              | Notes                                                                                                                                |
| ------- | ------------------------------------ | ------------------------------------------------------------------------------------------------------------------------------------ |
| **GPT** | *Generative Pre-trained Transformer* | “Transformer” is the neural architecture; “Pre-trained” means first trained on general data; “Generative” highlights text synthesis. |

* **GPT-n** (n = 1, 2, 3, 4 …) is OpenAI’s LLM series.
* GPT-3 (2020) has **175 B parameters** and was trained on \~570 GB of cleaned text (≈300 B tokens).
* GPT models are *instances* of LLMs, not synonyms – e.g., Claude, PaLM, Llama, Mistral are other LLM families.

---

## 3. Scale: Data & Parameters

### 3.1 Data Volumes

* **Rough thumb-rule**: plain-text English averages \~4–5 characters per word plus a space ⇒ **1 GB ≈ 200 M tokens**.
* State-of-the-art LLMs are trained on **hundreds of billions to trillions of tokens** (hundreds of gigabytes **compressed**, several **terabytes** uncompressed).
* “1 petabyte of training data” is a common *sound-bite* but *not literal* for GPT-3/4. Reality: curated high-quality subsets are smaller but still massive.

### 3.2 Parameters, Explained Simply

> **Parameters are the knobs the model can tune during training.** Each parameter is a weight in the network. More parameters → higher capacity to model complex patterns, but also higher computational cost and risk of overfitting without enough data.

| Model (public)     | Parameters | Training Tokens |
| ------------------ | ---------: | --------------: |
| GPT-2 (2019)       |      1.5 B |            40 B |
| GPT-3 (2020)       |      175 B |           300 B |
| Llama 2-70B (2023) |       70 B |             2 T |

*Note: private GPT-4 parameters are undisclosed.*

---

## 4. Anatomy of an LLM Pipeline

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

## 5. Customisation Techniques

| Technique                    | When to Use                                 | Pros                            | Cons                                      |
| ---------------------------- | ------------------------------------------- | ------------------------------- | ----------------------------------------- |
| **Prompt Engineering**       | Fast iteration, zero-shot or few-shot tasks | No training cost                | Limited control, can be brittle           |
| **Adapters / LoRA / Q-LoRA** | Need domain adaptation with *small compute* | Cheap, merge-able               | Slight latency overhead                   |
| **Full Fine-Tuning**         | Ample proprietary data, large budget        | Best quality                    | Expensive, risk of forgetting base skills |
| **RAG**                      | Knowledge changes frequently                | Latest facts, small model edits | Extra infra (vector DB, retriever)        |

---

## 6. Business & Product Use-Cases

1. **Customer Support Automation** (chat & voice, 24×7, multilingual)
2. **Content Generation & Personalisation** (blogs, ad copy, video scripts)
3. **Software Engineering Co-pilots** (code completion, review, migration)
4. **Data Analytics & BI** (natural-language SQL, narrative insights)
5. **Knowledge Management** (semantic search, document Q\&A)
6. **Creative Tools** (game narrative, marketing design, storyboarding)

> **Tip:** Map a use-case to *effort × impact*. Start with a constrained domain + human-in-the-loop.

---

## 7. Limitations & Risks

* **Hallucinations** – model may fabricate facts with high confidence.
* **Bias & Fairness** – reflects training data prejudice.
* **Privacy & IP Leakage** – risk when exposing sensitive data.
* **Compute & Energy Cost** – training can emit thousands of tonnes of CO₂.
* **Security** – prompt injections, jailbreaks, data exfiltration.

Mitigations include *rigorous evals*, *guardrails*, *RAG*, *monitoring*, and *policy/legal review*.

---

## 8. Evaluation Metrics (Quick Glance)

| Type                  | Examples                                     |
| --------------------- | -------------------------------------------- |
| **Intrinsic**         | Perplexity, BERTScore, MAUVE                 |
| **Task-Specific**     | BLEU, ROUGE (summarisation), CodeEval        |
| **Human / Alignment** | Helpful-Harmless scores, adversarial testing |

---

## 9. Further Reading

* *Attention Is All You Need* – Vaswani et al., 2017 (Transformer paper)
* *Language Models are Few-Shot Learners* – Brown et al., 2020 (GPT-3)
* *Llama 2 Model Card* – Meta AI, 2023
* *Prompt Engineering Guide* – [https://github.com/dair-ai/Prompt-Engineering-Guide](https://github.com/dair-ai/Prompt-Engineering-Guide)

---

### Changelog

| Date       | Note                                                          |
| ---------- | ------------------------------------------------------------- |
| 2025-06-28 | Initial draft generated via ChatGPT + basic terminology added |
