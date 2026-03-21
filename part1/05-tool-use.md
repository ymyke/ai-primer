# 5. Tool Use — Hands for the LLM MN "Hands for the LLM"? Any ideas for better alternative?

```
  ┌──────────────────────────────────────────────────────┐
  │  System Prompt:                                      │ MN why not just "System:" here?
  │  "You are a helpful assistant."                      │
  │                                                      │
  │  Available tools:                                    │
  │    get_weather(city: string) → weather data          │
  │    web_search(query: string) → search results        │
  ├──────────────────────────────────────────────────────┤
  │  User: "What's the weather in Tokyo?"                │
  └─────────────────────────┬────────────────────────────┘
                         │
                         ▼
                  ┌─────────────┐
                  │     LLM     │
                  └─────────────┘
                         │
         Tool call: get_weather(city="Tokyo")
                         │
                         ▼
              ┌─────────────────┐
              │  Application    │──── actual API call
              │  executes tool  │
              └────────┬────────┘
                       │           MN arrowss from here no longer perfectly aligned with arrows up to here
                       ▼
    Result: { temp: "28°C", condition: "humid" }
                       │
                       ▼
                ┌─────────────┐
                │     LLM     │
                └─────────────┘
                       │
                       ▼
   "It's currently 28°C and humid in Tokyo."
```

```
Behind the scenes — what the LLM sees at each step: MN should this line be outside the code block?

Step 1:  [system: "You are a helpful assistant.",
          tools: [get_weather, web_search],      MN why not the same system promopt as above? why split into tools here?
          user: "What's the weather in Tokyo?"]
              → LLM responds with: tool_call: get_weather(city="Tokyo")

Step 2:  [system: "...", tools: [...],
          user: "What's the weather in Tokyo?",
          assistant: tool_call: get_weather(city="Tokyo"),
          tool: { temp: "28°C", condition: "humid" }]   MN why tool: and not result:? generally, whioch role are tool results under usually=?
              → LLM responds with: "It's currently 28°C and humid in Tokyo."
```

**The crucial insight:** (MN this nece?) The LLM doesn't execute tools itself. It only decides *which* tool to call with *which* parameters. The application around the LLM performs the actual call and feeds the result back.

And the tool definitions? (MN maybe just state things instead of the rehotrical q in this case?) They're just text in the context window — typically part of the system prompt. The model has learned to recognize this format and generate matching structured calls.

**Typical tools:** Web search, database queries, API calls, file operations, email access, CRM access, code execution.

One of these deserves a closer look. (MN Maybe better: "Code execution deserves a better look:"?) Most tools fetch information from the outside world (MN or manipulate information...?). Code execution is different — it lets the model *compute*, compensating for weaknesses built into how LLMs work.

**Why code execution changes everything:** (MN DOES it change ecerything? or is this blabla? What would be sth more interesring/specific to point out here re code execution? what is it that makes it stick out?) Remember the strawberry problem from section 1? The model can't count letters in "strawberry" because it never sees individual letters — only tokens. But give the model a code execution tool, and it writes `'strawberry'.count('r')` — correct, every time. You can often trigger this simply by asking the model to "use code." The model didn't get smarter. It got a calculator. The same applies to arithmetic, date calculations, sorting, and anything else where precise computation beats pattern matching. This is why the *same model* gives better answers in a product that has code execution than in one that doesn't.

MN maybe mention one  aspect here? code execution is an important tool for LLMs to naviagte on the probabilistic vs deterministic spectrum. if we specify a task as a prompt and let an llm executre that task 100 times, we get dozens of different outcomes. some with tiny variations and some with much laerger. if hwoevber the llm writes a little software tool taht automates the task, the 100 executions will be identical.


Tool integrations are increasingly standardized through protocols like **MCP (Model Context Protocol)**, which aim to make tools portable across different AI systems — define the tool once, use it with any model.
