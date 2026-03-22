<!-- Editorial: Mental model gap = HIGH. Common wrong intuition: "The AI is reasoning step by step." Reality: CoT faithfulness as low as 25% (Anthropic); visible "thinking" may not reflect actual computation; longer ≠ better. -->

# 9. Reasoning Models — The Inner Monologue

```
  Classic LLM:                       Reasoning Model:

  "Should I buy or rent?"            "Should I buy or rent?"
           │                                    │
           ▼                                    ▼
    ┌─────────────┐                      ┌─────────────┐
    │     LLM     │                      │     LLM     │
    └─────────────┘                      │  ┌────────────────────┐
           │                             │  │ Thinking (hidden)  │
           ▼                             │  │ "Rent is $1,800/mo │
    Direct answer                        │  │  Buying: $2,700/mo │
                                         │  │  But equity..."    │
                                         │  └────────────────────┘
                                         └─────────────┘
                                                │
                                                ▼
                                         Answer (visible)
```

Classic LLMs generate the answer directly. **Reasoning models** (also called thinking models) have a reasoning step *before* the actual answer.

The idea started as a simple prompt trick (2022): write "Think step by step" and the model outputs its reasoning as normal text. Same model, just a cleverer prompt.

The current generation is fundamentally different: these models are trained through reinforcement learning to reason *before* answering. The reasoning happens in a separate block that is typically hidden from the user. This isn't a prompt trick — the ability to reason step by step is built into the model itself.

**When reasoning helps:** Complex logic, math, multi-step analysis, code debugging. For simple questions, it's overkill — slower and more expensive, because the hidden reasoning tokens still count toward cost and latency.

---
