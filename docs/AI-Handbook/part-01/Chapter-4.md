# Chapter 4 – Models, Applications, Platforms and Runtimes

If there is one chapter that will save you hours of confusion, it is probably this one.

One of the biggest reasons developers struggle to understand the AI ecosystem is that people constantly mix up **models**, **applications**, **platforms** and **runtimes**.

Consider the following statements:

> "I'm using ChatGPT."

> "I'm using GPT-4."

> "I'm using OpenAI."

> "I'm using Copilot."

> "I'm using Claude."

> "I'm using Ollama."

Technically, these do **not** all describe the same kind of thing.

Some are companies.

Some are applications.

Some are models.

Some are platforms.

Some are runtimes.

Yet they are often used interchangeably in everyday conversation.

As software developers, we naturally think in terms of architecture and responsibilities.

Let's apply that same mindset here.

---

# A Familiar Software Architecture

Suppose someone tells you:

> "I'm using Visual Studio."

As a developer, you immediately know that doesn't tell the whole story.

You might ask:

- Which programming language?
- Which .NET version?
- Which compiler?
- Which project?
- Which Git repository?

"Visual Studio" is only one layer.

A typical development environment might look like this.

```text
Developer
    │
    ▼
Visual Studio
    │
    ▼
.NET SDK
    │
    ▼
C# Compiler
    │
    ▼
Application
    │
    ▼
Windows
```

Nobody confuses Visual Studio with the C# compiler.

Nobody thinks .NET is the same thing as Windows.

Each component has a different responsibility.

Modern AI systems work exactly the same way.

---

# The Layers of an AI System

A modern AI assistant typically consists of several independent layers.

```text
You
 │
 ▼
Application (Chat Interface / IDE)
 │
 ▼
AI Runtime
 │
 ▼
AI Model
 │
 ▼
CPU / GPU
 │
 ▼
Operating System
```

Every layer has a specific purpose.

Understanding these responsibilities makes almost every AI product easier to understand.

---

# Layer 1 – The Model

The model is the "brain" of the system.

Examples include:

- GPT
- Claude
- Qwen
- Llama
- Gemma
- Mistral

The model receives input and generates output.

By itself, however, it does nothing.

A model is similar to a compiled executable.

Until something starts it and communicates with it, it simply exists as data on disk.

---

## Important

A model is **not** a chatbot.

A model is **not** a website.

A model is **not** ChatGPT.

The model is only one component within a much larger system.

---

# Layer 2 – The Runtime

A runtime is responsible for loading the model into memory and executing it.

Without a runtime, your operating system has no idea how to run an AI model.

You have already seen this concept many times.

Examples include:

| Technology | Runtime |
|------------|---------|
| C# | .NET Runtime |
| Java | JVM |
| Python | Python Interpreter |

AI has runtimes as well.

Examples include:

- Ollama
- llama.cpp
- vLLM
- TensorRT-LLM

Although they all execute AI models, they focus on different scenarios.

Some are optimized for local desktops.

Others target cloud servers.

Others specialize in NVIDIA GPUs.

Throughout this handbook we will primarily use **Ollama** because it provides an excellent experience for Windows developers getting started with local AI.

---

# What Is Ollama?

Ollama is a **local AI runtime**.

Its primary responsibilities are:

- downloading models
- storing models
- loading models into memory
- executing inference
- exposing a simple API for applications

Notice what is **not** on that list.

Ollama does **not** create AI models.

Ollama does **not** train AI models.

Ollama does **not** provide a chat interface.

It runs models.

---

## Gaming Analogy

If you've used Steam, imagine this:

Steam

- downloads games
- installs games
- updates games
- launches games

Steam is not the game.

Likewise:

Ollama

- downloads models
- stores models
- updates models
- launches models

Ollama is not the model.

For many developers, this analogy immediately makes Ollama "click."

---

# Layer 3 – The Application

Most users never interact with a runtime directly.

Instead, they interact with an application.

Examples include:

- ChatGPT
- Claude
- Open WebUI
- GitHub Copilot
- LM Studio
- Continue
- Roo Code
- Cline

These applications provide a user interface.

They send requests to a model and display the responses.

Think of them as clients.

---

# What Is Open WebUI?

Open WebUI is a web application that provides a user experience similar to ChatGPT.

Instead of hosting AI models itself, it connects to one or more model providers.

Those providers might include:

- Ollama
- OpenAI
- Anthropic
- Google
- Azure OpenAI
- others

This is one reason Open WebUI is so popular.

You can switch between local and cloud-hosted models while keeping the same interface.

---

## Software Engineering Analogy

Suppose you use Azure Data Studio.

Azure Data Studio is not the database.

It simply connects to databases.

Likewise,

Open WebUI is not the AI model.

It connects to AI models.

---

# Layer 4 – The Platform

Some companies provide the entire stack for you.

OpenAI is a good example.

When using ChatGPT, you usually don't think about:

- servers
- GPUs
- runtimes
- model storage
- APIs

OpenAI manages all of that.

You simply open the website and start chatting.

This is a **managed platform**.

---

# Local vs Managed

Let's compare two common setups.

## Managed

```text
You
 │
 ▼
ChatGPT
 │
 ▼
OpenAI Platform
 │
 ▼
GPT Model
```

Everything below ChatGPT is managed for you.

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
 │
 ▼
Your GPU
```

You are responsible for everything below Open WebUI.

That gives you much greater flexibility—but also more responsibility.

---

# Where Do Companies Fit?

One thing often causes confusion.

Companies build products.

Products use models.

Consider these examples.

| Company | Product | Model |
|---------|----------|--------|
| OpenAI | ChatGPT | GPT |
| Anthropic | Claude | Claude |
| Microsoft | GitHub Copilot | GPT / Claude / others* |
| Google | Gemini | Gemini |
| Alibaba | Qwen Chat | Qwen |

Notice how the same company may produce:

- applications
- APIs
- models

When reading AI documentation, always ask:

> Is this referring to the company, the product or the model?

---

# A Special Case: GitHub Copilot

GitHub Copilot is particularly interesting because it illustrates an important architectural principle.

Many developers initially assume that Copilot **is** an AI model.

It isn't.

GitHub Copilot is an application that orchestrates one or more AI models on your behalf.

Depending on your subscription and organization, it may use different underlying models for different tasks.

As a user, you primarily interact with Copilot.

Copilot decides which model should perform the work.

This separation between **application** and **model** becomes increasingly common in modern AI systems.

---

# Why This Matters

Imagine two developers.

Developer A says:

> "Claude is much better."

Developer B says:

> "I'm using Open WebUI."

They are discussing different layers.

One is talking about a model family.

The other is talking about an application.

Once you recognize the layers, conversations like this become much easier to follow.

---

# Putting Everything Together

Let's assemble everything we've learned so far.

```text
                Company
                   │
      ┌────────────┴────────────┐
      │                         │
   Platform                 Model Family
      │                         │
      ▼                         ▼
 ChatGPT                      GPT
 Claude                       Claude
 Copilot                      Qwen
 Open WebUI                   Llama
      │
      ▼
 Runtime
      │
      ▼
 Ollama
      │
      ▼
 Hardware
```

This diagram is intentionally simplified, but it captures the most important relationships.

Every new tool you encounter can now be placed somewhere within this architecture.

---

# Search Vocabulary

As you explore local AI, you'll frequently encounter these terms.

| Term | Meaning |
|------|---------|
| Model | The trained AI itself. |
| Runtime | Software that executes AI models. |
| Application | User interface that communicates with models. |
| Platform | A complete managed AI service. |
| API | A programming interface applications use to communicate with AI services or runtimes. |

These words are sometimes used loosely online.

As a developer, using them precisely will help both your understanding and your communication with others.

---

# Developer's Decision

You now know enough to make sense of most AI architectures.

More importantly, you've learned a reusable way to analyze any new AI product:

1. Who built it?
2. Is it a company, a product or a model?
3. Is it an application or a runtime?
4. Does it run locally or in the cloud?
5. Which model does it ultimately use?

These five questions will help you quickly understand almost any AI tool you encounter.

In the next chapter, we'll use this mental model to compare the most common commercial and local AI ecosystems. You'll see how products like ChatGPT, Claude, GitHub Copilot, Ollama and Open WebUI relate to one another—and why they often feel similar despite being built very differently.