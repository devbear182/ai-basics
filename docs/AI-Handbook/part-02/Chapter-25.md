# Chapter 25 – Designing AI Workflows: Building Maintainable AI Systems

In the previous chapter, you learned that reliable AI systems don't happen by accident.

They are engineered.

You also discovered that modern AI applications are pipelines composed of many specialised components.

Now imagine your AI assistant after several months.

It contains:

- dozens of instruction files,
- multiple Skills,
- several Agents,
- access to various MCP servers,
- project documentation,
- long-term memory,
- custom helper scripts.

Everything works.

But something feels familiar.

The system has become difficult to understand.

If that sounds familiar, it should.

Software developers have been solving exactly this problem for decades.

The same design principles that help us build maintainable software also help us build maintainable AI systems.

---

# The Temptation

As your assistant grows, it becomes tempting to solve every new problem in the same way:

> "I'll just add another prompt."

At first, this works remarkably well.

Then six months later you have:

```
Prompt A

Prompt B

Prompt C

Prompt D

Prompt E

...

Prompt Z
```

Nobody remembers:

- why they exist,
- which one is used,
- which one is outdated,
- which one depends on another.

You've accidentally reinvented "spaghetti code."

---

# A Software Engineering Analogy

Imagine a C# application.

Would you put everything into one class?

```text
Program.cs

12,000 lines
```

Probably not.

Instead, you separate responsibilities.

```
Controllers

↓

Services

↓

Repositories

↓

Utilities
```

AI systems deserve the same discipline.

---

# Every Component Should Have One Responsibility

Let's revisit the building blocks you've learned so far.

Each solves a different problem.

| Component | Responsibility |
|-----------|----------------|
| Instructions | Define behaviour |
| Skill | Perform one reusable task |
| Agent | Coordinate multiple steps |
| Deterministic Code | Compute facts |
| RAG | Retrieve knowledge |
| Memory | Remember useful information |
| MCP | Connect external systems |

Notice something important.

None of these components replaces another.

Each has a clearly defined purpose.

Whenever one component starts doing another component's job, complexity increases.

---

# A Decision Tree

When implementing a new capability, ask yourself a few simple questions.

```
Is the answer always the same?

↓

Yes

↓

Write code.
```

```
No

↓

Does the AI need external information?

↓

Yes

↓

Use RAG or a Tool.
```

```
No

↓

Does the AI simply need guidance?

↓

Use Instructions.
```

```
Does the workflow require several coordinated steps?

↓

Use an Agent.
```

```
Is the task reusable?

↓

Create a Skill.
```

Notice that prompting is only one option among several.

Experienced AI engineers choose the right building block for the problem.

---

# Build Layers, Not Shortcuts

One of the easiest mistakes is skipping layers.

For example:

```
User

↓

Agent

↓

Language Model
```

This may work for simple experiments.

A more maintainable design might be:

```
User

↓

Instructions

↓

Agent

↓

Skill

↓

Deterministic Code

↓

MCP Tool

↓

Language Model
```

Although there are more components, each one becomes easier to understand and maintain.

---

# Small Skills Beat Giant Skills

Suppose you create a Skill called:

```
Software Engineer
```

It performs:

- code review,
- bug investigation,
- architecture analysis,
- documentation,
- testing,
- deployment planning.

This quickly becomes difficult to maintain.

Instead, prefer smaller Skills.

For example:

```
Explain Architecture
```

```
Review Pull Request
```

```
Investigate Test Failure
```

```
Generate Release Notes
```

Each Skill has one clear responsibility.

This should remind you of the Single Responsibility Principle.

That's no coincidence.

---

# Agents Should Coordinate, Not Know Everything

A common beginner mistake is creating enormous Agents.

Instead, think of an Agent like an experienced team lead.

A team lead doesn't personally perform every task.

Instead, they decide:

- who should do what,
- in which order,
- when to stop,
- when to ask for help.

Similarly, a good Agent should coordinate:

- Skills,
- tools,
- retrieval,
- memory,

rather than containing all of the implementation itself.

---

# Prefer Stable Interfaces

Earlier, we discussed MCP.

This introduces another familiar software engineering principle.

Instead of depending on specific implementations:

```
GitHub

↓

Jira

↓

SQL Server
```

your Agent depends on capabilities.

```
Search Work Items

Read Repository

Query Database
```

The underlying implementation can later change.

The Agent doesn't need to know.

This is dependency inversion applied to AI systems.

---

# Configuration Belongs in Files

One temptation is embedding large amounts of information directly into prompts.

Instead, ask yourself:

Could this information be stored somewhere else?

For example:

- coding standards,
- naming conventions,
- architectural rules,
- documentation style,
- review checklists.

These usually belong in:

```
instructions.md
```

or

```
Skill.md
```

rather than inside every individual prompt.

If multiple prompts need the same information, the information probably belongs in a reusable artifact.

---

# Design for Humans

As your AI system grows, remember something important.

Most of the files won't be read by the language model first.

They'll be read by you.

Or by your colleagues.

Or by your future self.

Organise them like source code.

Use:

- meaningful names,
- small files,
- comments,
- version control,
- documentation.

The easier your AI project is for humans to understand, the easier it usually is for AI as well.

---

# An Example Architecture

By now, you have enough knowledge to understand an AI system like this.

```
Repository

├── instructions.md
│
├── skills
│     ├── ReviewPullRequest.md
│     ├── ExplainArchitecture.md
│     └── GenerateReleaseNotes.md
│
├── agents
│     └── SprintAssistant.md
│
├── docs
│
├── scripts
│     ├── GetSprintStatistics.ps1
│     └── ExportWorkItems.ps1
│
└── knowledge
      ├── Architecture.md
      └── CodingGuidelines.md
```

Notice how familiar this looks.

It's simply another software project.

The only difference is that some files are written for humans *and* AI.

---

# Engineering Note

Throughout this handbook, you've repeatedly encountered familiar software engineering principles:

- separation of responsibilities,
- composition over duplication,
- abstraction,
- modularity,
- reuse,
- configuration over hardcoding.

None of these ideas were invented for AI.

Modern AI systems simply benefit from applying them consistently.

In other words:

**Good AI engineering is usually just good software engineering.**

---

# Looking Ahead

So far, we've focused on building systems that work well today.

But AI technology evolves incredibly quickly.

New models appear every few months.

Frameworks change.

Protocols mature.

How can you build AI systems that remain maintainable as the ecosystem changes?

The next chapter explores architectural patterns that help future-proof your AI projects and reduce unnecessary coupling between models, frameworks and tools.

---

# Search Vocabulary

### Workflow

**Definition**

A sequence of coordinated steps that transform a user's request into a completed result.

**Example**

Retrieving documentation, analysing code, generating a summary and creating a work item.

---

### Separation of Responsibilities

**Definition**

An architectural principle in which each component focuses on one clearly defined task.

**Compare to**

Equivalent to the Single Responsibility Principle in traditional software engineering.

**Example**

Allowing a Skill to review code while deterministic code gathers repository statistics.

---

### Reusable Artifact

**Definition**

A file or component designed to be shared across multiple AI workflows.

**Example**

A project-wide `instructions.md` file or a reusable Skill for architecture reviews.

---

### Composition

**Definition**

Building complex behaviour by combining smaller specialised components.

**Example**

An Agent coordinating several Skills instead of implementing all logic itself.

---

# 🎉 Level Up!

You've reached an important milestone in your journey from AI user to AI engineer.

You've learned to:

- organise AI projects like software projects,
- assign clear responsibilities to each building block,
- create reusable artifacts,
- avoid prompt sprawl,
- and build AI systems that remain understandable as they grow.

Perhaps the biggest insight is this:

**The best AI architecture often looks surprisingly similar to the best software architecture.**

The technologies may be new.

The engineering principles are not.

### Next Level

So far, we've concentrated on designing a single AI assistant.

In the next chapter, we'll take a broader look at the evolving AI ecosystem.

You'll learn how to design your AI projects so that changing models, frameworks or runtimes doesn't force you to rebuild everything from scratch.

By the end, you'll begin thinking about AI systems the same way experienced software architects think about software platforms.