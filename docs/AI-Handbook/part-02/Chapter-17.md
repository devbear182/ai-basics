# Chapter 17 – From Repeated Prompts to Reusable Skills

In the previous chapter, you integrated AI directly into your development environment.

The experience probably felt much more natural than constantly switching between your editor and a browser.

As you continue using AI during your daily work, however, you'll notice another pattern.

You begin asking the same kinds of questions over and over again.

Perhaps not with exactly the same wording, but with the same intention.

This is where many developers unknowingly reach the next level of AI engineering.

---

# The Problem

Imagine your typical morning.

A pull request arrives.

You ask:

> Review this code according to our coding standards.

A little later, another pull request arrives.

You ask almost the same thing.

Then another.

And another.

Later in the afternoon you generate unit tests.

Tomorrow you document a service.

The day after that you investigate an exception.

Although the files change, the workflow remains almost identical.

At some point you realize:

> "I'm no longer repeating code—I'm repeating prompts."

As software developers, we already know how to solve repetitive work.

We don't copy and paste code forever.

We create reusable components.

The same idea applies to AI.

---

# What Is a Skill?

A **Skill** is a reusable capability that teaches an AI how to perform a particular kind of task consistently.

Instead of writing the same instructions repeatedly, you package them into something that can be reused whenever needed.

Think of it as moving from this:

```
Developer

↓

Write long prompt

↓

AI performs task
```

to this:

```
Developer

↓

Run Skill

↓

AI already knows how to perform the task
```

The conversation becomes shorter.

The results become more consistent.

---

# A Software Engineering Analogy

Suppose you need to validate an e-mail address.

You could copy the validation logic into every application.

Or you could write a reusable function.

```csharp
ValidateEmail(address);
```

Every project can now reuse the same implementation.

A Skill follows exactly the same philosophy.

Instead of repeatedly writing:

> Review this code as a senior developer. Focus on readability, SOLID principles, naming, performance, testability and security. Explain every finding and prioritise them.

you simply execute:

```
Review Pull Request
```

The detailed instructions already exist.

---

# Skills Build on Everything You've Learned

A Skill isn't magic.

It combines concepts you've already encountered throughout this handbook.

```
Skill

├── Instructions
├── Context
├── Project Knowledge
├── Tools
└── Prompt
```

Notice that nothing here is new.

A Skill simply packages existing building blocks into something reusable.

---

# A Simple Example

Imagine your team performs pull request reviews in a consistent way.

Every review should:

- summarise the overall change,
- identify possible bugs,
- check naming,
- verify coding conventions,
- suggest tests,
- avoid unnecessary micro-optimisations.

Instead of describing these expectations every time, you create a reusable Skill.

Now every review follows the same process.

The result is not only faster.

It is also more predictable.

---

# What Makes a Good Skill?

Good Skills are surprisingly focused.

They solve exactly one type of problem.

For example:

- Review Pull Request
- Explain Legacy Code
- Generate Unit Tests
- Write XML Documentation
- Analyse Stack Trace
- Create Release Notes

Notice that each Skill has a very clear purpose.

This follows the same philosophy as the Single Responsibility Principle.

One Skill.

One responsibility.

---

# Skills Should Be Opinionated

Earlier in the handbook we discussed coding conventions.

Suppose your team prefers:

- constructor injection,
- explicit variable names,
- XML documentation,
- xUnit,
- FluentAssertions,
- file-scoped namespaces.

A generic AI cannot assume these preferences.

A Skill can.

This makes the output much more consistent across different developers.

---

# Where Are Skills Stored?

The exact implementation depends on the AI application.

Some tools store Skills as:

- Markdown files
- YAML files
- JSON definitions

Others provide graphical editors.

Still others allow Skills to be managed centrally for an entire team.

The important point is not the file format.

The important point is the separation of responsibilities.

The Skill contains reusable behaviour.

The current conversation contains the current task.

---

# Start Small

One of the most common beginner mistakes is attempting to create a huge Skill that does everything.

For example:

```
Software Development Skill
```

which tries to:

- review code,
- write documentation,
- generate tests,
- investigate bugs,
- explain architecture,
- optimise performance,
- create commits.

This quickly becomes difficult to understand and maintain.

Instead, create several smaller Skills.

For example:

```
Skills

├── Review Pull Request
├── Generate Unit Tests
├── Explain Code
├── Write Documentation
└── Investigate Bug
```

Smaller Skills are easier to improve, easier to debug and easier to reuse.

---

# Version Your Skills

Skills are software.

Treat them like software.

Store them together with your project if they are project-specific.

Review changes.

Improve them gradually.

Ask your colleagues for feedback.

A good Skill often evolves over time in exactly the same way as a reusable library.

---

# Common Beginner Mistake

Many developers expect the Skill to contain every possible detail.

As a result, they create extremely long instructions.

This usually has the opposite effect.

Remember that the foundation model already understands software development remarkably well.

The Skill should primarily describe:

- your expectations,
- your workflow,
- your conventions.

Don't explain C# to a model that already knows C#.

Explain how **your team** wants C# to be written.

---

# Engineering Note

Think carefully about whether a behaviour belongs in:

- project documentation,
- `instructions.md`,
- or a Skill.

A useful guideline is:

- **Project documentation** explains the project.
- **Instructions** explain how the AI should generally behave.
- **Skills** explain how to perform a specific recurring task.

Keeping those responsibilities separate makes your AI system much easier to maintain as it grows.

---

# Looking Ahead

Your AI can now perform recurring tasks consistently.

But something is still missing.

You still decide:

- which Skill to run,
- when to run it,
- what information to provide.

Wouldn't it be useful if the AI could coordinate several Skills automatically?

Instead of simply executing instructions, it could plan a workflow.

That is exactly what an **Agent** does.

---

# Search Vocabulary

### Skill

**Definition**

A reusable AI capability that packages instructions, context and, optionally, tools for solving a specific type of recurring task.

**Compare to**

Similar to a reusable function or library in software development.

**Example**

A "Review Pull Request" Skill can consistently review code according to your team's conventions.

---

### Reusable Workflow

**Definition**

A sequence of steps that is performed repeatedly and therefore benefits from being standardised and reused.

**Example**

Generating documentation for every public API using the same structure and wording.

---

### Single Responsibility Principle (SRP)

**Definition**

A design principle stating that a component should have one clear responsibility and one primary reason to change.

**Compare to**

Just as a class should not perform unrelated tasks, a Skill should focus on solving one specific problem.

**Example**

A Skill that only generates unit tests is easier to maintain than one that attempts to review code, write documentation and optimise performance simultaneously.

---

# 🎉 Level Up!

You've moved beyond writing individual prompts.

You now understand how to package recurring workflows into reusable Skills.

You can now:

- recognise repetitive AI workflows,
- decide when a Skill is appropriate,
- design focused, reusable Skills,
- and separate project knowledge, behavioural instructions and task-specific workflows.

Perhaps more importantly, you've started applying familiar software engineering principles to AI systems.

Instead of copying prompts, you're beginning to build reusable AI components.

### Next Level

So far, every decision has still come from you.

You decide which Skill to execute and when.

In the next chapter, you'll learn how an **Agent** can coordinate multiple Skills, choose appropriate tools and carry out a larger objective with much less guidance from the user.

This is where AI begins to move from *assisting* with work to *orchestrating* work.