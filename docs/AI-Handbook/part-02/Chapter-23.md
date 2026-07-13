# Chapter 23 – AI Engineering: When to Prompt and When to Write Code

In the previous chapters, you've assembled a capable AI development environment.

Your assistant can now:

- follow project instructions,
- access your repository,
- retrieve documentation,
- execute Skills,
- coordinate work through Agents,
- interact with external systems using MCP.

At this point, many developers ask the same question:

> "How much should I solve with AI, and how much should I solve with ordinary software?"

This is one of the most important questions in modern AI engineering.

The answer is rarely "always AI" or "never AI."

Like every engineering decision, it depends on the problem you're trying to solve.

---

# The Wrong Mental Model

When developers first discover Agents, they often think:

> "I can replace my application with prompts."

Technically, you sometimes can.

Engineering-wise, you usually shouldn't.

Imagine writing an application where every calculation is delegated to an LLM.

Need to calculate VAT?

Ask the AI.

Need today's date?

Ask the AI.

Need to sort a list?

Ask the AI.

Need to parse JSON?

Ask the AI.

This would work.

It would also be slow, expensive and unreliable.

AI is not a replacement for deterministic software.

It complements it.

---

# A Software Engineering Analogy

Imagine you're building a web application.

Would you implement this?

```text
Controller

↓

ChatGPT

↓

"Please calculate 19% VAT."

↓

Return result
```

Of course not.

You'd simply write:

```csharp
decimal vat = amount * 0.19m;
```

The calculation is:

- deterministic,
- fast,
- testable,
- inexpensive,
- always correct.

AI adds no value here.

---

# Two Kinds of Problems

One of the biggest mindset shifts is recognising that software problems fall into two broad categories.

## Deterministic Problems

Given the same input, the correct output is always the same.

Examples include:

- parsing JSON,
- calculating taxes,
- sorting data,
- validating e-mail addresses,
- reading configuration,
- calling REST APIs,
- querying databases.

Traditional software excels at these tasks.

---

## Reasoning Problems

The correct answer depends on judgement, interpretation or creativity.

Examples include:

- reviewing code,
- summarising documentation,
- explaining architecture,
- proposing refactorings,
- comparing implementations,
- writing documentation,
- brainstorming solutions.

These are where AI shines.

---

# A Useful Rule of Thumb

Whenever you design an AI workflow, ask yourself:

> Could I write a deterministic algorithm for this?

If the answer is:

> Yes.

Write code.

If the answer is:

> Not easily.

AI may be a good fit.

This single question prevents many unnecessary AI solutions.

---

# Let Software Do Software Things

Earlier in the handbook, we introduced Skills.

Imagine you have a Skill called:

```
Generate Release Notes
```

Should the Skill:

- calculate version numbers?
- read Git tags?
- parse commit history?

Probably not.

Instead:

```text
Code

↓

Collect deterministic data

↓

AI

↓

Write release notes
```

Each component performs the task it is best suited for.

---

# A Real Example

Imagine your company stores work items in Azure DevOps.

You want an Agent to create a sprint summary.

One approach is:

```text
Agent

↓

Ask AI to search Azure DevOps

↓

Ask AI to understand JSON

↓

Ask AI to count work items

↓

Ask AI to calculate totals

↓

Generate report
```

A much better approach is:

```text
Code

↓

Azure DevOps API

↓

Collect data

↓

Summarise numbers

↓

AI writes narrative
```

Notice what changed.

The AI no longer performs deterministic work.

Instead, it focuses on what humans actually want to read.

---

# Skills Should Prefer Code Whenever Possible

This principle becomes increasingly important as your AI system grows.

Suppose your Skill repeatedly needs to:

- retrieve the current sprint,
- calculate team velocity,
- determine overdue work items.

Instead of asking the model to figure these things out every time:

Write a small helper.

For example:

```text
GetSprintStatistics()
```

Your Skill now receives structured information instead of having to rediscover it.

Benefits include:

- fewer tokens,
- lower costs,
- faster responses,
- fewer mistakes,
- easier debugging.

---

# The Cost of Ambiguity

Every time you ask an AI to reason about something that software already knows, you introduce unnecessary ambiguity.

Compare these approaches.

**Approach A**

> Read all work items and determine which sprint is active.

**Approach B**

```json
{
  "Sprint": "Sprint 42",
  "Completed": 51,
  "Remaining": 7
}
```

Which one gives the AI less room for misunderstanding?

The second.

One of the most effective ways to improve AI quality is reducing unnecessary ambiguity before the model ever sees the data.

---

# AI Is the Last Step, Not the First

Many successful AI systems follow a surprisingly simple architecture.

```
Raw Data

↓

Deterministic Code

↓

Structured Information

↓

Language Model

↓

Natural Language Output
```

Notice where the AI appears.

At the end.

Not at the beginning.

The model transforms information into something useful for humans.

It doesn't replace your business logic.

---

# Engineering Note

As software engineers, we already optimise systems by separating responsibilities.

We don't ask SQL Server to render HTML.

We don't ask the browser to execute database queries.

Likewise, we shouldn't ask a language model to perform tasks that deterministic software already solves perfectly.

A useful mental model is:

> **Use software to discover facts. Use AI to explain them.**

This simple principle scales remarkably well.

---

# Looking Ahead

So far, we've focused on building capable AI systems.

Now it's time to make them **reliable**.

What happens when:

- the AI hallucinates?
- a retrieved document is outdated?
- a tool fails?
- an Agent makes a poor decision?

Professional AI systems are designed with these situations in mind.

In the next chapter, you'll learn practical techniques for making AI workflows observable, testable and trustworthy.

---

# Search Vocabulary

### Deterministic

**Definition**

A process that always produces the same output for the same input.

**Compare to**

Traditional software is typically deterministic, whereas language models are probabilistic.

**Example**

Calculating VAT or parsing JSON.

---

### Probabilistic

**Definition**

A process that may produce different—but still valid—results for the same input.

**Example**

Generating documentation or suggesting alternative implementations.

---

### Business Logic

**Definition**

The deterministic rules that implement how an application behaves.

**Example**

Calculating discounts, validating orders or enforcing workflow rules.

---

### Structured Data

**Definition**

Information organised in a predictable format that software can process reliably.

**Example**

JSON returned from a REST API before being summarised by an AI assistant.

---

# 🎉 Level Up!

You've reached an important architectural milestone.

You now understand that successful AI systems are not built by replacing software with prompts.

Instead, they combine the strengths of both.

You've learned to:

- distinguish deterministic from reasoning tasks,
- decide when code is the better solution,
- reduce ambiguity before involving AI,
- and design workflows where software and AI complement each other.

Perhaps the most valuable lesson is this:

**Don't ask AI to rediscover facts that your software already knows.**

Let software compute the facts.

Let AI communicate them.

### Next Level

As your AI assistant becomes more capable, reliability becomes increasingly important.

In the next chapter, you'll learn how experienced teams evaluate, debug and continuously improve AI systems—using many of the same engineering practices you've applied to traditional software for years.