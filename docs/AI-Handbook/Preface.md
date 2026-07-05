# Preface

> *Learn only what you need, when you need it. Build as you learn.*

Welcome!

If you picked up this handbook, chances are you have already experienced what modern AI can do. Perhaps you have used ChatGPT to explain a piece of code, GitHub Copilot to generate a function, or Claude to review a design document. You have seen AI solve problems in seconds that previously required minutes or even hours of work.

At the same time, you have probably noticed that the AI ecosystem has become increasingly confusing.

Every week introduces new buzzwords:

- AI
- Machine Learning
- Deep Learning
- Foundation Models
- Large Language Models (LLMs)
- Agents
- RAG
- MCP
- Embeddings
- Quantization
- Fine-tuning
- Context Windows

Blogs, videos and conference talks often assume you already understand these terms. If you don't, it becomes difficult to even search for the information you actually need.

This handbook was written to bridge exactly that gap.

---

# Who This Book Is For

This book is written for software developers.

Not AI researchers.

Not data scientists.

Not mathematicians.

If you already know concepts like source control, REST APIs, databases, Docker, Visual Studio, GitHub or Azure DevOps, then you already possess many of the skills needed to build AI-powered software.

You do **not** need a background in machine learning.

You do **not** need to understand linear algebra.

You do **not** need to know how to train neural networks.

Instead, this handbook assumes something different:

> You already know how to build software.
>
> Now you want to learn how AI becomes another component within your software architecture.

---

# The Goal

The goal is not to become an AI expert.

The goal is to become a developer who confidently answers questions like:

- Which AI model should I choose?
- Should I use ChatGPT or host a model locally?
- What exactly is Ollama?
- Why do people combine Open WebUI with Ollama?
- What is an AI Agent?
- How does GitHub Copilot actually work?
- Why does Claude seem smarter than my local model?
- How can I safely give an AI access to my files?
- How can I combine my software engineering knowledge with my company's domain knowledge?

By the end of this handbook, you should not only understand these concepts—you should have built your own local AI assistant step by step.

---

# What You Will Build

Throughout this handbook we will continuously improve the same AI system.

Initially, it is very simple.

```text
You
 │
 ▼
ChatGPT
```

Later, you will replace the hosted service with your own local components.

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

As your understanding grows, so does your system.

```text
You
 │
 ▼
Open WebUI
 │
 ▼
AI Agent
 │
 ├── File System
 ├── Git
 ├── PowerShell
 └── Browser
 │
 ▼
Ollama
 │
 ▼
Qwen
```

By the end of the book you will understand how systems like GitHub Copilot or Claude Code combine language models with tools to perform increasingly autonomous work.

---

# AI Is Another Software Stack

One of the biggest misconceptions surrounding AI is that it is somehow "magic."

It is not.

Modern AI systems are software systems.

Like every software system, they consist of multiple layers that each have a specific responsibility.

A web application is not just "a website."

It consists of:

- a browser
- a web server
- an application
- a database
- an operating system
- hardware

Likewise, an AI assistant is not just "an AI."

It consists of multiple independent components working together.

```text
You
 │
 ▼
User Interface
 │
 ▼
AI Assistant / Agent
 │
 ▼
Model Runtime
 │
 ▼
AI Model
 │
 ▼
Operating System
 │
 ▼
Hardware
```

Understanding these layers is one of the most valuable mental models you will gain from this handbook.

Once you understand them, almost every AI product suddenly becomes much easier to reason about.

---

# A Familiar Perspective

Throughout the book we will intentionally compare AI concepts to technologies that software developers already know.

Instead of introducing completely new mental models, we will build upon existing ones.

For example:

| Software Development | AI |
|----------------------|----|
| Visual Studio | Open WebUI |
| .NET Runtime | Ollama |
| ASP.NET Application | Qwen Model |
| REST API | Model API |
| Git | AI Memory / Knowledge Sources |
| Plugins | Tools / MCP Servers |

These analogies are not perfect, but they provide useful intuition and help answer an important question whenever a new concept appears:

> "Where does this fit?"

---

# How to Read This Book

This handbook follows a simple philosophy:

Learn only what you need, when you need it.

Every chapter introduces a small number of new concepts.

Each concept answers four questions:

1. What is it?
2. Where does it fit?
3. When do I actually need it?
4. How does it help me build a better AI assistant?

Some chapters contain optional deep dives.

These sections are clearly marked and provide additional background for readers who want to explore a topic further. They are **not** required to continue with the practical parts of the handbook.

If your goal is simply to build a capable AI assistant, it is perfectly acceptable to skip these sections and return to them later.

---

# A Word on AI

AI is currently evolving at an incredible pace.

New models appear almost every month.

New tools appear almost every week.

Many product names will change.

Some companies will disappear.

Others will merge or introduce entirely new technologies.

The underlying principles, however, change much more slowly.

This handbook therefore focuses primarily on principles rather than products.

If you understand the principles, learning the next tool becomes significantly easier.

Our objective is not to memorize today's technology.

Our objective is to build a mental model that remains useful for years.

---

Let's begin by answering what appears to be a simple question:

> **What is Artificial Intelligence?**
