# Chapter 10 – Running Your First Local Model with Ollama

You've now reached the point where theory meets practice.

Up until now, every chapter answered questions such as:

- What is a model?
- What is a runtime?
- What is an application?
- How do they relate?

Now we're finally going to install something.

More importantly, you'll understand **why** you're installing it.

---

# What Problem Does Ollama Solve?

Imagine someone gives you a model file.

For example:

- Qwen 2.5
- Llama 3
- Gemma

What now?

Unlike a Word document or an executable, you can't simply double-click a model and start chatting.

A model is not an application.

It is trained data that must be loaded into memory and executed by software designed specifically for that purpose.

That software is called a **runtime**.

Ollama is currently one of the most popular local AI runtimes.

Its job is surprisingly simple:

> Load a model and make it available for applications to use.

Nothing more.

Nothing less.

---

# Where Does Ollama Fit?

Let's revisit our architecture.

```text
You
 │
 ▼
Application
(Open WebUI)
 │
 ▼
Runtime
(Ollama)
 │
 ▼
Model
(Qwen)
```

Without Ollama:

❌ No runtime

↓

No model execution

↓

No AI.

---

# Software Engineering Analogy

Think about .NET.

You write:

```csharp
Console.WriteLine("Hello");
```

Can Windows execute this source code directly?

No.

You need the .NET Runtime.

The runtime knows how to execute .NET applications.

AI models work similarly.

Qwen does not "run itself."

It requires a runtime that understands how to execute transformer models efficiently.

Ollama fills that role.

---

# Why Has Ollama Become So Popular?

Several reasons contributed to Ollama's popularity.

It is:

- easy to install
- cross-platform
- beginner-friendly
- actively maintained
- supports many popular open-weight models
- integrates well with other AI applications

Most importantly, many other AI tools already know how to communicate with Ollama.

This makes it an excellent foundation for a local AI workbench.

---

# Alternatives

Ollama is not the only runtime.

Some alternatives include:

| Software | Typical Use |
|-----------|-------------|
| Ollama | General-purpose local runtime |
| LM Studio | Desktop application with built-in runtime |
| llama.cpp | Low-level runtime used by many projects |
| vLLM | High-performance inference server for larger deployments |

Notice that these products occupy similar positions within the architecture.

Choosing one runtime rarely forces you to replace every other component.

---

# Installing Ollama

Visit the official Ollama website and download the Windows installer.

Install it using the default settings.

After installation, open a new PowerShell window.

Run:

```powershell
ollama --version
```

If the installation was successful, you should see the installed version number.

---

# Downloading Your First Model

Now let's download Qwen.

```powershell
ollama pull qwen2.5:7b
```

This command downloads the model from Ollama's model library.

Depending on your internet connection, this may take several minutes.

Once downloaded, the model is stored locally.

Future conversations do **not** require another download.

---

# Running the Model

Now start your first local conversation.

```powershell
ollama run qwen2.5:7b
```

After a short loading phase, you should see a prompt.

Try asking:

> Explain dependency injection in C#.

If everything works, congratulations.

You are now talking to a completely local AI model.

No browser.

No cloud service.

No subscription.

---

# What Actually Happened?

Although it looked like a simple command, several things happened behind the scenes.

```text
You

↓

PowerShell

↓

Ollama

↓

Load Qwen into memory

↓

Run inference

↓

Generate tokens

↓

Display response
```

Understanding this pipeline will make troubleshooting much easier later.

---

# Measuring Success

Before continuing to the next chapter, verify the following.

✅ `ollama --version` works.

✅ `ollama list` shows your downloaded model.

✅ `ollama run qwen2.5:7b` starts successfully.

✅ The model answers basic questions.

If all four checks pass, your runtime is working correctly.

---

# Common Beginner Mistakes

## "The model downloads every time."

It doesn't.

The model is stored locally after the first download.

---

## "My model is slow."

Large models require significant RAM and CPU or GPU resources.

Performance depends on both your hardware and the chosen model.

We'll discuss model selection in a later chapter.

---

## "I expected something like ChatGPT."

At the moment, you're interacting directly with the runtime.

The user experience is intentionally minimal.

In the next chapter we'll install a proper user interface.

---

# Engineering Note

At this stage, resist the temptation to download many different models.

One reliable model is far more valuable than twenty models you've barely used.

Learning how to work effectively with a single model teaches skills that transfer to every other model.

---

# Looking Ahead

Right now you're communicating through a terminal.

That proves the runtime works.

It doesn't provide a particularly pleasant user experience, though.

The next chapter introduces **Open WebUI**.

We'll add a modern chat interface while keeping Ollama as the underlying runtime.

For the first time, you'll see how independent AI components begin working together.

---

# Search Vocabulary

| Term | Meaning |
|------|---------|
| Runtime | Software responsible for executing AI models. |
| Inference | The process of generating an answer from a trained model. |
| Model Library | A collection of downloadable AI models. |
| Local Inference | Running a model entirely on your own computer. |

---

# Capability Unlocked

✅ You can now execute AI models locally.

This may not seem like much yet.

However, every capability we'll add throughout the remainder of the handbook builds on this single foundation.

Without a runtime, there is no local AI assistant.