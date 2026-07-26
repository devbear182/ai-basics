# Chapter 26 – Future-Proofing Your AI Projects: Designing for Change

Throughout this handbook, you've probably noticed a recurring theme.

The names change.

The principles don't.

When this book was written, you might have heard names such as:

- ChatGPT
- Claude
- Gemini
- Qwen
- DeepSeek
- Llama
- Mistral

A year from now, that list will almost certainly look different.

The same is true for:

- AI applications,
- frameworks,
- IDE extensions,
- agent frameworks,
- MCP servers.

If you tightly couple your AI workflows to today's tools, you'll spend your time rewriting them instead of improving them.

Professional AI engineering assumes that change is inevitable.

The goal is not to prevent change.

The goal is to make change inexpensive.

---

# The Wrong Question

Beginners often ask:

> Which AI model should I invest in?

A better question is:

> How can I avoid depending too much on any single model?

That's a much more sustainable engineering mindset.

---

# A Software Engineering Analogy

Imagine writing a .NET application.

Would you write:

```csharp
SqlServerConnection connection = ...
```

everywhere?

Or would you introduce an abstraction?

```csharp
IRepository
```

The second approach makes replacing the implementation much easier.

AI systems benefit from exactly the same thinking.

---

# Depend on Capabilities

Suppose your Skill currently says:

> Use GPT-5.5 to review this pull request.

What happens if your company later standardises on another model?

Now you need to update every Skill.

Instead, think in terms of capabilities.

```
Review Pull Request
```

rather than

```
Use Model X
```

The application or runtime can decide which model is most appropriate.

Your Skill remains unchanged.

---

# Separate Policy from Implementation

Earlier, we discussed `instructions.md`.

Notice what belongs there:

- coding conventions,
- documentation style,
- architectural principles,
- review expectations.

Notice what usually does **not** belong there:

- specific model names,
- API keys,
- endpoint URLs,
- hardware settings.

Those belong in configuration.

This separation keeps your AI artifacts portable.

---

# Build Replaceable Layers

Let's revisit the architecture we've gradually assembled.

```
Instructions

↓

Skills

↓

Agents

↓

Tools

↓

Language Model

↓

Runtime
```

Every layer should be replaceable.

For example:

Replace:

```
Qwen
```

with

```
Llama
```

without changing your Skills.

Replace:

```
Open WebUI
```

with

```
ChatGPT Desktop
```

without rewriting your documentation.

Replace:

```
GitHub MCP Server
```

with

```
Azure DevOps MCP Server
```

without redesigning your Agent.

Good architecture isolates change.

---

# Keep Business Knowledge Outside the Model

One of the biggest lessons in this handbook has been:

Your model already knows software engineering.

What it doesn't know is **your company**.

That's why your valuable knowledge should live in places such as:

- documentation,
- architecture decision records,
- coding standards,
- Skills,
- instruction files,
- RAG knowledge bases.

These assets survive changing models.

If you change from one foundation model to another, your domain knowledge stays exactly where it belongs.

---

# Prefer Standards

Whenever possible, choose standards over proprietary features.

For example:

- Markdown instead of custom formats.
- Git repositories instead of hidden configuration.
- MCP instead of application-specific integrations.
- REST APIs instead of tightly coupled interfaces.

Standards tend to outlive products.

That's why experienced software architects trust them.

---

# Design for Teams

So far, you've mostly imagined building an AI assistant for yourself.

Now imagine your entire development team.

Questions suddenly change.

Who owns the instructions?

Who reviews new Skills?

How are Agents versioned?

How are changes tested?

How do new developers discover available capabilities?

These are software engineering questions.

Treat AI artifacts like production code.

Review them.

Version them.

Document them.

Improve them over time.

---

# Avoid the "Prompt Graveyard"

Many organisations already have one.

A folder containing:

```
Prompt-final.txt

Prompt-final-v2.txt

Prompt-new.txt

Prompt-final-really-final.txt
```

Nobody knows:

- which one is current,
- who wrote them,
- why they exist.

Instead, organise prompts exactly like code.

```
skills/

instructions/

agents/

knowledge/
```

Use meaningful names.

Write commit messages.

Review changes.

Future you will be grateful.

---

# Your AI Project Is a Software Project

By now, the directory might look like this.

```
AI-Assistant/

├── instructions/
│
├── skills/
│
├── agents/
│
├── knowledge/
│
├── scripts/
│
├── mcp/
│
├── docs/
│
└── README.md
```

Notice something surprising.

Nothing about this structure is fundamentally different from any other software repository.

That's intentional.

The closer your AI project resembles an ordinary software project, the easier it becomes to maintain.

---

# Engineering Note

Technology changes much faster than engineering principles.

If you optimise for today's model, today's framework or today's application, your solution will age quickly.

If you optimise for:

- modularity,
- clear interfaces,
- reusable artifacts,
- documented knowledge,
- standard protocols,

your project will adapt naturally as the AI ecosystem evolves.

This is one reason why we've deliberately spent so much time discussing architecture rather than individual products.

---

# Looking Ahead

By now, you've learned how to build an AI assistant that is:

- modular,
- maintainable,
- extensible,
- reliable,
- future-proof.

But one important topic remains before we bring everything together.

AI systems introduce new risks that traditional software often doesn't.

Prompt injection.

Data leakage.

Secrets.

Excessive permissions.

Unsafe automation.

In the next chapter, you'll learn practical security principles that every AI engineer should understand before giving an assistant access to production systems.

---

# Search Vocabulary

### Coupling

**Definition**

The degree to which one component depends on another.

**Compare to**

Loose coupling makes components easier to replace independently.

**Example**

A Skill depending on a generic "review code" capability instead of a specific model.

---

### Portability

**Definition**

The ability to move software or AI artifacts between different environments with little or no modification.

**Example**

Using the same instruction files with different AI applications.

---

### Vendor Lock-In

**Definition**

A situation where changing providers becomes difficult because software depends heavily on proprietary features.

**Example**

Building dozens of workflows that only function with one specific AI platform.

---

### Standard

**Definition**

A widely adopted specification that enables different systems to work together.

**Example**

Markdown, Git, HTTP and MCP.

---

# 🎉 Level Up!

You've learned one of the defining characteristics of experienced software architects:

They don't optimise for today's technology.

They optimise for tomorrow's change.

You now understand how to:

- keep domain knowledge independent from models,
- reduce coupling,
- organise AI artifacts like source code,
- favour standards over proprietary features,
- and build AI projects that survive an evolving ecosystem.

Perhaps the most important lesson is this:

**Models will change. Your engineering principles shouldn't.**

### Next Level

Your AI assistant is now powerful enough to access repositories, documentation and external systems.

That power comes with responsibility.

In the next chapter, you'll learn how to build AI systems that are not only capable—but also secure.

Because an AI assistant with unrestricted access can become just as dangerous as one with no access at all.