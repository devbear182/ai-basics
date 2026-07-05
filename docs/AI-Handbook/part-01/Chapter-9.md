# Chapter 9 – Prompting: Programming with Natural Language

When most people hear the word **prompt**, they think of a question.

For example:

> "Explain dependency injection."

Or:

> "Write a C# method that sorts a list."

Those are indeed prompts.

However, after working with AI for a while, you'll discover something surprising:

> **The most effective prompts don't look like questions.**

Instead, they look remarkably similar to software specifications.

As a software developer, this is good news.

You're already used to describing requirements, defining constraints and specifying expected behaviour.

Prompting is less about "talking to AI" and more about **communicating requirements clearly.**

---

# What Is a Prompt?

A **prompt** is all the information you intentionally provide to the model in order to guide its behaviour.

That information may include:

- instructions
- goals
- constraints
- examples
- documents
- source code
- images
- previous decisions

Notice something important.

A prompt is much more than a single sentence.

In many professional AI systems, the user's visible question is actually one of the smallest parts of the complete prompt.

---

# Prompting Is Programming

Consider these two C# methods.

```csharp
DoWork();
```

and

```csharp
DoWork(
    customer,
    invoice,
    taxRules,
    currency,
    logger,
    cancellationToken);
```

Which one provides more information?

Obviously the second one.

Prompting follows exactly the same principle.

Compare these prompts.

---

## Version 1

> Explain dependency injection.

---

## Version 2

> You are mentoring a junior .NET developer.
>
> Explain dependency injection using examples from ASP.NET Core.
>
> Assume the reader understands interfaces but has never used a Dependency Injection container.
>
> Avoid discussing the internal implementation of Microsoft's DI framework.
>
> End with a small coding exercise.

The second prompt doesn't make the model "smarter."

It simply removes ambiguity.

---

# The Four Questions Every Good Prompt Answers

Over time you'll notice that effective prompts usually answer four questions.

## 1. What is the goal?

What should the AI accomplish?

Examples:

- explain
- summarize
- review
- generate
- compare
- refactor

---

## 2. Who is the audience?

Should the explanation target:

- beginners?
- architects?
- customers?
- management?

Changing the audience often changes the entire response.

---

## 3. What constraints exist?

Examples:

- maximum length
- programming language
- coding standards
- libraries
- security requirements

Constraints reduce uncertainty.

---

## 4. What should success look like?

This is perhaps the most overlooked part.

Instead of saying:

> Improve this code.

Try:

> Refactor this code to improve readability without changing behaviour.
> Use modern C# features where appropriate.
> Explain every significant change.

Now the AI knows what "better" means.

---

# Why Ambiguity Produces Bad Results

Imagine asking a colleague:

> "Build me an API."

They would probably respond with questions.

- REST?
- GraphQL?
- Authentication?
- Database?
- Cloud?
- Local?
- Which language?

AI models usually don't ask all of these questions.

Instead, they make assumptions.

Sometimes those assumptions happen to match your expectations.

Sometimes they don't.

Many disappointing AI responses are simply the result of unanswered questions.

---

# The Hidden Prompt

One surprising fact about modern AI applications is that **your prompt is rarely the only prompt**.

A typical request may look more like this.

```text
System Prompt
        │
Conversation History
        │
Application Context
        │
Your Prompt
        │
Uploaded Files
        │
Tool Results
        ▼
      AI Model
```

Your visible message may be only a few lines.

The actual prompt received by the model may span several pages.

This explains why different applications can produce different answers using the same underlying model.

---

# What Is a System Prompt?

Every AI conversation starts with instructions that are usually invisible to the user.

These instructions are called the **system prompt**.

Think of it as configuration rather than conversation.

A system prompt defines how the assistant should generally behave before it ever sees your first message.

For example, a system prompt might contain instructions such as:

- You are a helpful software engineering assistant.
- Prefer Markdown for formatted output.
- Explain concepts before giving code.
- Do not generate unsafe code.
- Be concise unless the user requests more detail.

Applications often generate these prompts automatically.

For example:

- ChatGPT uses system prompts to define the behaviour of the assistant.
- GitHub Copilot uses system prompts optimized for software development tasks.
- Open WebUI allows you to create assistants with your own custom system prompts.
- AI agents often generate system prompts dynamically depending on the task they are performing.

As an end user, you usually write only the **user prompt**.

The application combines your prompt with its own hidden instructions before sending everything to the model.

> **Developer Note**
>
> When building your own AI applications, you'll often spend more time designing good **system prompts** than writing individual user prompts. A well-designed system prompt can improve every interaction that follows.

---

# Prompting vs Context Engineering

By now we've encountered two closely related concepts.

**Prompting**

You intentionally describe the task.

**Context Engineering**

You decide which information should be available while solving that task.

These complement each other.

A beautifully written prompt cannot compensate for missing information.

Likewise, enormous amounts of context cannot compensate for vague instructions.

Professional AI systems optimize both.

---

# Prompt Patterns

Over time, developers have discovered several prompt patterns that consistently produce better results.

Many professional AI applications combine several of these patterns automatically.

---

## Role Prompting

Tell the model who it should act as.

Example:

> You are an experienced DevOps engineer.

This helps establish the perspective from which the response should be written.

---

## Task Prompting

Describe exactly what should be accomplished.

Example:

> Review this PowerShell script for potential security issues.

The more precise the task, the fewer assumptions the model must make.

---

## Constraint Prompting

Reduce ambiguity by defining boundaries.

Examples:

- Target .NET 10.
- Use xUnit.
- Avoid third-party libraries.
- Maximum 300 words.
- Assume Windows 11.

Constraints narrow the solution space and often produce more consistent results.

---

## Output Format Prompting

Tell the AI how the result should be structured.

For example:

- Markdown
- JSON
- Table
- Bullet list
- C# code
- Step-by-step guide

Never underestimate the value of specifying the output format.

It often saves more time than refining the task itself.

---

## Example-Based Prompting

Sometimes explaining the desired result is less effective than showing it.

This family of prompting techniques differs only in the number of examples provided.

### Zero-Shot Prompting

You simply ask the model to perform a task without providing any examples.

Example:

> Explain dependency injection for a junior .NET developer.

The model relies entirely on its existing knowledge.

---

### One-Shot Prompting

You provide a single example before asking the model to continue.

Example:

```text
Input:
Customer

Output:
Entity

Now classify:

Invoice
```

The single example demonstrates the expected pattern.

---

### Few-Shot Prompting

You provide several examples.

```text
Example 1

fix(auth): validate JWT expiration

Example 2

feat(api): add customer search endpoint

Example 3

docs(readme): explain installation

Now generate another commit message.
```

Rather than following written instructions, the model infers the pattern from the examples.

Few-shot prompting is particularly useful when formatting or consistency is important.

---

# Prompting Is an Iterative Process

One of the biggest mindset shifts is realizing that prompting resembles software development.

Your first version is rarely your final version.

Instead, you gradually improve it.

```text
Prompt v1

↓

Observe response

↓

Improve instructions

↓

Observe response

↓

Improve context

↓

Repeat
```

This iterative approach often produces dramatically better results than trying to write the "perfect prompt" immediately.

Think of prompts as source code.

You don't expect to write perfect code on the first attempt.

Prompting follows the same engineering mindset.

---

# Your Future AI Assistant

Remember your original goal for this handbook.

You want to build a local AI assistant that helps with software development.

Interestingly, you won't be writing every prompt yourself.

Eventually, applications such as:

- Continue
- Roo Code
- Cline
- GitHub Copilot

will automatically construct large parts of the prompt for you.

Their job is not only to call the model.

Their job is to prepare an excellent prompt by combining:

- system prompts
- project context
- source code
- tool outputs
- your request

Understanding prompt engineering therefore helps you evaluate AI tools as well.

When one tool consistently produces better answers than another, the difference may lie in the prompt it generates—not necessarily in the model itself.

---

# A Brief Historical Perspective

Around 2023–2024, **Prompt Engineering** became one of the best-known AI skills.

At that time, interacting with AI primarily meant learning how to ask better questions.

As AI systems became more capable, the focus gradually shifted.

Today, experienced AI developers increasingly talk about:

- Context Engineering
- Tool Integration
- Memory
- Agent Design
- Workflow Automation

Prompting remains an important skill, but it is now viewed as one component of a much larger system.

A well-written prompt is valuable.

A well-designed AI system is even more valuable.

---

# Looking Ahead

Earlier in this handbook, you learned about context windows and token limits.

These are not just theoretical concepts.

As developers, we need strategies to work within these constraints efficiently.

Questions such as these naturally arise:

- How do I avoid filling the context window with irrelevant information?
- How do I preserve important decisions over long conversations?
- How can an AI continue working after its context window is full?
- Why does GitHub Copilot often seem to "remember" my project?
- How can I build a local assistant that behaves similarly?

These questions belong to the discipline of **Context Engineering**.

In Part II, we'll learn practical techniques such as:

- maintaining rolling summaries
- externalizing memory into files
- retrieving only relevant information (RAG)
- structuring long-running AI workflows
- building assistants that combine temporary context with persistent knowledge

You'll discover that managing context effectively is often more important than choosing a larger model.

---

# Search Vocabulary

| Term | Meaning |
|------|---------|
| Prompt | Instructions intentionally provided to the model. |
| User Prompt | The prompt written by the user. |
| System Prompt | Hidden instructions supplied by the application before the user's prompt. |
| Prompt Engineering | Designing prompts to improve model behaviour. |
| Zero-Shot Prompting | Asking the model to perform a task without providing examples. |
| One-Shot Prompting | Providing one example before asking the model to continue. |
| Few-Shot Prompting | Providing several examples from which the model infers the desired pattern. |

As AI systems continue to evolve, you'll increasingly encounter another term:

> **Context Engineering**

Many practitioners now consider context engineering to be the broader discipline, with prompt engineering being one of its tools.

---

# Developer's Decision

As a software developer, don't think of prompting as **asking better questions**.

Think of it as **writing better specifications**.

Every prompt is an interface between you and the model.

The clearer that interface is, the fewer assumptions the model must make.

As your AI systems become more sophisticated, you'll notice a gradual shift in your work.

Instead of spending most of your time writing prompts, you'll spend more time designing systems that provide:

- the right context,
- the right tools,
- the right memory,
- and the right constraints.

That transition—from writing prompts to engineering AI systems—marks the point where AI becomes another discipline within software architecture.

In the next chapter, we'll leave theory behind and begin assembling our first practical AI workstation.

We'll answer questions such as:

- Why do I need Ollama?
- Why do I need Open WebUI?
- Could I use LM Studio instead?
- What is VS Code's role?
- Where do tools like Continue, Roo Code and Cline fit?
- Which components are optional, and which are essential?

For the first time, we'll start building an architecture that resembles the AI assistants used in professional software development.