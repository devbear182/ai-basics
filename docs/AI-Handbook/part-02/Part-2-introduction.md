# Chapter 10 – Building Your First AI Workbench

Congratulations.

You now understand the core concepts behind modern AI systems.

You know:

- what AI models are
- what transformers do
- why tokens exist
- how context works
- why prompting matters
- how commercial AI ecosystems are structured

Until now, however, everything has been theoretical.

It's time to build something.

This chapter marks the beginning of **Part II**, where we gradually assemble a practical AI workbench for software development.

By the end of Part II, you'll have a local AI assistant that can help you write, understand and modify software in a way that feels surprisingly similar to commercial tools like GitHub Copilot.

The difference is that you'll understand every component involved.

---

# The Goal

Let's start with the end in mind.

Imagine your ideal AI assistant while working in Visual Studio Code.

You ask:

> "Review my latest changes."

The assistant responds by:

- reading the modified files
- understanding your project structure
- checking recent Git changes
- finding relevant documentation
- suggesting improvements
- optionally modifying files
- explaining every change

Notice something important.

This requires much more than an AI model.

It requires an entire system.

---

# A Common Beginner Misconception

Many newcomers believe that downloading a model is enough.

The reasoning usually goes like this:

> "I downloaded Qwen 2.5 7B, so where is my Copilot?"

Unfortunately, that's a bit like downloading the .NET runtime and expecting Visual Studio to appear.

The runtime is only one piece of the puzzle.

A productive AI assistant consists of multiple cooperating components.

---

# Building an AI Assistant Is Like Building a Development Environment

Think about setting up a new Windows development machine.

You don't install only one piece of software.

Instead, you assemble a collection of tools.

For example:

```text
Windows
│
├── Git
├── Visual Studio Code
├── .NET SDK
├── Docker
├── PowerShell
└── SQL Server
```

Each tool has a specific responsibility.

Together, they create a productive development environment.

A local AI workbench follows exactly the same philosophy.

---

# The Big Picture

At a high level, our local AI system will eventually look like this.

```text
                    You
                     │
                     ▼
          Visual Studio Code
                     │
                     ▼
      AI Extension (Continue / Roo Code / ...)
                     │
                     ▼
              Ollama Runtime
                     │
                     ▼
             AI Model (Qwen)
                     │
      ┌──────────────┼──────────────┐
      ▼              ▼              ▼
    Files           Git          Terminal
      │              │              │
      └──────────────┼──────────────┘
                     ▼
              Your Project
```

Don't worry if every box isn't familiar yet.

Over the next chapters, we'll build this architecture one component at a time.

---

# Every Component Has One Job

One reason AI tooling feels overwhelming is that many products have similar-sounding names.

The easiest way to understand them is to ask:

> **"What is this component responsible for?"**

Let's briefly introduce each piece.

---

## The Model

Examples:

- Qwen
- Llama
- Gemma
- Mistral

Responsibility:

Generate text, code and reasoning.

The model is the "brain."

By itself, however, it cannot access your files or interact with your computer.

---

## The Runtime

Examples:

- Ollama
- LM Studio (also provides runtime capabilities)

Responsibility:

Load the model into memory and execute it.

Think of the runtime as the engine that allows applications to use the model.

Without a runtime, the model is simply a collection of files on disk.

---

## The Application

Examples:

- Open WebUI
- ChatGPT
- Claude
- LM Studio

Responsibility:

Provide a user interface for interacting with one or more models.

Applications focus on the user experience.

Many applications don't execute models themselves.

Instead, they communicate with a runtime.

---

## The IDE Extension

Examples:

- Continue
- Roo Code
- Cline
- GitHub Copilot

Responsibility:

Bring AI directly into your development environment.

These extensions understand concepts such as:

- open files
- source code
- selections
- diagnostics
- projects

This additional context is one reason they often outperform a simple chatbot for development tasks.

---

## The Tools

Examples:

- file reader
- file editor
- terminal
- Git
- web search

Responsibility:

Allow the AI to interact with the outside world.

Without tools, the model can only generate text.

With tools, it can begin performing useful work.

We'll spend several chapters exploring these capabilities later in Part II.

---

# A Familiar Software Architecture

If you're a software developer, the overall architecture should already look familiar.

```text
Presentation Layer
        │
Business Logic
        │
Infrastructure
        │
Operating System
```

Our AI workbench follows the same layered approach.

```text
Application
        │
AI Extension
        │
Runtime
        │
Model
        │
Operating System
```

Each layer depends on the one below it.

Each layer hides complexity from the one above it.

Understanding this architecture makes it much easier to troubleshoot problems.

---

# Commercial vs Local Revisited

Earlier, we compared commercial and local AI ecosystems.

Now we can revisit that comparison with a deeper understanding.

## Commercial

```text
You
 │
 ▼
ChatGPT
 │
 ▼
OpenAI
```

Most of the layers are hidden from you.

The provider manages everything.

---

## Local

```text
You
 │
 ▼
Open WebUI
 │
 ▼
Ollama
 │
 ▼
Qwen
```

You assemble the layers yourself.

This requires more initial effort.

In return, you gain flexibility and control.

The underlying architecture, however, is remarkably similar.

---

# Building Incrementally

One of the biggest mistakes beginners make is trying to build the final system immediately.

For example:

> I want a fully autonomous AI software engineer that edits my code, runs tests, creates pull requests and deploys my application.

While exciting, that goal involves many independent capabilities.

Instead, we'll build our assistant incrementally.

Our roadmap looks like this.

```text
Step 1
Chat with a local model

↓

Step 2
Use a better user interface

↓

Step 3
Integrate with VS Code

↓

Step 4
Read project files

↓

Step 5
Understand repositories

↓

Step 6
Edit files

↓

Step 7
Use tools

↓

Step 8
Automate workflows
```

Each step introduces only one major concept.

This mirrors how software projects are typically developed.

---

# Our Guiding Principle

Throughout Part II, we'll repeatedly ask the same question:

> **What new capability are we adding?**

For example:

| Capability | New Component |
|------------|---------------|
| Chat locally | Ollama |
| Better chat interface | Open WebUI |
| IDE integration | Continue |
| File access | Tools |
| Project knowledge | RAG |
| Long-term memory | Memory store |
| Autonomous workflows | Agents |

This table provides a mental map for the remainder of the handbook.

Whenever we install a new component, we'll know exactly why it exists.

---

# Choosing Software

If you've searched for local AI tutorials online, you've probably noticed that people recommend very different software stacks.

Some prefer:

- Ollama
- Open WebUI
- Continue

Others use:

- LM Studio
- VS Code
- Roo Code

Others prefer:

- Claude Desktop
- MCP Servers
- External APIs

This variety often confuses newcomers.

The good news is that these systems are not competing architectures.

Most of them simply occupy different positions within the same overall ecosystem.

As your understanding grows, you'll find it much easier to evaluate new tools because you'll ask:

> **Which layer does this replace—or extend?**

Rather than:

> **Should I abandon everything and start over?**

---

# Looking Ahead

The next chapter introduces the first component we'll actually install:

**Ollama.**

You'll learn:

- what Ollama is
- why it has become one of the most popular local AI runtimes
- how it differs from applications like Open WebUI
- where it fits within the architecture we've introduced today

Once Ollama is running, we'll have the foundation upon which every remaining chapter in Part II will build.

---

# Search Vocabulary

| Term | Meaning |
|------|---------|
| AI Workbench | A collection of software components used to work productively with AI. |
| Runtime | Software responsible for loading and executing AI models. |
| IDE Extension | An extension that integrates AI capabilities directly into an editor or IDE. |
| Tool | A capability that allows an AI to interact with external systems, such as files or Git. |
| Layered Architecture | A design in which each component has a clearly defined responsibility and depends only on lower layers. |

---

# Developer's Decision

At this point, resist the temptation to search for **"the best local AI setup."**

There isn't one.

Just as there is no universally best software architecture, the right AI workbench depends on your goals, hardware and workflow.

Instead, focus on understanding the role of each component.

Once you know what every layer is responsible for, replacing one component with another becomes straightforward.

That's an empowering realization.

You're no longer memorizing products.

You're understanding an architecture.

And once you understand the architecture, new AI tools become much less intimidating—they're simply new implementations of familiar ideas.