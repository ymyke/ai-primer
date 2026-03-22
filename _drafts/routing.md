<!-- Editorial: Mental model gap = LOW. Common wrong intuition: "Use the best model for everything." Reality: Different models for different tasks; 90% of tasks don't need the most powerful model. Consider folding into "When to Use AI" or treating as a short sidebar. -->

# 12. Routing — The Right Model for the Job

```
  User request
       │
       ▼
  ┌──────────┐
  │  Router  │
  └────┬─────┘
       │
       ├── Simple ("What time is it in Tokyo?")
       │         └──▶  Small model (fast, cheap)
       │
       ├── Medium ("Summarize this article")
       │         └──▶  Mid-tier model (balanced)
       │
       └── Complex ("Compare these two contracts clause by clause")
                 └──▶  Flagship model (slow, expensive, smart)
```

In practice, you don't send every request to the most powerful (and most expensive) model. **Routing** decides which model handles a request — based on complexity, cost, and latency.

**How routing works:**
- **Rule-based** — Keywords or categories determine the model
- **Classifier** — A small, fast model estimates complexity and routes accordingly
- **Cascading** — Try the cheap model first; if the answer is uncertain or poor, escalate to the bigger one

**Why it matters:** Flagship models can be 30x more expensive per token than small models, and most work is simple — 80% of requests don't need the top-tier model.

MN this section is a bit thin? could be that it just is. but let's list the things a user should know about this topic. is the section worthwhile to keep or shall we dump it? is one aspect that the user should decide consciously which model to take ("manual routing"?)

---
