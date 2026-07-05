# Chapter 6 – Context: Why AI Sometimes Feels Brilliant... and Sometimes Feels Stupid

Imagine you hire a new software developer.

On their first day you ask:

> "Please fix bug #471."

Most likely, they will look at you with a puzzled expression.

Not because they are a bad developer.

They simply don't know:

- what product you're building
- where the bug was reported
- which repository contains the code
- how your company organizes work
- what "bug #471" even refers to

Now imagine asking a different question.

> "Please investigate bug #471 in the Customer Portal. The issue was reported yesterday. The failing method is `InvoiceService.CalculateTotals()`. The customer expects VAT to be rounded according to ISO 4217. The failing unit test is `CalculateTotals_GermanVAT_ShouldRoundCorrectly()`."

Suddenly the same developer has a much better chance of succeeding.

Nothing about the developer changed.

Only the **context** changed.

Modern AI systems behave exactly the same way.

---

# What Is Context?

**Context** is all information available to the model while it generates its response.

Many people assume context means:

> "The prompt."

That is only part of the story.

In reality, context can include many different sources.

```text
Context
│
├── Your prompt
├── Previous conversation
├── Uploaded files
├── Images
├── Source code
├── Documentation
├── Tool results
├── System instructions
└── Application-specific information
```

Every additional piece of useful information helps the model produce a more relevant answer.

---

# Why Context Matters More Than Many People Think

Suppose you ask:

> "Why doesn't this work?"

To a human colleague, this question is almost impossible to answer.

The same is true for an AI.

Now compare it to:

> "Why does `InvoiceService.CalculateTotals()` throw a `NullReferenceException` after migrating from .NET 8 to .NET 10? The exception occurs only when `DiscountRules` is empty."

The second prompt contains far more context.

The AI doesn't suddenly become more intelligent.

It simply has more information to work with.

One of the most important lessons in practical AI is this:

> Better context usually produces better answers.

---

# The Context Window

You may have heard people talk about a model's **context window**.

A context window is the maximum amount of information a model can consider during a single request.

Imagine your desk.

A small desk can hold only a few sheets of paper.

A larger desk can hold:

- design documents
- source code
- meeting notes
- architecture diagrams
- requirements
- error messages

Having a larger desk doesn't automatically make you a better developer.

It simply allows you to keep more relevant information visible while solving a problem.

A context window works in much the same way.

---

# Context Is Temporary

Another common misconception is that AI permanently remembers everything you tell it.

In most cases, it does not.

The information inside the context window exists only while the conversation or request is active.

When the conversation ends, that temporary context is usually gone.

Think of a whiteboard in a meeting room.

At the beginning of the meeting it is empty.

During the discussion, you fill it with ideas.

When the meeting ends, someone wipes it clean.

The participants still remember what happened.

The whiteboard does not.

The context window is more like the whiteboard than the participants.

---

# Why ChatGPT Sometimes "Forgets"

Suppose you spend an hour discussing a software architecture.

Eventually you notice the AI forgetting details mentioned much earlier.

This is usually **not** because the model is broken.

Instead, newer information gradually replaces older information as the available context fills up.

Different models support different context window sizes.

Some can remember relatively short conversations.

Others can process hundreds of pages of text in a single request.

Regardless of size, however, every context window has a limit.

---

# Context Is More Than Conversation

One of the biggest surprises for new AI users is that many modern AI applications automatically gather context for you.

Consider GitHub Copilot.

When you ask:

> "Generate unit tests."

Copilot doesn't simply send those three words to the model.

Instead, it may also include information such as:

- the current source file
- nearby methods
- project references
- compiler diagnostics
- programming language
- cursor position
- selected text

Your actual prompt may be only three words.

The complete context may contain thousands of lines of additional information.

This is one reason Copilot often produces surprisingly relevant answers.

---

# Local AI Starts with Almost No Context

When you install your first local model, the situation is very different.

Initially, your assistant knows almost nothing about your computer.

It cannot automatically see:

- your repositories
- your documents
- your screenshots
- your browser
- your terminal

This is intentional.

By default, a locally running model is isolated from the rest of your system.

That isolation protects your privacy.

It also limits what the assistant can do.

Throughout Part II of this handbook we will gradually provide our assistant with carefully controlled access to additional sources of context.

---

# General Knowledge vs Current Knowledge

Large Language Models already possess an enormous amount of general knowledge acquired during training.

For example, a model may know:

- C#
- Git
- SQL
- REST APIs
- design patterns
- common algorithms

What it does **not** automatically know is:

- your company's coding standards
- yesterday's design meeting
- your private Git repository
- today's support tickets
- this morning's production outage

That information simply wasn't part of the training data.

It must be supplied as context.

This distinction explains many situations where developers mistakenly conclude that a model is "stupid."

In reality, it often lacks the information needed to answer correctly.

---

# Context Is Usually Better Than a Bigger Model

Imagine two developers.

Developer A has thirty years of programming experience.

Developer B has five years of experience but is sitting next to the system architect with complete project documentation.

Who is more likely to answer a project-specific question correctly?

The answer depends on the question.

General programming?

Probably Developer A.

Your company's internal billing rules?

Possibly Developer B.

The same principle applies to AI.

Providing a model with relevant project information often improves the answer more than switching to a much larger model.

This observation has had a profound influence on modern AI systems.

Rather than building infinitely larger models, many organizations invest heavily in delivering better context.

---

# Where Does Context Come From?

Modern AI applications gather context from many different places.

```text
User
 │
 ├── Prompt
 ├── Conversation
 ├── Files
 ├── Images
 ├── Documentation
 ├── Source Code
 ├── Search Results
 ├── Tool Output
 └── Business Data
          │
          ▼
      Context
          │
          ▼
      AI Model
```

Notice something important.

The model itself hasn't changed.

Only the information supplied to it has changed.

---

# Looking Ahead

As we continue building our local AI assistant, one question will repeatedly appear:

> "How can we safely provide more context?"

Sometimes that means reading a file.

Sometimes it means searching a Git repository.

Sometimes it means querying a knowledge base.

Sometimes it means calling external tools.

Almost every advanced AI capability ultimately revolves around providing the right context at the right time.

---

# Search Vocabulary

| Term | Meaning |
|------|---------|
| Context | Information available to the model during a request. |
| Context Window | Maximum amount of information the model can consider at once. |
| Prompt | The instructions written by the user. |
| Conversation History | Previous messages that remain available as context. |
| System Prompt | Hidden instructions supplied by the application before your prompt. |

Don't worry about **system prompts** yet.

We'll examine them in detail when we begin building our own AI assistants.

---

# Developer's Decision

If there is one lesson to remember from this chapter, it is this:

> **AI quality depends on context quality.**

When an AI produces an unexpected answer, don't immediately assume the model is incapable.

Instead, ask yourself:

- Did I provide enough information?
- Does the model know which file I'm referring to?
- Does it understand my project?
- Does it have access to the relevant documentation?
- Am I assuming knowledge that was never provided?

Learning to think in terms of context is one of the biggest mindset shifts when working with AI.

As software developers, we are used to thinking about algorithms.

When building AI-powered applications, we must also think carefully about **information flow**.

The next chapter introduces another fundamental concept that builds directly on context: **tokens**. Understanding what tokens are will explain model limits, pricing, context windows, and why seemingly short documents can consume far more memory than expected.