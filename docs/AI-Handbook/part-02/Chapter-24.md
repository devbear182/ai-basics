# Chapter 24 – Building Reliable AI Systems: Hallucinations, Evaluation and Observability

In the previous chapter, you learned an important engineering principle:

> Let software compute facts. Let AI communicate them.

Following this principle already makes AI systems more reliable.

But no matter how carefully you design your architecture, every AI system will eventually encounter situations where things don't go as expected.

For example:

- the model confidently invents information,
- a document retrieved through RAG is outdated,
- an external tool returns an error,
- an Agent chooses an inefficient approach,
- a prompt produces an unexpected answer.

Unlike traditional software, AI systems are probabilistic.

That doesn't mean they are unreliable.

It means they require a different engineering mindset.

---

# The Wrong Expectation

Many developers approach AI like traditional software.

They expect something like this:

```
Input

↓

Algorithm

↓

Correct Output
```

Language models don't work that way.

A better mental model is:

```
Input

↓

Reasoning

↓

Most Likely Output
```

Most of the time, that distinction doesn't matter.

Sometimes, it matters enormously.

The goal of AI engineering is not to eliminate uncertainty.

It is to **manage** it.

---

# A Software Engineering Analogy

Imagine you're building an online shop.

Would you trust a single HTTP request without checking:

- whether it succeeded,
- whether it timed out,
- whether the response was valid,
- whether retries are necessary?

Of course not.

You've probably written code like this hundreds of times.

```text
Call API

↓

Success?

↓

Retry?

↓

Log?

↓

Continue
```

AI systems deserve the same engineering discipline.

---

# Hallucinations

Perhaps the best-known AI failure is the **hallucination**.

A hallucination occurs when a model generates information that sounds plausible but is actually incorrect or unsupported.

For example:

> "This API was introduced in .NET 11."

The statement may sound perfectly reasonable.

The problem is that the API never existed.

Notice something important.

The model is not lying.

It is doing exactly what it was designed to do:

generate the most probable continuation based on its available context.

If the context is incomplete, the answer may still sound convincing.

---

# Reducing Hallucinations

There is no switch that disables hallucinations completely.

Instead, experienced AI engineers reduce the opportunities for them to occur.

Common techniques include:

- provide better context,
- retrieve documentation through RAG,
- ask more specific questions,
- let deterministic code collect facts first,
- ask the model to reference its sources,
- break large problems into smaller ones.

Notice how many of these techniques build directly on earlier chapters.

Reliable AI systems are usually the result of good architecture—not better prompts.

---

# Evaluation Is Different from Testing

As software developers, we're used to writing tests like this:

```csharp
Assert.Equal(42, result);
```

AI rarely fits into that pattern.

Suppose you ask:

> Explain this architecture.

There isn't just one correct answer.

There may be dozens of excellent answers.

Instead of asking:

> Is the output exactly correct?

AI evaluation often asks:

- Is it factually correct?
- Is it complete?
- Is it easy to understand?
- Did it follow the instructions?
- Would a developer find it useful?

The evaluation becomes more qualitative.

---

# Human Evaluation Still Matters

One misconception is that AI systems should evaluate themselves.

While automatic evaluation is improving, humans remain essential.

Especially when evaluating:

- writing quality,
- architectural advice,
- design decisions,
- code reviews,
- documentation.

Ultimately, your users decide whether an AI assistant is helpful.

Not a benchmark.

---

# Observe Before You Optimise

Earlier in the handbook, we discussed optimisation.

Experienced engineers know something important:

Never optimise what you haven't measured.

The same applies to AI.

Suppose someone reports:

> "The assistant has become unreliable."

Where do you start?

Without observability, you don't know.

Was the problem:

- a poor prompt?
- outdated documentation?
- missing instructions?
- an MCP server failure?
- an Agent choosing the wrong Skill?
- an older model version?

Without visibility into the workflow, debugging becomes guesswork.

---

# What Should You Observe?

A good AI application records information such as:

- the model used,
- important prompts,
- retrieved documents,
- tools that were called,
- execution time,
- token usage,
- errors,
- final response.

This information is often called a **trace**.

Instead of only seeing the final answer, you can inspect the entire reasoning workflow.

---

# A Practical Example

Imagine an Agent summarises your sprint.

The result is obviously wrong.

Without tracing:

```
Wrong Summary
```

That's all you know.

With tracing:

```
Question

↓

Retrieved Sprint 41

↓

Azure DevOps Tool Failed

↓

Fallback Documentation Used

↓

Summary Generated
```

Now the problem becomes obvious.

The AI wasn't the real issue.

The tool failed.

Observability turns mysterious AI behaviour into ordinary debugging.

---

# Don't Debug the Prompt First

A common beginner reaction is:

> "The prompt must be wrong."

Sometimes it is.

Often it isn't.

A much better debugging process is:

```
Did the tool succeed?

↓

Was the correct documentation retrieved?

↓

Were instructions loaded?

↓

Did the Skill execute correctly?

↓

Was the model appropriate?

↓

Only then inspect the prompt.
```

Notice how similar this is to debugging traditional software.

You investigate the system.

Not just one component.

---

# AI Systems Are Pipelines

One of the most important mindset shifts is recognising that modern AI systems are pipelines.

```
User

↓

Instructions

↓

Memory

↓

RAG

↓

Skills

↓

Tools

↓

Language Model

↓

Answer
```

Any stage can influence the final result.

This is why experienced AI engineers rarely ask:

> "Why did the model do this?"

Instead, they ask:

> "What information did the model receive?"

That question is usually much easier to answer.

---

# Engineering Note

Earlier in the handbook, we introduced the principle of separating responsibilities.

Reliability follows the same philosophy.

Instead of trying to make the language model perfect, we improve the surrounding system.

Good AI engineering often means making failure easier to detect, understand and recover from.

This should feel familiar.

The same philosophy has guided reliable software engineering for decades.

---

# Looking Ahead

By now, you've built an AI assistant that is:

- configurable,
- connected,
- extensible,
- observable,
- increasingly reliable.

The next challenge isn't technical.

It's architectural.

As your collection of instructions, Skills, tools and Agents grows, how do you organise them without creating another monolithic system?

In the next chapter, you'll learn practical design principles for creating AI workflows that remain understandable and maintainable as they evolve.

---

# Search Vocabulary

### Hallucination

**Definition**

A response generated by a language model that is plausible but factually incorrect or unsupported by the available context.

**Compare to**

Unlike an ordinary software bug, a hallucination results from probabilistic generation rather than faulty program logic.

**Example**

Inventing a non-existent API or attributing behaviour to a library that does not provide it.

---

### Evaluation

**Definition**

The process of assessing the quality, correctness and usefulness of AI-generated outputs.

**Example**

Reviewing whether a code explanation is technically correct, complete and easy to understand.

---

### Observability

**Definition**

The ability to understand how an AI system reached its result by inspecting its internal workflow.

**Compare to**

Similar to logging, tracing and monitoring in distributed software systems.

**Example**

Recording retrieved documents, tool calls and token usage to diagnose unexpected responses.

---

### Trace

**Definition**

A chronological record of the individual steps performed while processing an AI request.

**Example**

Showing which tools were called, which documents were retrieved and how long each step required.

---

# 🎉 Level Up!

You've now adopted one of the most important habits of professional AI engineers.

You've learned to:

- treat AI systems as observable pipelines,
- distinguish hallucinations from software bugs,
- evaluate outputs rather than expecting exact answers,
- and debug the entire workflow instead of blaming the prompt.

Perhaps the most valuable lesson is this:

**Reliable AI systems are rarely created by writing better prompts.**

They are created by designing better systems.

### Next Level

So far, we've focused on individual building blocks.

In the next chapter, we'll zoom out and look at the bigger picture.

You'll learn how to combine instructions, Skills, deterministic code, RAG, MCP and Agents into clean, modular AI workflows that remain easy to understand—even as your assistant grows from a weekend project into a real engineering tool.