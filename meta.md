# AI Primer — Meta & Guidelines

## Review Panel

See [panel.md](panel.md) — content panel (what to teach, how to teach it) and fact-check panel (technical accuracy).

## Target Audience

People *using* AI systems, not people building them. Average white-collar workers — comfortable with office software, chatbots, search engines, and similar tools. No programming background assumed.

## Structure

### Nine Chapters + Closing Page

A dependency chain from simple LLM to autonomous multi-agent systems, with two additions: Multimodality (a branch extending the token concept from §1) and Context Engineering (a synthesis chapter tying everything together).

| # | Section | Role |
|---|---------|------|
| 1 | The Plain LLM | The atomic unit: tokens, statelessness, next-word prediction |
| 2 | Multimodality | Branch: non-text inputs are tokens too, with lossy compression |
| 3 | The Chatbot | Adds conversation via history resend |
| 4 | The System Prompt | Programs behavior with hidden instructions |
| 5 | Structured Output | Machine-readable responses |
| 6 | Tool Use | LLM can act via external tools |
| 7 | The Agentic Loop | Autonomous loops: plan, act, observe, repeat |
| 8 | Multi-Agent | Division of labor via orchestrator + subagents |
| 9 | Context Engineering | Synthesis: everything competes for the finite context window |
| — | What We Didn't Cover | Closing page: thinking models, RAG, trust, security, routing |

Chapters 1 and 3–8 form a strict dependency chain (each requires the previous). Chapter 2 is a branch off Chapter 1 (depends only on tokens). Chapter 9 is the capstone (depends on all preceding chapters).

**Cut from v1 (in `_drafts/`):** Thinking Models, RAG, Routing, Trusting the Output, Security & Risks, When to Use AI. Summarized in the closing page.

### Main Sections

Each numbered section should be **self-contained** and explain the most important concepts at a level accessible to the target audience. A reader should be able to understand the core idea without reading the "Under the Hood" subsections.

### Under the Hood (Diving Deeper)

Optional subsections that dive deeper into the technical details. More technical than the main text, but still accessible. These sections help readers who want to understand *why* things work the way they do, not just *what* they do.

- Marked as `### Under the Hood: [Topic]`
- Not required reading — the main section should stand on its own
- Good for: internal mechanics, embeddings, encoding details, architecture concepts
- Alternative name considered: "Diving Deeper"

In the final result, UTH sections may be collapsible/hidden, expanded only on interaction — keeping the main flow focused and uncluttered.

## Examples

- **Concrete over generic.** "Summarize these 12 restaurant reviews" beats "Summarize this document." Vivid scenarios the reader can picture.
- **Universal over niche.** If the reader needs even a moment to process what the example is about, pick a different one. No domain expertise required.
- **Transparent.** The reader looks *through* the example at the concept, not *at* the example. The example is a window, not a painting.
- **Double duty.** Each example earns its place twice: it illustrates the technical concept AND feels like a real task someone would do.
- **Varied domains.** No single domain forced across all sections. Each concept gets the example that serves it best — everyday work (emails, meetings, documents), everyday life (travel, cooking, shopping).
- **No footnotes.** If an example needs explaining, it's the wrong example.

## Tone & Style

- Conversational but precise
- Use analogies, but don't stretch them too far
- ASCII diagrams for key concepts
- Bold key terms on first introduction
- Keep it concrete — real examples over abstract explanations
- Disclaimer up front: this guide deliberately simplifies

## Key Principles

- **Tokens are the central user-facing concept** — cost, context limits, and prompt design all revolve around tokens
- **Embeddings are supporting** — mentioned once to complete the picture, not a major topic
- **Text is the native format** — multimodality expands input but text remains most reliable
- **Practical relevance over technical completeness** — what does the reader need to *do* with this knowledge?
- **Correct broken mental models** — each section earns its place by fixing a specific misconception the target audience holds. If the common intuition is already roughly correct, the section doesn't need deep treatment. The primer is most valuable where people *think* they understand something but their mental model is off. Evidence: Elon University/IDFC survey (Jan 2025, n=500 LLM users) found 49% think LLMs are smarter than they are, 40% say the LLM "understands" them; Nature Machine Intelligence found users systematically overestimate LLM accuracy; NN/g research confirms inaccurate mental models lead to underwhelming usage.

## Editorial Filter: Mental Model Gaps by Section

Each section should be evaluated against: (1) how wrong is the common intuition? (2) how well do existing resources correct it for our audience? Sections with high gaps on both axes are where the primer adds the most value.

| Section | Common (wrong) intuition | What's actually true | Gap size |
|---|---|---|---|
| Multimodality | "The AI sees my image" | Images are tokenized (expensively); text remains more reliable; the model processes token representations, not visual perception | HIGH |
| Context Engineering | "The AI remembers our conversation" | No memory — re-reads everything every call; context window ≠ usable memory; lost-in-the-middle problem | VERY HIGH |
| Thinking Models | "The AI is reasoning step by step" | CoT faithfulness as low as 25% (Anthropic); visible "thinking" may not reflect actual computation; longer ≠ better | HIGH |
| RAG | "Just upload all our documents and the AI will know them" | It searches then reads on each call; quality depends on retrieval, not just access | MODERATE |
| Trusting the Output | "If the AI says it confidently, it's right" | Confidence ≠ accuracy; fabricates sources when pressed; never says "I don't know"; confirms whatever bias you bring | VERY HIGH |
| Security | "I'm just chatting, what's the security risk?" | Prompt injection is unsolved; content the AI reads can hijack it; agent permissions amplify risk | HIGH |
| When to Use AI | "AI is great for everything" / "AI can't be trusted" | Sweet spot is fuzzy input → structured output; dangerous for unverifiable outputs; knowing when NOT to use it matters most | HIGH |
| Routing | "Use the best model for everything" | Different models for different tasks; 90% of tasks don't need the most powerful model | LOW |

**Implication for Routing:** The mental model gap is small — the concept is straightforward once stated. Consider folding into "When to Use AI" or treating as a short sidebar rather than a full section.

## Building the Website

`python3 build.py` generates a multi-page HTML site in `site/`. Open `site/index.html` in a browser. Requires `pandoc`.
