<!-- Editorial: Mental model gap = VERY HIGH. Common wrong intuition: "If the AI says it confidently, it's right." Reality: Confidence ≠ accuracy; fabricates sources when pressed; never says "I don't know"; confirms whatever bias you bring. -->

# 13. Trusting the Output — When Confidence ≠ Correctness

LLMs always sound confident. They never say "I'm not sure" or "I made that up." This creates a specific set of risks that aren't bugs — they're features of how language models work.

### Hallucinations

LLMs sometimes generate convincing-sounding false information. They invent facts, fabricate statistics, and cite papers that don't exist. This is particularly dangerous with numbers, dates, legal references, and source citations.

A counterintuitive trap: the more you *demand* specific outputs — "provide a reference for every claim," "give me exact statistics" — the higher the chance of hallucination. The model will produce what you ask for, whether or not it exists.

### Source Pressure

Ask a model "what's your source for that?" and instead of admitting it has none, it will often generate a plausible-looking citation — a real-sounding author, journal, and title that simply doesn't exist. The pressure to produce a source creates the hallucination.

### Mitigations

No mitigation is foolproof — always verify critical facts. But strategies that help:

- **RAG with source citations** — Let the model reference specific, retrievable documents instead of its training data
- **Cross-checking** — Ask the model to verify its own claims from a different angle, use a second model for an independent check, or have it find multiple sources for the same fact
- **Lower temperature** for factual tasks — reduces creative variation
- **Explicitly permitting uncertainty** — Tell the model in the system prompt that it's okay to say "I don't know"

<!-- Potential additional mitigations to consider:
- Have the model factcheck its own output
- Use several models for 2nd and 3rd opinions
- Have the model "triangulate" numbers from 3 different perspectives
- Have the model find several sources for the same fact
-->

### Opinions on Demand

You can get *any* opinion from an LLM. Ask "why is X a bad idea?" and you'll get compelling arguments against X. Ask "why is X brilliant?" and you'll get equally compelling arguments for X. The model isn't reasoning — it's pattern-matching to what you seem to want.

This makes it dangerously easy to use AI to validate decisions you've already made, and mistake its agreeable output for independent analysis.

### Automation Bias

The more you use AI, the more you tend to trust it uncritically. Outputs that you would have questioned on day one start getting accepted without review by day thirty. This is a well-documented cognitive bias — not specific to AI, but amplified by it because the output sounds so confident and fluent.

### The Verification Rule

**If you can't verify the output, don't automate the task.** AI is most useful when the human can quickly check the result — reading a draft, spot-checking extracted data, reviewing a summary. The harder it is to verify, the more dangerous it is to delegate.

---
