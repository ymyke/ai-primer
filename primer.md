# AI Primer: The Evolution of AI Systems

> A non-technical guide to how AI systems actually work.
> From fundamentals to agents — step by step.

*This guide deliberately simplifies. Some details are omitted, some analogies are imperfect. The goal is a useful mental model, not a textbook.*

---

## [Part I: The Evolution](part1-the-evolution.md)

From a simple text box to autonomous agents — each step builds on the last.

1. The Plain LLM — The Foundation
2. The Chatbot — Statefulness as Illusion
3. The System Prompt — Programming Behavior
4. Structured Output — Machine Talks to Machine
5. Tool Use — Hands for the LLM
6. The Agentic Loop — Autonomous Action
7. Multi-Agent — Division of Labor

## [Part II: What the Model Sees](part2-what-the-model-sees.md)

What flows through the system — and how it's processed on each call.

8. RAG — Tapping External Knowledge
9. Multimodality — More Than Text
10. Thinking Models — The Inner Monologue
11. Context Engineering — The Real Discipline

## [Part III: In Practice](part3-in-practice.md)

What matters when you use AI systems for real.

12. Routing — The Right Model for the Job
13. Security & Risks

---

## Glossary

| Term                    | Explanation                                                          |
| ----------------------- | -------------------------------------------------------------------- |
| **Token**               | Word fragment, the basic unit for LLMs (~¾ of a word)                |
| **Context Window**      | Maximum text an LLM can process at once                              |
| **Temperature**         | Creativity dial (0 = deterministic, 1 = creative)                    |
| **Inference**           | A single call to the LLM                                             |
| **Embedding**           | Numeric vector representation of text (or images, audio)             |
| **RAG**                 | Retrieval Augmented Generation — external knowledge at runtime       |
| **Fine-Tuning**         | Retraining a model on custom data                                    |
| **Harness**             | All application code around the LLM (loop, tools, RAG, routing)      |
| **Context Engineering** | The discipline of optimally filling the context window on every call |
| **Few-Shot**            | Examples in the prompt to demonstrate desired behavior               |
| **Chain of Thought**    | Step-by-step reasoning, explicit or implicit                         |
| **MCP**                 | Model Context Protocol — open standard for connecting tools to LLMs  |
| **Guardrails**          | Safety mechanisms that prevent unwanted outputs                      |
| **Hallucination**       | False information invented by the model                              |

---

*v.3-en — March 2026*
