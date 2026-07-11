# Chapter 14 – Teaching Your AI

In the previous chapter, you discovered one of the biggest limitations of every foundation model.

It already understands software development remarkably well.

What it doesn't understand is **your** software development.

It doesn't know:

- your architecture,
- your coding conventions,
- your repository structure,
- your preferred review style,
- or your company's terminology.

Fortunately, solving this problem does **not** require training a new model.

Instead, you'll build something much simpler—and much more practical.

A knowledge layer around the model.

---

# The Problem

Imagine a new developer joins your team.

Before assigning their first task, you probably don't sit down and explain every rule from memory.

Instead, you point them to resources such as:

- the README,
- the architecture documentation,
- coding guidelines,
- contribution guidelines,
- onboarding documentation,
- design decisions.

After reading those documents, they'll immediately ask better questions and produce better work.

Your AI assistant is no different.

---

# Reuse Before You Create

A common beginner assumption is:

> "I need to create lots of AI-specific files."

In reality, most projects already contain valuable documentation.

Examples include:

- `README.md`
- `CONTRIBUTING.md`
- `ARCHITECTURE.md`
- `docs/`
- ADRs (Architecture Decision Records)
- API documentation
- coding standards
- naming conventions

These documents already describe how your project works.

The first step is not writing new documentation.

The first step is making good use of the documentation you already have.

---

# Different Types of Knowledge

Not every document serves the same purpose.

It helps to think of project knowledge as different layers.

```text
Project Knowledge

├── General documentation
│   ├── README.md
│   ├── Architecture
│   ├── ADRs
│   └── Wiki
│
├── Development Guidelines
│   ├── Coding conventions
│   ├── Review checklist
│   ├── Naming rules
│   └── Testing strategy
│
└── AI-specific Instructions
    ├── instructions.md
    ├── prompt templates
    └── reusable Skills
```

Notice something interesting.

Only the bottom layer exists specifically because of AI.

Everything else should ideally already exist.

---

# Start With Stable Knowledge

When deciding what information to provide to an AI, ask yourself one simple question.

> **"Will this still be true next month?"**

If the answer is yes, it's a good candidate for reusable project knowledge.

Examples include:

- architectural principles,
- coding standards,
- naming conventions,
- repository layout,
- logging strategy,
- error handling conventions.

These change relatively rarely.

By contrast, things like:

- today's sprint,
- a temporary bug,
- an ongoing refactoring,

usually belong in the current conversation rather than permanent documentation.

---

# Introducing `instructions.md`

Sooner or later you'll notice that, regardless of the task, you always want the AI to behave in a certain way.

For example:

- explain reasoning before suggesting changes,
- prefer simple solutions,
- avoid unnecessary dependencies,
- produce compilable code,
- follow your team's naming conventions.

Rather than repeating these expectations in every conversation, many AI tools support a reusable instruction file.

A common name for such a file is:

```text
instructions.md
```

Think of it as a standing agreement between you and the AI.

Instead of telling the AI how to behave every time, you write those expectations once and reuse them.

---

# What Belongs in `instructions.md`?

Good instruction files focus on **behaviour**, not project documentation.

For example:

- preferred communication style,
- review priorities,
- coding preferences,
- output formatting,
- assumptions the AI should make,
- things the AI should avoid.

For example:

```text
- Explain significant changes before generating code.

- Prefer readability over clever solutions.

- Do not introduce new dependencies unless requested.

- When uncertain, ask clarifying questions.

- Highlight assumptions explicitly.

- Suggest unit tests for non-trivial changes.
```

Notice what is *not* included.

There is no repository structure.

No business logic.

No architecture diagrams.

Those belong elsewhere.

---

# Keep Instructions Stable

Beginners often create enormous instruction files.

Some exceed hundreds of lines.

This usually makes maintenance harder rather than easier.

A useful rule of thumb is:

> If the instruction changes every week, it probably doesn't belong in `instructions.md`.

Instructions should describe stable behaviour.

Project documentation should describe the project.

Conversations should contain temporary task-specific information.

Keeping those responsibilities separate makes your AI setup easier to understand and maintain.

---

# A Software Engineering Analogy

Think about configuration in a .NET application.

You probably wouldn't put everything into `appsettings.json`.

Instead, you separate concerns.

For example:

- configuration,
- source code,
- documentation,
- secrets,
- build scripts.

The same principle applies here.

Different kinds of knowledge belong in different places.

Trying to solve everything with one giant instruction file quickly becomes unmanageable.

---

# Common Beginner Mistake

Many people try to turn `instructions.md` into a complete knowledge base.

It becomes a mixture of:

- architecture,
- coding conventions,
- temporary notes,
- business rules,
- prompts,
- meeting minutes,
- personal reminders.

Eventually nobody knows which information is still correct.

Instead, think of `instructions.md` as a configuration file.

Its job is to describe **how the AI should work**, not **everything the AI should know**.

---

# Engineering Note

One of the strengths of good software architecture is separating responsibilities.

Apply the same idea to AI.

Keep:

- documentation,
- coding standards,
- architectural decisions,
- AI behaviour,
- task-specific prompts,

in separate places.

This makes each part easier to maintain and easier to reuse.

As your AI workflows become more sophisticated, this separation will become increasingly valuable.

---

# Looking Ahead

Your AI now has reusable behavioural instructions.

But there is still a significant limitation.

Even if the AI knows *how* it should behave, it still cannot automatically inspect your project.

It can't read source files.

It can't open configuration files.

It can't compare two classes.

It only sees what you manually provide.

The next chapter introduces the first capability that truly transforms your assistant:

**Giving the AI controlled access to your project's files.**

---

# Search Vocabulary

### Instructions

**Definition**

Reusable guidance that tells an AI how it should behave across many conversations or tasks.

**Compare to**

Similar to a configuration file that defines default behaviour.

**Example**

An `instructions.md` file can tell the AI to prefer readable code, explain assumptions and avoid unnecessary dependencies.

---

### Project Documentation

**Definition**

Documents that describe a software project, its architecture and its development practices.

**Example**

`README.md`, architecture diagrams and coding guidelines.

---

### Separation of Concerns

**Definition**

A software engineering principle in which different responsibilities are kept in separate components to simplify maintenance and reduce complexity.

**Compare to**

Just as application settings, source code and documentation belong in different files, AI behaviour, project knowledge and task-specific prompts should also remain separate.

---

# 🎉 Level Up!

You've taken the first step from *using* AI to *teaching* AI.

You can now distinguish between:

- reusable behavioural instructions,
- project documentation,
- and task-specific prompts.

More importantly, you've learned that improving an AI assistant often means improving its surrounding knowledge—not replacing the model itself.

### Next Level

In the next chapter, you'll give your AI assistant controlled access to your project's files.

This marks a major milestone: instead of relying only on what you paste into the conversation, the AI will begin working directly with the source code and documentation that already exist in your project.