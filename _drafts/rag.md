<!-- Editorial: Mental model gap = MODERATE. Common wrong intuition: "Just upload all our documents and the AI will know them." Reality: It searches then reads on each call; quality depends on retrieval, not just access. -->

# 10. RAG — Tapping External Knowledge

```
  "What's our remote work policy?"
                   │
        ┌──────────┴──────────┐
        ▼                     │
  ┌───────────────┐           │
  │  Knowledge    │           │
  │  Database     │           │
  │  (search)     │           │
  └───────┬───────┘           │
          │ relevant          │
          │ documents         │
          ▼                   ▼
  ┌───────────────────────────────┐
  │  Prompt: question + documents │
  └───────────────┬───────────────┘
                  ▼
           ┌─────────────┐
           │     LLM     │
           └─────────────┘
                  │
                  ▼
      Answer with source citation
```

**Retrieval Augmented Generation (RAG)** solves a core problem: LLMs only know what was in their training data. RAG fetches relevant documents at runtime and injects them into the prompt.

**How it works:** When a user asks a question, the system searches a knowledge database for relevant documents, adds them to the prompt as context, and lets the LLM answer based on that context. The "knowledge database" is typically a specialized database optimized for semantic search — it finds documents by meaning, not just keywords.

**Why it matters:** A large share of AI products — chatbots over company knowledge, document search, support tools — are RAG systems at their core. Quality depends heavily on how documents are organized and how well the search finds the right ones.

### Prompting vs. RAG vs. Fine-Tuning

Three ways to get a model to do what you want, ordered from simplest to most involved:

- **Prompting** (including system prompts and few-shot examples) — Cheapest, fastest to iterate. Good for steering behavior, tone, and format. Limited by context window size.
- **RAG** — Best when the model needs access to specific, changing, or proprietary knowledge (company handbooks, emails, meeting notes, internal reports). Doesn't change the model itself.
- **Fine-tuning** — Actually retrains the model on your data. Expensive, slow, and hard to iterate. Use it when you need the model to learn a fundamentally different *skill* or style that can't be achieved through prompting — not just to give it information (that's what RAG is for).

In practice, most use cases are solved with prompting + RAG. Fine-tuning is rarely necessary.

---
