# 13. Trusting the Output — When Confidence ≠ Correctness

LLMs always sound confident. They never say "I'm not sure" or "I made that up." This creates a specific set of risks that aren't bugs — they're features of how language models work.

### Hallucinations

LLMs sometimes generate convincing-sounding false information. They invent facts, fabricate statistics, and cite papers that don't exist. This is particularly dangerous with numbers, dates, legal references, and source citations. MN the more you force an LLM to create sth ("i want a reference for every bit of information you generate"), the higher the likelihood for a hallu. mention sth like this? 

Mitigations: RAG with source citations, factual cross-checks (MN by who, the user?), lower temperature for factual tasks. But no mitigation is foolproof — always verify critical facts. MN more: have the model factcheck things, use several models for 2nd and 3rd opinions, have the model "triangulate" numbers from 3 different perspectives, have the model find several sources for the same fact, ...

### Source Pressure

Ask a model "what's your source for that?" and instead of admitting it has none, it will often generate a plausible-looking citation — a real-sounding author, journal, and title that simply doesn't exist. The pressure to produce a source creates the hallucination. MN separate point or include above?

### Opinions on Demand

You can get *any* opinion from an LLM. Ask "why is X a bad idea?" and you'll get compelling arguments against X. Ask "why is X brilliant?" and you'll get equally compelling arguments for X. The model isn't reasoning — it's pattern-matching to what you seem to want.

This makes it dangerously easy to use AI to validate decisions you've already made, and mistake its agreeable output for independent analysis.

### The Verification Rule

**If you can't verify the output, don't automate the task.** AI is most useful when the human can quickly check the result — reading a draft, spot-checking extracted data, reviewing a summary. The harder it is to verify, the more dangerous it is to delegate. MN is this valuable?

MN is there anything else to say in this section? list and discuss all the relevant things that could be said in this section.

---
