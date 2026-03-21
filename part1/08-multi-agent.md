# 8. Multi-Agent — Division of Labor

```
  User: "Plan a birthday party for 30 people:
         find a venue, plan the menu, create invitations."
                     │
                     ▼
         ┌───────────────────────┐
         │   Orchestrator Agent  │
         │   (plans & delegates) │
         └───┬─────┬─────┬───────┘
             │     │     │
             ▼     ▼     ▼
         ┌─────┐┌─────┐┌──────┐
         │Venue││Menu ││Invi- │    ◄── Subagents
         │find ││plan ││tation│        (each with own loop,
         └──┬──┘└──┬──┘└──┬───┘         own context, own tools)
            │      │      │
            ▼      ▼      ▼
         ┌───────────────────────┐
         │   Orchestrator Agent  │
         │   (synthesizes)       │
         └───────────────────────┘
                     │
                     ▼
            Complete party plan
```

You've seen that every LLM call has a limited context window, and that irrelevant context can hurt quality. So what happens when a task has parts that don't need to see each other?

The system splits it. The orchestrator agent delegates each subtask to a **subagent** — a separate agent with its own context window, its own tools, and its own agentic loop. The menu planner never sees the venue research. Each subagent returns its result, and the orchestrator combines them into a final answer.

**What this means for you:**
- **Better results on complex tasks** — each subtask gets the model's full, focused attention instead of competing for space in one crowded context window.
- **Faster results** — independent subtasks can run simultaneously.
- **One caveat** — because subtasks run independently, the pieces may not reference each other. The venue section of your party plan won't mention the menu, unless the orchestrator explicitly connects them.

MN more cevates? e.g., the fact that the orch only sees what the subagent outputs? which can be too terse to identify broeader context or to identify wrong approahces a subagent might have pursued etc. (also pot pratical tip: instrtuct the orch to instruct the subagents to document everything in sep files for later review -- helpful? best practice?)

**The practical takeaway:** When you give an AI a complex task, structure it as clear, separable subtasks. "Find a venue, plan the menu, and create invitations" is easier for the system to delegate than "plan a party." MN this has always been good advice, also way before multiagents. is this nevertheless useful?
