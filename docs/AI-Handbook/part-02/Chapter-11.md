# Chapter 11 – Talking to Your Model with Open WebUI

Congratulations!

You've reached your first practical milestone.

Your local AI model is running.

You can ask questions, generate code and experiment with prompts—all without relying on an online service.

However, you may also have noticed something.

Talking to your model through a terminal quickly becomes cumbersome.

Let's solve that.

---

# Level Up

## Previous Capability

✅ Run a local AI model.

## New Capability

🎯 Build a comfortable chat experience on top of your local AI runtime.

You'll learn:

- why an AI application exists
- why Ollama and Open WebUI are separate programs
- how they communicate
- why separating them is actually a good design

---

# A Common Beginner Question

Many people install Ollama and then immediately wonder:

> "Why do I also need Open WebUI?"

It's a good question.

After all, Ollama can already answer prompts.

The answer is surprisingly similar to something every software developer already knows.

---

# Software Engineering Analogy

Imagine writing a REST API.

The API contains all the business logic.

Would you normally ask users to interact with it using `curl`?

Probably not.

Instead, you build a web application.

```text
User

↓

Browser

↓

Web Application

↓

REST API
```

The web application doesn't replace the API.

It simply provides a much better user experience.

Exactly the same thing happens here.

---

# Ollama Is Not a Chat Application

Ollama's responsibility is intentionally small.

It:

- downloads models
- starts models
- executes models
- returns responses

It is **not** designed to be:

- a polished chat application
- a document manager
- a prompt library
- a workspace
- a collaboration platform

Those responsibilities belong somewhere else.

---

# Meet Open WebUI

Open WebUI is one of the most popular open-source applications for interacting with local AI models.

Think of it as:

> **"ChatGPT for your own computer."**

Instead of talking directly to Ollama through PowerShell, you'll open a browser.

Behind the scenes, Open WebUI forwards every request to Ollama.

The architecture now looks like this.

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

Notice something important.

The model hasn't changed.

Only the user interface has.

---

# Why Is This Separation Useful?

At first glance, having two applications may seem unnecessary.

In reality, separating responsibilities makes the system far more flexible.

Imagine you decide to replace Qwen with Llama.

Does Open WebUI need to change?

No.

Suppose you replace Open WebUI with another chat application.

Does Ollama need to change?

Again, no.

Each component has exactly one responsibility.

This follows the same design principles you've probably used in your own software projects.

---

# What Does Open WebUI Add?

Compared to using the terminal, Open WebUI provides many quality-of-life improvements.

For example:

- chat history
- multiple conversations
- Markdown rendering
- code formatting
- file uploads
- conversation management
- model selection
- reusable prompts
- user management (optional)

Notice that none of these features belong inside the model itself.

They belong in the application.

---

# A First Look at the Bigger Picture

At the moment, Open WebUI mainly provides a pleasant way to chat.

Later, we'll use it for much more.

For example:

- comparing models
- testing prompts
- creating assistants
- experimenting with system prompts
- managing documents

For now, however, we'll keep things simple.

One capability at a time.

---

# Installing Open WebUI

Open WebUI offers several installation options.

The most common approaches are:

- Docker (recommended)
- Python
- Existing container platforms

Throughout this handbook, we'll use the Docker installation because it is:

- easy to update
- isolated from your system
- commonly used
- well documented

> **Prerequisite**
>
> Docker Desktop should already be installed.
>
> If not, complete the installation described in the appendix before continuing.

Start Open WebUI using the official Docker command.

*(We'll keep the exact command in sync with the current Open WebUI documentation, as it occasionally changes.)*

Once started, open your browser and navigate to the local address shown in the console.

Create your first local account.

---

# Connecting to Ollama

This is the nice part.

Normally there isn't much to configure.

Open WebUI automatically detects Ollama running on your computer.

If everything works, your previously downloaded model appears in the model list.

Select:

```
qwen2.5:7b
```

Start a new conversation.

Ask the same question you asked in the previous chapter.

The answer should be identical.

Only the experience has improved.

---

# What Actually Happened?

Although the interface looks completely different, the request still follows the same path.

```text
Browser

↓

Open WebUI

↓

Ollama

↓

Qwen

↓

Generated Response

↓

Browser
```

Open WebUI didn't become intelligent.

It simply became the messenger between you and the model.

---

# Why This Matters Later

Remember our long-term goal.

We don't just want to chat.

Eventually we want our AI assistant to:

- understand projects
- read files
- edit code
- use Git
- execute tools
- automate workflows

Notice where these features naturally belong.

Not inside the runtime.

Not inside the model.

They belong in the application layer.

That's one reason understanding the architecture is so valuable.

---

# Engineering Note

When you're learning AI, avoid installing several chat applications at once.

Use one application until you're comfortable with it.

Once you understand the architecture, trying alternatives becomes straightforward because you'll already know which layer you're replacing.

---

# Looking Ahead

At this point you have:

✅ A local runtime.

✅ A local model.

✅ A modern chat interface.

That's enough to begin experimenting.

But another question naturally arises.

Should you always use the same model?

Or should you choose different models for different tasks?

In the next chapter, we'll learn how to select models based on hardware, speed, quality and intended use.

You'll discover that choosing the right model is often more important than simply choosing the largest one.

---

# Search Vocabulary

| Term | Meaning |
|------|---------|
| Chat Application | Software that provides a user interface for interacting with AI models. |
| Open WebUI | An open-source chat application that connects to local or remote AI runtimes. |
| Separation of Concerns | A software design principle where each component has a single responsibility. |
| Frontend | The user-facing part of an application. |
| Backend | The component performing the underlying work, such as running AI models. |

---

# Capability Unlocked

## 🎉 Level Up!

✅ You now have a comfortable interface for interacting with your local AI.

More importantly, you've learned another architectural principle:

**The runtime executes the model.**

**The application provides the experience.**

Keeping these responsibilities separate makes your AI workbench easier to understand, maintain and extend as new tools emerge.