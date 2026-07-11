# Chapter 16 – Bringing AI into Your IDE

In the previous chapter, you gave your AI controlled access to your project's files.

This was an important milestone.

For the first time, your AI could understand more than the few snippets you manually pasted into a chat window.

But another small inconvenience quickly becomes noticeable.

Your workflow still looks something like this:

```
Visual Studio Code
        │
Copy code
        │
        ▼
Browser
        │
Ask question
        │
        ▼
Copy answer
        │
        ▼
Back to Visual Studio Code
```

After doing this a few dozen times, most developers start asking the same question:

> "Why isn't the AI simply available inside my editor?"

Fortunately, it can be.

---

# The Problem

Think about the tools you already use every day.

Your debugger is built into your IDE.

Git integration is built into your IDE.

Syntax highlighting is built into your IDE.

Code completion is built into your IDE.

None of those tools require you to constantly switch applications.

AI should feel the same.

The goal isn't replacing your IDE.

The goal is making AI another tool inside it.

---

# AI as a Development Tool

Earlier in this handbook, we separated:

- model,
- runtime,
- application.

Now we're adding another layer.

```
Foundation Model
        │
        ▼
Runtime
        │
        ▼
AI Application
        │
        ▼
IDE Integration
```

Notice something important.

The IDE extension usually **doesn't replace** your runtime.

Instead, it connects to it.

For example:

```
VS Code

↓

Continue Extension

↓

Ollama

↓

Qwen 2.5
```

Or, in a cloud setup:

```
VS Code

↓

GitHub Copilot

↓

Cloud Service

↓

Foundation Model
```

The editor becomes another client that communicates with the model.

---

# Two Common Approaches

Today, developers generally use one of two approaches.

## Cloud-Based IDE Assistants

Examples include:

- GitHub Copilot
- Cursor
- Windsurf

Advantages:

- minimal setup
- powerful hosted models
- seamless updates
- large context windows

Trade-offs:

- internet connection required
- data leaves your machine (depending on configuration)
- subscription costs
- limited control over the underlying models

---

## Local IDE Assistants

Examples include:

- Continue
- Cline
- Roo Code
- OpenHands (for more autonomous workflows)

Advantages:

- works with locally hosted models
- full control over the runtime
- easier experimentation
- better understanding of the underlying architecture

Trade-offs:

- more initial setup
- limited by local hardware
- requires choosing and managing models yourself

Neither approach is universally better.

Many developers use both.

For example:

- local models for experimentation,
- cloud models for particularly demanding tasks.

---

# What Can an IDE Assistant Actually Do?

At first glance, it may seem like an embedded chat window.

In reality, it can become much more.

Depending on the tool and its permissions, it can:

- explain code,
- search your repository,
- generate implementations,
- rename symbols,
- create documentation,
- generate tests,
- compare files,
- suggest refactorings,
- review pull requests,
- answer questions about the current workspace.

Notice how many of these tasks already fit naturally into your existing development workflow.

---

# The Importance of Context

Imagine asking:

> Explain this method.

If the IDE knows:

- the current file,
- the selected code,
- nearby classes,
- referenced interfaces,
- project structure,

then the AI receives far richer context than a browser chat usually provides.

This is one reason why IDE integrations often feel "smarter."

In many cases, they aren't using a better model.

They're simply providing better context automatically.

---

# Your First IDE Workflow

Suppose you open an unfamiliar class.

Instead of switching to your browser, you highlight a method and ask:

> Explain this method to a developer who has just joined the project.

The AI can now:

- inspect surrounding code,
- identify referenced classes,
- understand naming conventions,
- explain the implementation in context.

The conversation becomes much more natural because both you and the AI are looking at the same project.

---

# AI Is Becoming Part of Your Toolbox

Think about your daily development tools.

You probably don't consciously think:

> "Now I'll use Git."

You simply commit your changes.

Likewise, you don't think:

> "Now I'll use IntelliSense."

You just accept a completion.

Over time, AI becomes another tool you reach for naturally.

Not because it's special.

Because it's useful.

This is an important mindset shift.

You're no longer "using AI."

You're solving software engineering problems with the help of AI.

---

# Common Beginner Mistake

Many developers try to use AI for every single line of code.

This usually slows them down.

Instead, use AI where it provides the greatest leverage.

Good examples include:

- understanding unfamiliar code,
- exploring large codebases,
- generating repetitive boilerplate,
- documenting existing implementations,
- brainstorming alternative designs.

Keep writing straightforward code yourself.

Reserve AI for tasks where another perspective genuinely adds value.

---

# Engineering Note

An IDE assistant should enhance—not replace—your existing engineering practices.

Continue to:

- use source control,
- write tests,
- review code,
- run static analysis,
- perform manual verification.

AI is another tool in your toolbox.

It is not a substitute for sound engineering discipline.

---

# Looking Ahead

By now, your AI has become a capable development companion.

It understands your project.

It can inspect files.

It is available directly inside your IDE.

But you may have noticed something else.

You still repeat certain workflows.

For example:

- "Review this code according to our coding standards."
- "Generate unit tests following our conventions."
- "Write documentation using our template."

You're repeating the same instructions over and over again.

Wouldn't it be useful if those workflows themselves became reusable?

That's exactly what you'll build in the next chapter.

---

# Search Vocabulary

### IDE Integration

**Definition**

Connecting an AI assistant directly to a development environment so it can assist while you write, read and modify code.

**Example**

A Visual Studio Code extension that communicates with Ollama or a cloud AI service.

---

### Workspace

**Definition**

The collection of files, folders and projects currently opened in an editor or IDE.

**Compare to**

Similar to the current solution loaded in Visual Studio.

**Example**

An AI assistant may use the workspace to understand relationships between files before answering a question.

---

### Context-Aware Assistance

**Definition**

AI assistance that automatically considers relevant information—such as the current file, selected code or project structure—when generating responses.

**Example**

Explaining a method while also considering the interfaces and classes it depends on.

---

# 🎉 Level Up!

Your AI assistant has become part of your everyday development environment.

You now understand:

- how IDE integrations fit into the overall AI architecture,
- the differences between local and cloud-based development assistants,
- why automatic context improves AI responses,
- and how AI can naturally become another tool in your software engineering toolbox.

Most importantly, you've stopped thinking of AI as a separate application.

It's now part of your development workflow.

### Next Level

As you continue using your IDE assistant, you'll begin repeating the same multi-step tasks.

In the next chapter, you'll learn how to package those recurring workflows into reusable capabilities that can be executed consistently with minimal effort.

This is where simple prompts begin to evolve into **Skills**.