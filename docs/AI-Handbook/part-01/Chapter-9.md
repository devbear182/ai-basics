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
- formatting
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
System Instructions
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

# Prompting vs Context Engineering

By now we've encountered two related concepts.

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

Over time, developers have discovered several prompt patterns that work remarkably well.

We'll revisit these throughout the handbook.

---

## Role

Tell the model who it should act as.

Example:

> You are an experienced DevOps engineer.

This helps establish the perspective from which the response should be written.

---

## Task

Describe exactly what should be accomplished.

Example:

> Review this PowerShell script for security issues.

---

## Constraints

Limit the solution space.

Example:

- Target .NET 10
- Use xUnit
- Avoid third-party libraries
- Maximum 300 words

---

## Output Format

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

# Few-Shot Prompting

Sometimes examples are more effective than explanations.

Suppose you want commit messages in a specific style.

Instead of describing the format, simply provide two or three examples.

```text
Example 1

fix(auth): validate JWT expiration

Example 2

feat(api): add customer search endpoint

Now generate another commit message.
```

The model learns the pattern from the examples.

This technique is called **few-shot prompting** because only a few examples are needed.

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

Their job is to prepare an excellent prompt.

Understanding prompt engineering therefore helps you evaluate AI tools as well.

When one tool consistently produces better answers than another, the difference may lie in the prompt it generates—not necessarily in the model itself.

---

# Prompting Is Not the End Goal

Many online tutorials focus heavily on "prompt engineering."

That can give the impression that becoming good at AI means becoming good at writing prompts.

That was largely true in the early days of ChatGPT.

Today, the field is evolving.

Increasingly, AI applications generate prompts automatically.

Developers spend less time crafting individual prompts and more time designing systems that provide:

- good context
- useful tools
- structured workflows
- reliable memory

Prompting remains important—but it is gradually becoming one component within a much larger discipline.

---

# Search Vocabulary

| Term | Meaning |
|------|---------|
| Prompt | Instructions intentionally provided to the model. |
| Prompt Engineering | Designing prompts to improve model behaviour. |
| Few-Shot Prompting | Teaching by providing a small number of examples. |
| Zero-Shot Prompting | Asking the model without examples. |
| System Prompt | Hidden instructions supplied by the application. |

As AI systems continue to evolve, you'll increasingly encounter a newer term:

> **Context Engineering**

Many practitioners now consider context engineering to be a broader and more important discipline than prompt engineering alone.

---

# Developer's Decision

As a software developer, don't think of prompting as "asking better questions."

Think of it as **writing better specifications**.

Every prompt is an interface between you and the model.

The clearer that interface is, the fewer assumptions the model must make.

And just like good software architecture, the best prompts are usually:

- explicit
- structured
- testable
- repeatable
- easy to improve over time

In the next chapter, we'll leave the theoretical world behind and begin assembling our first practical AI workstation.

We'll answer questions such as:

- Why do I need Ollama?
- Why do I need Open WebUI?
- Could I use LM Studio instead?
- What is VS Code's role?
- Where do tools like Continue, Roo Code and Cline fit?
- Which components are optional, and which are essential?

For the first time, we'll start building an architecture that resembles the AI assistants used in professional software development.